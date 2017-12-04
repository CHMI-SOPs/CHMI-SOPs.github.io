---
title: analysis of 16S rRNA gene sequencing data
tags: [bioinformatics, microbiome]
keywords:
summary: "Preparation of V4 region, 16S dual-indexed libraries for sequencing on an Illumina platform"
sidebar: mydoc_sidebar
permalink: mydoc_qiime.html
folder: mydoc
---

## Connect to a compute cluster:

### option 1: use PMACS

use ssh to connect to PMACS.  You'll be propted for your password.

```
ssh -X username@consign.pmacs.upenn.edu
```

Enter the interactive bash shell

```
bsub -Is bash
```

or for larger datasets:

```
bsub -Is -q denovo -n 5 bash 
```

Activate QIIME

```
source /opt/software/qiime/1.8.0/activate.sh
```

### option 2: use CHMI's linux server

```
ssh username@130.91.255.137
```

## check your mapping file

In order to use QIIME, you must have your mapping file correctly formatted.  An example of this format is shown in the table below.  '#SampleID', 'BarcodeSequence', 'LinkerPrimerSequence' and 'Description' must all be present in the file and named exactly as we've written (case sensitive).  Specific details about your experiment (treatment, sample type, cage, etc) are added between the 'LinkerPrimerSequence' and 'Description' columns.  Here we've simply listed these as covariate1, covariate2, etc.  You can have as many of these columns as necessary to describe your experiment.  Note the sampleID column must be unique.


| #SampleID | BarcodeSequence | LinkerPrimerSequence | covariate1 | covariate2 | covariate3 | Description |
|-------|--------|--------|--------|--------|--------|--------|
| 001 | ATCGCTACTTAGCGCT | GTGCCAGCMGCCGCGGTAA | cageA | control | wild-type | WT naive mouse #1 |
| 002 | TGCGCCACTAACCGCT | GTGCCAGCMGCCGCGGTAA | cageB | treated | wild-type  | WT infected mouse #1 |
| 003 | GGCAATCACTAACCGC | GTGCCAGCMGCCGCGGTAA | cageA | treated | wild-type  | WT infected mouse #2 |

Once you think you have your mapping file ready to go, run the ```validate_mapping_file.py``` line below to confirm that the format is correct.  Visualize the output html file. Yellow is ok, red is an error that needs to be fixed.

```
validate_mapping_file.py -m MappingFile.txt
```



## Join forward and reverse reads

We begin by taking our forward and reverse reads and joining these reads.  The resulting output file (called 'joinedReads' in the example below) will be a single fastq file containing all of your data.

```
join_paired_ends.py -f myForwardReads.fastq -r myReverseReads.fastq -o JoinedReads
```

## dealing with barcodes
Our UPenn sequencing core delivers fastq files that have the barcode listed in the header.  After joining paired ends, both barcodes will be listed in the header, with a '+' separating the two.  We'll use a perl script to remove the '+' in order to prevent issues later.  

```
perl Testscript.pl JoinedReads/fastqjoin.join.fastq > JoinedReads.fastq
```

With the '+' removed, we then extract the barcodes and put these into new file called 'barcodes'

```
extract_barcodes.py -f JoinedReads.fastq -l 16 -o Barcodes -c barcode_in_label
```


