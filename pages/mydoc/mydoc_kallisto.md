---
title: RNAseq FAQs
tags: [getting_started, troubleshooting]
keywords:
summary: "Kallisto is our first choice for aligning reads because of its speed, accuracy, and ability to leverage bootstraps for understanding technical variance"
sidebar: mydoc_sidebar
permalink: mydoc_kallisto.html
folder: mydoc
---

## Installing Kallisto on a Mac OS

If you're running a Mac OS, then being by downloading [Homebrew](https://brew.sh/). 

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Now installing Kallisto is simple
```
brew tap homebrew/science
brew install kallisto
```

Test whether it is properly installed by typing ```kallisto```

## Installing Kallisto on a Windows OS

## Build an index from reference transcriptome .fasta file

Get reference transcriptome files from [here](http://useast.ensembl.org/info/data/ftp/index.html)
Choose organism and cDNA, then download the file that ends in “cDNA.all.fa.gz”

Build the index
```
kallisto index -i myNewIndex InputFasta.fasta
```


{% include links.html %}
