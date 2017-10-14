---
title: Kallisto
tags: [getting_started, troubleshooting]
keywords:
summary: "Kallisto is our first choice for aligning reads because it combines speed, accuracy, and ability to leverage bootstraps for modeling technical variance"
sidebar: mydoc_sidebar
permalink: mydoc_kallisto.html
folder: mydoc
---

## Intro
[Kallisto](https://pachterlab.github.io/kallisto/about) is a relatively new tool from Lior Pachter's lab at UC Berkeley and is described in [this 2016 Nature Biotechnology paper](http://CHMI-sops.github.io/papers/Kallisto.pdf).  

## Installing Kallisto on a Mac OS

If you're running a Mac OS, then begin by downloading and installing [Homebrew](https://brew.sh/) with this single line of code: 

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Now, installing Kallisto is simple:
```
brew tap homebrew/science
brew install kallisto
```

Test whether Kallisto is properly installed by typing ```kallisto```, and you should see this output

```
kallisto 0.43.1

Usage: kallisto <CMD> [arguments] ..

Where <CMD> can be one of:

    index         Builds a kallisto index 
    quant         Runs the quantification algorithm 
    pseudo        Runs the pseudoalignment step 
    h5dump        Converts HDF5-formatted results to plaintext
    version       Prints version information
    cite          Prints citation information

Running kallisto <CMD> without arguments prints usage information for <CMD>
```

## Installing Kallisto on a Windows OS

* Download Kallisto for Windows and unzip.  You'll need to have the Kallisto.exe in the same folder with the .fastq files you wish to align.  Alternatively, you could add the .exe to your path, but I'm not sure how to do this on a Windows machine.
* To run Kallisto on a PC, open the Command Prompt (All programs -> Accessories -> Command Prompt), 
* use the ```cd``` command to change your working directory to the location of the .fastq files and Kallisto.exe.
* Drag and drop the Kallisto.exe file onto your open Command Prompt window
* type the word 'kallisto' to make sure the program is running

## Build an index from reference transcriptome .fasta file

Get reference transcriptome files from [here](http://useast.ensembl.org/info/data/ftp/index.html)
Choose your the cDNA file for your organism, then download the file that ends in “cDNA.all.fa.gz”

Build the index
```
kallisto index -i myNewIndex InputFasta.fasta
```

## align single-end reads

Run the following command for pseudoalignment of single-end reads to index. 
```
kallisto quant -i myHumanIndex -o Sample1.mapped -b 100 —-single -l 275 -s 20 read1.fastq.gz
```
{% include note.html content="bootstrapping (-b command in the line above) adds significant time to the mapping, but is essential for accurate quantification. With a typical reference index for the mouse or human transcriptome, I find it takes about 15sec per bootstrap. So expect this to add ~30 min to the mapping time for each sample." %}

{% include warning.html content="avoid putting hyphens in the name of the kallisto output, as this could cause problems later" %}

## align paired-end reads
```
kallisto quant -i myMouseIndex -o Sample1.mapped -b 100 read1.fastq.gz read2.fastq.gz
```

## install Sleuth
Open RStudio and install the [rhdf5 package](http://bioconductor.org/packages/release/bioc/html/rhdf5.html) from the BioC website

install the [devtools package](https://cran.r-project.org/web/packages/devtools/README.html) (if you don’t already have it)

install the [Sleuth package](https://github.com/pachterlab/sleuth) directly from Lior Pachter's github page using:
```
devtools::install_github("pachterlab/sleuth")
```

## Using Sleuth

* open Rstudio and load the Sleuth package ```library(sleuth)```
* read in a study design file with column called 'path' which lists the path to each Kallisto output folder
* set-up a study design using the model.matrix function in R, with an intercept: ```myDesign <- model.matrix(~treatment)```


{% include links.html %}