Right now, each of your sequences is associated with a specific barcode, but we haven't yet matched these barcodes with our original sample identifiers.  This is where your mapping file comes in.  In the process of doing this mapping, we'll also discard any sequences with [Phred](https://en.wikipedia.org/wiki/Phred_quality_score) scores < 30.

```
split_libraries_fastq.py -i JoinedReads.fastq -o sl_out -q 29 -b Barcodes/barcodes.fastq -m MappingFile.txt --barcode_type 16
```


## Quality filtering

We use [Mothur]((https://www.mothur.org/)) to trim our sequences, but you can also use other programs such as the FASTX toolkit.  We'll begin by firing up Mothur:

```
mothur
```


First, let's use Mothur's handy ```summary.seqs``` function to sumarize information about the sequence file, including binning sequences by length,  looking at the number of sequences in each bin, and finding homopolymers

```
summary.seqs(fasta=sl_out/seqs.fna)
```

Now, we'll use Mothur to trim the sequences and remove homopolymer runs.  You can adjust these values based on the region you are looking at. For 16S V4 we expect sequences of 250 bp, so we trim based on that expectiation.  If you're using another 16S region, then you may want to adjust the ```minlength``` and ```maxlength``` parameters accordingly. Once complete, we run ```summary.seqs``` again to visualize the impact of trimming on our data.  Finally, we quit mothur.

```
trim.seqs(fasta=sl_out/seqs.fna, maxhomop=10, minlength=248, maxlength=256)
summary.seqs(fasta=sl_out/seqs.trim.fasta)
quit()
```

## Optional: Concatenate fasta data from multiple runs
We typically put data from each run into a single large file that contains all data from all past runs.  This is something we do internally at CHMI, so if you're running though this on your own, feel free to skip this step.

```
cat MiSeq1234567_seqs.fna MiSeq8_seqs.fna > MiSeq12345678_seqs.fna
```


## Generate a fasta file that has only your sequences of interest 

16S microbiome sequencing runs often include 100's of samples.  Since you many not want to analyze all the samples from a single run at the same time, you can use the QIIME ```filter_fasta.py``` function to select only samples of interest.  You'll need to provide a simple text file with the samples IDs you'd like to keep arranged in a single column (in the example below, we have called this 'sample_id_fp').

```
filter_fasta.py -i MiSeq12345678_seqs.fna --sample_id_fp MappingFile.txt -o Project.fna
```

## Generate OTU table

At this point, you'll have to decide if you want to pick OTU's *de novo*, use a closed reference method, or use an open reference method.  You can read more about these methods, and their respective advantages/disadvantages [here](). Don't be deceived by this short line of code.  There's a lot of important stuff that's happening here, so you may want to read up a bit on this.

### Option 1: 

```
pick_de_novo_otus.py -i Project.fna -o DeNovoOTUs 
```

### Option 2: (longer way, but easier to extract the chimeras)

pick_otus.py -i Project.fna --enable_rev_strand_match --otu_picking_method cdhit -s 0.97 --prefix_prefilter_length 200 -o otus

pick_rep_set.py -f Project.fna -i otus/Project_otus.txt --rep_set_picking_method most_abundant -o rep_set.fna

align_seqs.py -i rep_set.fna -t /home/Reference/core_set_aligned.fasta.imputed.txt -o aligned_seqs

assign_taxonomy.py -i rep_set.fna -o assigned_taxonomy --confidence 0.8


## Remove PCR chimeras

[chimeras](http://genome.cshlp.org/cgi/pmidlookup?view=long&pmid=21212162) are PCR amplicons formed from two separate parent DNA molecules during the PCR reaction.  These need to be removed, otherwise they would be interpreted as novel organisms and would therefore erroneously inflate community diveristy. The output file is a txt file that has the list of sequence numbers.

```
identify_chimeric_seqs.py -i aligned_seqs/rep_set_aligned.fasta -m ChimeraSlayer -o chimeric_seqs.txt -a /home/misic/Reference/core_set_aligned.fasta.imputed.txt
```

## Filtering and subsetting

Produce a .biom file from your data.  You can read about the .biom file format [here](http://biom-format.org/)

```
make_otu_table.py -i otus/Project_otus.txt -t assigned_taxonomy/rep_set_tax_assignments.txt -o otu_table.biom -e chimeric_seqs.txt
```

Remove OTUs from the table that only have a single representative sequence, a.k.a. 'singletons', as well as OTUs with fewer than 10 sequences

```
filter_otus_from_otu_table.py -i otu_table.biom -n 10 -o otu_table2.biom
```

If you want to see the most (or least) abundant OTUs in your table

```
filter_otus_from_otu_table.py -i otu_table_2.biom --min_count_fraction 0.01 -o otu_table_onlygreaterthan1percent.biom
```

We use file with the otu names of the mitochondria, cyanobacteria, and unassigned taxa and remove those from the OTU table.  Depending on your project, you may or may not want to remove these. For work involving stool, I remove cyanobacteria. However, if you are performing an enviornmental study, you may choose to keep these in.

```
$ filter_otus_from_otu_table.py -i otu_table2.biom -e Mito_Cyano_and_unassigned.txt -o otu_table3.biom
```

Now subset your data to select only those columns of the taxa table the correspond to the samples you're interested in analyzing

```
filter_samples_from_otu_table.py -i otu_table_3.biom --sample_id_fp MappingFile_SoilOnly.txt -o otu_table_4SoilOnly.biom
```

Summarize your .biom file to produce a simple text file with taxa

```
biom summarize-table -i otu_table3.biom -o Table3Summary.txt
```

## rarify to desired depth

```
single_rarefaction.py -i otu_table_4soilonly.biom -d 2900 -o otu_table_5_soil_2900.biom
```

## create rel abund for taxa

```
summarize_taxa_through_plots.py -m /home/misic/MAD/Files/MappingFile_MAD_v3.txt -c Treatment -o TaxaSumTreatment -i otu_table_3.biom 
```


## Get counts for taxa

```
summarize_taxa.py -i otu_table_3.biom -a -o TaxaSumAbs -m /home/misic/MAD/Files/MappingFile_MAD_v3.txt 
# Flag: -L 2 phylum ; -L 3 class ; -L 4 order ; -L 5 family -L 6 genus ; -L 7 species
example: summarize_taxa_through_plots.py -m /home/misic/MAD/Files/MappingFile_MAD_v3.txt -c Treatment -o TaxaSumTreatment -i otu_table_3.biom  -L 5
```

## Group samples by treatment group

```
filter_samples_from_otu_table.py -i otu_table_3.biom --sample_id_fp MappingFile_MAD_SoilOnly.txt -o otu_table_4soilonly.biom
```

## Generate beta diversity plots

```
beta_diversity_through_plots.py -i otu_table_5_soil_2900.biom -m MappingFile_MAD_SoilOnly.txt -o BetaDiv_Soil -t rep_set.tre 
```

## filter taxa based on rel abund

```
$ filter_otus_from_otu_table.py -i otu_table_3.biom --min_count_fraction 0.01 -o otu_table_onlygreaterthan1percent.biom
```

## relative abundance and plots

```
summarize_taxa_through_plots.py -m MappingFile.txt -c Treatment -o TaxaSumTreatment -i otu_table_3.biom 
```


Optional flags include for this function include: 
* ```-L 2``` for phylum 
* ```-L 3``` for class
* ```-L 4``` for order
* ```-L 5``` for family
* ```-L 6``` for genus
* ```-L 7``` for species


Example: summarize_taxa_through_plots.py -m MappingFile.txt -c Treatment -o TaxaSumTreatment -i otu_table_3.biom -L 5.  Only gives data at family level. Groups samples into treatment groups


Produce a table with absolute sequence counts.

```
summarize_taxa.py -i otu_table_3.biom -a -o TaxaSumAbs -m MappingFile.txt 
```


Identify the core microbiome in your samples at different taxanomic levels (for example, which OTUs are found in 90% of the samples).

```
compute_core_microbiome.py -i otu_table.biom -o otu_table_core_fast --mapping_fp MappingFile.txt --valid_states "Treatment:Fast"
```


## Alpha diversity

Obtain the alpha diversity values for the listed at 4 phylogenetic levels

There are many options for alpha diversity metrics, but the ones we use most commonly include: 

* observed_species
* shannon
* simpson 
* simpson_e
* PD_whole_tree
* chao1 
* fisher_alpha

```
alpha_diversity.py -m shannon,chao1,PD_whole_tree,observed_species -i otu_table.biom -o AlphaDiv.txt -t rep_set_aligned.tre 
```


## rarefaction

Generate 'collectors curves' (A.K.A. rarefaction plots) that can be visualized as HTML

```
alpha_rarefaction.py -O 10 -a -i otu_table3.biom -o alpha_rare_curves -m MappingFile.txt -t rep_set_aligned.tre -p parameters.txt
```

rarify to desired depth, in this example, 2900 sequences

```
single_rarefaction.py -i otu_table.biom -d 2900 -o otu_table_2900.biom
```

## Optional: QIIME 'core diversity analysis'

If so desired, you can use the function below to carry out several QIIME diversity analyses together.  This is a basic workflow that begins with a BIOM table, mapping file, and optional phylogenetic tree. 

```
core_diversity_analyses.py -i otu_table.biom -m MappingFile.txt -o CoreAnalyses -t rep_set_aligned.tre -c Timepoint,Exper_name,Breed_Strain -e 5000
```

The included scripts are those run by the workflow scripts alpha_rarefaction.py, beta_diversity_through_plots.py, summarize_taxa_through_plots.py, plus the (non-workflow) scripts make_distance_boxplots.py, compare_alpha_diversity.py, and otu_category_significance.py. To update parameters to the workflow scripts, you should pass the same parameters file that you would pass if calling the workflow script directly.

Additionally, a table summary is generated by running the 'biom summarize-table' command (part of the biom-format package). To update parameters to this command, your parameters file should use 'biom-summarize-table' (without quotes) as the script name. See http://qiime.org/documentation/qiime_parameters_files.html for more details.


## Beta diversity

This is to create the distance matrix which is then used for the next script, compare categories

```
beta_diversity_through_plots.py -i otu_table.biom -m MappingFile.txt -o BetaDiv -t rep_set.tre -p parameters.txt
```

```
beta_diversity.py -i otu_table.biom -m weighted_unifrac,unweighted_unifrac,bray_curtis,binary_jaccard -t rep_set_aligned.tre -o BetaDivMatricesV10
```

With Beta diversity you also have many choices for metrics to you.  We most often look at:
* weighted_unifrac
* unweighted_unifrac
* bray_curtis
* binary_jaccard

This script uses anosim (Analysis of similarities) to analyze if groups vary by timepoint. Output is an R value (from -1 to 1) and a p value. The more a category influences microbiota, the larger the R values will be, and the smaller the p value will be.

```
compare_categories.py -i otu_table.biom -m MappingFile.txt -i BetaDivMatrices/weighted_unifrac_otu_table.txt -c Timepoint --method anosim -o WU_Timepoint
```

Note: you must explicitly state which statisical test you would like to use to compare categories.  You options include:
Also Note: you input biom. file could be rarefied (or not), or filtered to only be certain groups

* adonis
* anosim
* best
* morans_i
* mrpp
* permanova
* permdisp
* dbrda 

You may also find it useful to make boxplots showing distances.  You can do this as follows:

```
make_distance_boxplots.py -d BetaDivMatrices/unweighted_unifrac_otu_table.txt -o DistanceHist -m MappingFile.txt -f Treatment
```

## Machine learning approaches

```
supervised_learning.py -i otu_table.biom -m MappingFile.txt -c Treatment -o MachineLearningResults -v -e cv10
```


{% include links.html %}



