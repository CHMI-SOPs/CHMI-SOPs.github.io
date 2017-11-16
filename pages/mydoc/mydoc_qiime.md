---
title: analysis of 16S rRNA gene sequencing data
tags: [library construction]
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
bsub -Is 
```

Activate QIIME

```
source /opt/software/qiime/1.8.0/activate.sh
```

### option 2: use CHMI's linux server

```
ssh username@130.91.255.137
```

## Join forward and reverse reads
```
join_paired_ends.py -f myForwardReads.fastq -r myReverseReads.fastq -o JoinedReads
```

## Validated mapping files

Just keep trying until it works. Visualize the output html file. Yellow is ok, red is an error that needs to be fixed.

```
validate_mapping_file.py -m MappingFile.txt
```

```
perl Testscript.pl JoinedReads/fastqjoin.join.fastq > JoinedReads.fastq
```


perl script to remove the plus sign from the barcodes

```
split_libraries_fastq.py -i JoinedReads.fastq -o sl_out -q 29 -b Barcodes/barcodes.fastq -m MappingFile.txt --barcode_type 16
```

Assign sequences to a sample number in your mapping file

## Quality filtering using [Mothur](https://www.mothur.org/)

start mothur

```
mothur
```



```
#at the mother prompt, run:
summary.seqs(fasta=sl_out/seqs.fna)
trim.seqs(fasta=sl_out/seqs.fna, maxhomop=10, minlength=248, maxlength=256)
summary.seqs(fasta=sl_out/seqs.trim.fasta)
quit()
```


## Generate OTU table

At this point, you'll have to decide if you want to pick OTU's *de novo*, or use a closed reference method, or an open reference method.

```
pick_de_novo_otus.py -i sl_out/seqs.trim.fasta -o DeNovoOTUs 
```


## Filter singletons

## Remove chimeras

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

## Groups samples into treatment groups
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

{% include links.html %}