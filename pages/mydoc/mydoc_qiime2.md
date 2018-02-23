---
title: analysis of marker gene sequencing data using QIIME
tags: [bioinformatics, microbiome]
keywords:
summary: "Using the Quantitative Insights Into Microbial Ecology (QIIME2) software pipeline for analysis of marker gene-based microbiome sequencing data"
sidebar: mydoc_sidebar
permalink: mydoc_qiime2.html
folder: mydoc
---

## Step 1: Connect to a CHMI linux cluster

{% include important.html content="if you do not have an account on our cluster and would like to get one, please contact Dan Beiting" %}

```
ssh username@130.91.255.137
```

## Step 2: prepare your metadata

Before you get started, there are a few basic QIIME commands that you will want to get familiar with

```
#take a look at all the plugins you have available to you through QIIME
qiime tools

#documentation for any QIIME function ca be accessed by appending --help at the end of any command



```

Metadata is information about your samples (e.g. date collected, patient age, sex, pH, etc).  This information should be contained within a single spreadsheet that has samples as rows and variables as columns.

In order to use QIIME, you **must** have your mapping spreadsheet correctly formatted.  Set this file up as a google sheet, using [this example]().  In order to check whether your file is correctly formatted, use the [Keemei plugin](keemei.qiime2.org) for google sheets.  Once Keemei says your spreadsheet is correctly formatted for QIIME2, you're ready to proceed. 

Create a .txt version of your metadata spreadsheet and save in your working directory on a computer with QIIME2 installed.  You can then inspect further if you want using:

```
qiime tools inspect-metadata [filename]
```


Create a visualiation of your metadata on the QIIME2 viewer (.qzv is a qiime zipped visualization)
```
qiime metadata tabulate --m-input-file sample-metadata.tsv --o-visualization tabulated-metadata.qzv
```

navigate to [QIIME2 viewer](https://view.qiime2.org/) in browser to view this visualization


## Step 3: prepare your raw data

There are a number of ways you may have your raw data structured, depending on sequencing platform (e.g., Illumina vs Ion Torrent) and sequencing approach (e.g., single-end vs paired-end), and any pre-processing steps that have been performed by sequenencing facilities (e.g., joined paired ends, barcodes in fastq header, etc).  Check out the [QIIME info page](https://docs.qiime2.org/2018.2/tutorials/importing/)

Move your fastq files and your barcode file (if data is not already demultiplexed) to your working directory

create an artifact of your data
```
qiime tools import \
  --type EMPSingleEndSequences \
  --input-path emp-single-end-sequences \
  --output-path emp-single-end-sequences.qza
```
 
Check this artifact to make sure that QIIME now recognizes your data (.qza is a qiime zipped artifact)

```
qiime tools peek emp-single-end-sequences.qza
```

{% include important.html content="the .qza and .qzv files can be unpacked using the unix command  ```unzip``` or the qiime commands ```qiime tools extract``` or ```qiime tools export```.  These unpacked files can then be used in other settings (R, perl, etc).  In other words, the QIIME concept of an 'artifact' does not permanently alter the structure of your data." %}

## Step 4: demultiplexing

{% include note.html content="If you data is already demultiplexed, you can skip this step. For paired data you would use qiime demux emp-paired in the code snipet below to produce a demux.qza file" %}

```
qiime demux emp-single \
  --i-seqs emp-single-end-sequences.qza \
  --m-barcodes-file sample-metadata.tsv \
  --m-barcodes-column BarcodeSequence \
  --o-per-sample-sequences demux.qza
```


{% include note.html content="If you ran qiime tools extract on the demux.qza, you would have all your demultiplexed per-sample fastq files, if you wanted these for other fun stuff" %}

Now produce a visualization of the demux'ing.  This will produce a file called *demux.qza*, which can be viewed on the [QIIME2 viewer](https://view.qiime2.org/) as you did earlier for your metadata.qzv file

```
qiime demux summarize \
  --i-data demux.qza \
  --o-visualization demux.qzv
```

## Step 5: denoising 

### DADA2
BLURB ABOUT OTU AND denoising.  One method for denoising is to use DADA2.  You can learn more about this method by checking out the Nature Methods paper, and the online methods section for more indepth (but still very readable) description of the statistical methods [here]()

{% include important.html content="DADA2 denoising will join paired reads for you.  Do not join your reads prior to running DADA2, since the program has a model for the basewise error of illumina reads, and joining reads would violate the expectations of that model.  If you're working with single-end data, you would use 'denoise-single' in the code below." %}

{% include important.html content="If you have multiple runs, it is recommended that you run DADA2 separately on data from each run individually, then combine data from the runs after denoising.  See the [QIIME2 fecal transplant tutorial](https://docs.qiime2.org/2018.2/tutorials/fmt/) for an example of how this works" %}

```
qiime dada2 denoise-paired \
  --i-demultiplexed-seqs demux.qza \
  --p-trim-left 0 \
  --p-trunc-len 120 \
  --o-representative-sequences rep-seqs-dada2.qza \
  --o-table table-dada2.qza
```

Once you're confortable with the individual steps of this workflow, you could use [this shell script](), to run the entire workflow 



{% include links.html %}



