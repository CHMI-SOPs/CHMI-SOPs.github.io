---
title: sourmash workflow
tags: [bioinformatics, microbiome]
keywords:
summary: "QC and analysis of microbial WGS and metagenomic data using Sourmash"
sidebar: mydoc_sidebar
permalink: mydoc_sourmash.html
folder: mydoc
---

## before starting
The following protocol outlines the use of [Sourmash](https://sourmash.readthedocs.io/en/latest/) for interpreting microbial whole genome sequence (WGS) or metagenomic data.  Sourmash computes a fingerprint or 'sketch' from your WGS data using minHash, and enables comparison of sketches from isolates (to understand strain relatedness, for example).  Similarly, a sketch can be compared against a large databases of sketches, stored as a Sequence Bloom Tree (SBT) for rapid searching, from RefSeq or Genbank in order to help assign identity to a sample.  SBT databases of microbial genomes from all of Genbank and RefSeq are available directly on our server for convenience.

If you want to learn more about how Sourmash works, you could start with C. Titus Brown's blog posts on the topic [here](http://ivory.idyll.org/blog/2016-sourmash-sbt.html) and [here](http://ivory.idyll.org/blog/2016-sourmash-sbt-more.html).  Also take a look at Adam Phillippy's [original Mash paper](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-016-0997-x)


## Step 1: Connect to a CHMI linux cluster

{% include important.html content="if you do not have an account on our cluster and would like to get one, please contact Dan Beiting" %}

```
ssh username@130.91.255.137
```

## Step 2: Check data quality

Begin by using [fastqc](https://www.bioinformatics.babraham.ac.uk/projects/download.html) to check the quality of each of your fastq files.  Throughout this protocol, 'path/to/your/data' indicats the path to your folder on our linux server which contains raw sequence data from your WGS or metagenomics experiment.

```
cd path/to/your/data
fastqc *.gz -t 24 #uses all 24 threads available on our machine
```

## Step 3: Summarize QC results

[MultiQC](https://multiqc.info/) is a fantastic piece of software for aggregating and summarizing the outputs from many different kinds of bioinformatics programs in one convenient and interactive html file.  In this case, we'll use it to summarize the output from fastqc.

```
multiqc path/to/your/data
```

## Step 4: Prepare a 'sketch' of your raw data

Here, we'll use sourmash's ```compute``` function to prepare a sketch of each fastq file in our directory.  the ```--scaled``` option to apply a 1000:1 compression ratio, which retains the ability to detect regions of similarity in the 10kb range.

```
sourmash compute --scaled 1000 *.gz
```

## Step 5: Compare sketches to each other

The Sourmash ```compare``` command computes the jaccard index between two or more sketches generated above.

```
sourmash compare *.sig -k 31 -o cmp
```

## Step 6: Visualize sample relatedness

```
sourmash plot --pdf --labels cmp
```

## Step 7: Search against RefSeq

This Sequence Bloom Tree (SBT) database contains approximately 60,000 microbial genomes (including viral and fungal) from NBCI's RefSeq, including:

- 53865 bacterial genomes
- 5463 viral genomes
- 475 archael genomes
- 177 fungal genomes
- 72 protist genomes

```
sourmash search *.sig /data/reference_db/refseq-d2-k31.sbt.json -n 20 
#shows top 20 hits
```

## Step 8: Search against Genbank

This Sequence Bloom Tree (SBT) database contains approximately 100,000 microbial genomes (including viral and fungal) from NBCI's GenBank.

```
sourmash search *.sig /data/reference_db/genbank-d2-k31.sbt.json -n 20
#shows top 20 hits
```

## Optional: 'What genomes are in my sample?'

Often times there are questions about whether a preparation used for WGS was contaminated with another organism.  Perhaps Sanger sequencing of 16S rDNA gave murky results, or restreaking an isolate showed more than one distinct colony morphology.  Alternatively, you may *know* that your sample has multiple genomes present (e.g. metagenomics).  In either case, the Sourmash ```gather``` function allows you to ask exactly which organisms might be present in a sample based only on the sequence data.  Like the search function above, gather needs a reference database to search against.

```
sourmash gather -k 31 *.sig /data/reference_db/refseq-d2-k31.sbt.json #using refseq
sourmash gather -k 31 *.sig /data/reference_db/genbank-d2-k31.sbt.json #using genbank
```

On the other hand, if you suspect contamination of a particular kind (e.g. host, plasmid, or common bacterium used in lab), you can run [fastq_screen](https://www.bioinformatics.babraham.ac.uk/projects/fastq_screen/_build/html/index.html) to check a subsample of reads from your raw fastq file against a set of reference genomes.  Although this has nothing to do with Sourmash or minHask sketches *per se*, it can be a useful way to confirm findings from Sourmash, or to check for organisms not well represented in the SBT reference databases provided above.

fastq_screen uses bowtie2 for aligning reads to the references, so we've provided a set of reference genomes on our cluster to which you can easily compare.

We've taken care of configurating fastq_screen so that it knows where to find bowtie2 and where to look for the reference genomes.  This information is pretty clearly outlined in the fastq_screen configuration file found at /usr/local/bin/fastq_screen_v0.12.0/fastq_screen.conf

{% include important.html content="The reference genomes listed below have already been added to the configuration file.  If you don't want a particular reference, you can comment it out.  Please **do not** delete the configuration file or remove any of the lines in the file...just comment out.  If you want to include a reference that is now listed below, please contact us for help." %}

- Human
- Mouse (*Mus musculus*)
- Dog (*Canis familiaris*)
- Cow (*Bos taurus*)
- Horse (*Equus caballus*)
- Pig (*Sus scrofa*)
- Chicken (*Gallus gallus*)
- Fruitfly (*Drosophila melanogaster*)
- Yeast (*Saccharomyces cerevisiae*)
- *E. coli* (strain K12)
- Staph (*Staphyloccous aureus* strain NCTC 8325)
- Lambda phage (Enterobacteriophage lambda)
- PhiX 
- [Contaminants](www.bioinformatics.babraham.ac.uk/projects/fastqc)
- [plasmids/vectors](http://www.ncbi.nlm.nih.gov/VecScreen/UniVec.html)

{% include note.html content="Just as you summarized the fastqc results in Step 3 using multiQC, the same can be done with the results from fastq_screen.  Rerunning multiqc and you will get a report that incorporates both fastqc and fastq_screen outputs, as long as these outputs are in the same directory." %}


## Optional: filtering reads

Depending on the results you get with Sourmash gather or fastq_screen above, you may want to filter reads based on alignment to a particular reference genome of interest.  This is particularly useful for removing host reads contaminating a metagenomic sample, for example.  To do this, you can use the ```--tag``` and ```--filter``` options for fastq_screen.

First, tag each read in each fastq with the genome to which it aligns (from the available references described above)

```
fastq_screen --tag sampleX.fastq.gz
```

Next, filter based on tags that were assigned above

```
fastq_screen --filter 1000 sampleX.fastq.gz
``` 


{% include links.html %}




