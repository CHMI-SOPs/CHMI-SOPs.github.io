---
title: Preparing microbiome data for deposit to microbiomeDB.org 
tags: [microbiomeDB, bioinformatics]
keywords: 
summary: "Instructions on how to prepare your raw sequence data and metadata mapping file for submission to microbiomeDB.org"
sidebar: mydoc_sidebar
permalink: mydoc_microbiomeDB_deposit.html
folder: mydoc
---

## Overview

Our lab developed and maintains [MicrobiomeDB](http://www.microbiomedb.org), a web-based platform for sharing, integrating and carrying out sophisticated queries of 16S microbiome experiments.  We can load your published data into our database.  To facilitate this process, it helps our data loading team if you can prepare your raw data and mapping file.  Currently, we can accept legacy data from 454 'pyrosequencing', as well as newer 16S rRNA gene sequencing data from the Illumina miSeq platform.  The protocol below outlines steps for preparing miSeq data.  

## Before starting

* You'll need access to your raw 16S rRNA gene sequence data, in the form of one forward.fastq.gz and one reverse.fastq.gz
* Sign-up for a Google account (alternatively, Microsoft Excel is fine)
* Get access to a compute cluster (or local workstation) with [QIIME](http://qiime.org/) installed
* Sign up for an account on microbiomeDB.org (it's free and always be!)


## prepare your fastq files

Activate qiime1 and unzip your fastq files

```
source activate qiime1
gunzip *fastq.gz
```

Depending on the exact format of your fastq files, you may need to remove the '+' in the fastq files 

```
perl -ane 'if (m/^\@/){s/\+//;} print;' forward.fastq > forward.fastq
```

## extract barcodes

```
extract_barcodes.py \
	-f forward.fastq \
	-r reverse.fastq \ #only used for paired-end reads
	-l 16 \ #this option specifies the barcode length. see documentation for guidance for your particular barcodes.
	-o barcodes.fastq \
	-c barcode_in_label
```

## demultiplex libraries

If using paired-end reads, perform the following steps for **both** forward and reverse reads.

{% include important.html content="The output files will be named the same (sampleID.fastq) for both forward and reverse, so be sure to make a separate folder for forward and reverse files" %}

```
split_libraries_fastq.py \ 
	-i forward.fastq \
	-o forward/split_libraries \
	-m metadata_file.txt \
	-b barcodes.fastq \
	--barcode_type 16 \
	--store_demultiplexed_fastq #Without this flag the output is only a demultiplexed fasta file
```

Rename your files so the runID/name and the forward or reverse info is indicated in the name (in this example, the run name was 'miseq12' and these were forward reads) 

```
mv seqs.fastq miseq12_forward_seqs.fastq
mv seqs.fna miseq12_forward.fna
mv histograms.txt miseq12_forward_histograms.txt
mv split_library_log.txt miseq12_forward_split_library_log.txt
```

```
split_sequence_file_on_sample_ids.py \
	-i seqs.fastq \
	-o forward/split_libraries/forward_fastqs \
	--file_type fastq
```

## prepare metadata

MicrobiomeDB allows users to analyze and visualize microbiome data based on any user-provided metadata.  This metadata needs to be provided as a [google sheet](https://www.google.com/sheets/about/).  Each column of your spreadsheet should represent a metadata variable (*e.g.*, Age, Sex, Treatment, *etc*), and each row should be identified with unique sample IDs that matches those used in naming the fastq files above.  If you need help naming your column headers using appropriate terminology, you may find it useful to view our [terminology list](http://microbiomedb.org/mbio/showQuestion.do?questionFullName=SampleQuestions.MicrobiomeSampleByMetadata) on microbiomeDB.

{% include links.html %}
