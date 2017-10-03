---
title: Kallisto
tags: [getting_started, troubleshooting]
keywords:
summary: "Kallisto is our first choice for aligning reads because of its speed, accuracy, and ability to leverage bootstraps for understanding technical variance"
sidebar: mydoc_sidebar
permalink: mydoc_kallisto.html
folder: mydoc
---

## Intro
a bit about Kallisto and why we like it for alignments

## Installing Kallisto on a Mac OS

If you're running a Mac OS, then being by downloading and installing [Homebrew](https://brew.sh/) with this single line of code: 

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

This makes installing Kallisto simple:
```
brew tap homebrew/science
brew install kallisto
```

Test whether Kallisto is properly installed by typing ```kallisto```

## Installing Kallisto on a Windows OS

## Build an index from reference transcriptome .fasta file

Get reference transcriptome files from [here](http://useast.ensembl.org/info/data/ftp/index.html)
Choose organism and cDNA, then download the file that ends in “cDNA.all.fa.gz”

Build the index
```
kallisto index -i myNewIndex InputFasta.fasta
```

## align single-end reads

Run the following command for pseudoalignment of single-end reads to index. 
```
kallisto quant -i myHumanIndex -o Sample1.mapped -b 100 —-single -l 275 -s 20 read1.fastq.gz
```
{% include note.html content="bootstrapping (-b command in the line below) adds significant time to the mapping, but is essential for accurate quantification. With a typical reference index for the mouse or human transcriptome, I find it takes about 15sec per bootstrap. So expect this to add ~30 min to the mapping time for each sample.  Also, avoid putting hyphens in the name of the kallisto output, as this could cause problems later" %}


## align paired-end reads
```
kallisto quant -i myMouseIndex -o Sample1.mapped -b 100 read1.fastq.gz read2.fastq.gz
```

## install Sleuth
Open RStudio and install the [rhdf5 package]() from the BioC website

install [devtools]() package (if you don’t already have it)

install sleuth from Lior Pachter github page using:
```
devtools::install_github("pachterlab/sleuth")
```

{% include links.html %}
