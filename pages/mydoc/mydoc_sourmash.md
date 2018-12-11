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
The following protocol outlines the use of [Sourmash](https://sourmash.readthedocs.io/en/latest/) for interpreting microbial whole genome sequence (WGS) or metagenomic data.  Sourmash computes a fingerprint or 'sketch' from your WGS data using minHash, and enables comparison of sketches from isolates (to understand strain relatedness, for example).  Similarly, a sketch can be compared against a large databases of sketches, stored as a Sequence Bloom Tree (SBT) for rapid searching, from RefSeq or Genbank in order to help assign identity to a sample.  We have made these SBT databases available directly on our server for convenience.

If you want to learn more about how Sourmash works, you could start with C. Titus Brown's blog posts on the topic [here](http://ivory.idyll.org/blog/2016-sourmash-sbt.html) and [here](http://ivory.idyll.org/blog/2016-sourmash-sbt-more.html).  Also take a look at Adam Phillippy's [original Mash paper](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-016-0997-x)


## Step 1: Connect to a CHMI linux cluster

{% include important.html content="if you do not have an account on our cluster and would like to get one, please contact Dan Beiting" %}

```
ssh username@130.91.255.137
```

## Step 2: Check data quality

Begin by using fastqc to check the quality of each of your fastq files.  Throughout this protocol, 'path/to/your/data' indicats the path to your folder on our linux server which contains raw sequence data from your WGS experiment.

```
cd path/to/your/data
fastqc *.gz -t 24
```

## Step 3: Summarize QC results

Use multiQC to summarize the output from running fastqc above for each sample

```
multiqc path/to/your/data
```
## Step 4: Prepare a 'sketch' of your raw data

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

This SBT database contains approximately 60,000 microbial genomes (including viral and fungal) from NBCI's RefSeq, including:

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

This SBT database contains approximately 100,000 microbial genomes (including viral and fungal) from NBCI's GenBank.

```
sourmash search *.sig /data/reference_db/genbank-d2-k31.sbt.json -n 20
#shows top 20 hits
```

## Optional: 'What else is in my sample?'

Often times there are questions about whether a preparation used for WGS was contaminated with another organism.  Perhaps Sanger sequencing of 16S rDNA gave murky results, or restreaking an isolate showed more than one distinct colony morphology.  Alternatively, you may *know* that your sample has multiple genomes present (e.g. metagenomics).  In either case, the Sourmash ```gather``` function allows you to ask exactly which organisms might be present in a sample based only on the sequence data.  Like the search function above, gather need a reference database to work from.

```
sourmash gather -k 31 *.sig /data/reference_db/refseq-d2-k31.sbt.json #using refseq
sourmash gather -k 31 *.sig /data/reference_db/genbank-d2-k31.sbt.json #using genbank

```

If you suspect contamination of a particular kind (e.g. host, or common bacterium used in lab), you can run [fastq_screen](https://www.bioinformatics.babraham.ac.uk/projects/fastq_screen/) to check a subsample of reads from your raw fastq file against a set of reference genomes.  Although this has nothing to do with Sourmash or minHask sketches *per se*, it can be a useful way to confirm findings from Sourmash, or to check for organisms not well represented in the SBT reference databases provided above.

fastq_screen uses bowtie2 for aligning reads to the references, so we've provided a set of reference genomes on our cluster to which you can easily compare.


## Optional: removing contaminating reads

Depending on the results you get with Sourmash gather and/or Fastq_screen above, you may want to remove reads mapping to a particular reference genome.  This is particularly useful for removing host reads contaminating a metagenomic sample, for example.  To do this, use 



{% include links.html %}




