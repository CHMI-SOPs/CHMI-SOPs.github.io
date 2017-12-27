---
title: Kallisto
tags: [bioinformatics, transcriptomics]
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

1. Obtain administrative access for your computer
2. Go to https://pachterlab.github.io/kallisto/download
3. Download the latest Windows release (v0.43.1 for Fall 2017)
4. Extract to Program Files or Applications.  Kallisto is now installed on your computer but it cannot be accessed from any location in the command prompt/terminal until you add it to your computer’s path system variable 
5. Add the kallisto directory to your PATH to allow for access from any directory
* Start the System Control Panel applet (Start -> Settings -> Control Panel -> System)
* Select the Advanced tab.
* Click the Environment Variables button.
* Under System Variables, select Path, then click Edit.
Note: You'll see a list of folders, as this example for my system shows: C:\Program Files\Windows Resource Kits\Tools\; etc
* Add the name of the path to your kallisto directory (e.g. including semicolon ;C:\Program Files\kallisto_windows-v0.43.1
6. Relaunch command prompt and check for proper installation by typing kallisto (Windows equivalent of Terminal)
7. although not required for running kallisto, you should install [Cygwin](https://www.cygwin.com/) to give your PC some linux functionality (like running shell scripts)

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
kallisto quant -i myHumanIndex -o Sample1.mapped -b 60 —-single -l 275 -s 20 read1.fastq.gz
```
{% include warning.html content="avoid putting hyphens in the name of the kallisto output, as this could cause problems later" %}

{% include important.html content="bootstrapping (-b command in the line above) adds significant time to the mapping, but is essential for accurate quantification. With a typical reference index for the mouse or human transcriptome, I find it takes about 15sec per bootstrap. So expect this to add ~30 min to the mapping time for each sample." %}

{% include important.html content="If you want a .bam file output with your alignment, use ```--pseudobam```." %}

{% include important.html content="If you have multiple cores on your computer, you can speed up the aligment with the ```-t``` argument followed by the number of threads you have on your machine.  If you're on a mac, you can find out the number of virtual cores (i.e. threads) using the ```sysctl hw.ncpu``` command directly in the terminal" %}


## align paired-end reads
```
kallisto quant -i myMouseIndex -o Sample1.mapped -b 100 read1.fastq.gz read2.fastq.gz
```

## stranded alignments and bigwigs
In some cases, you may want to carry out a stranded alignment with the end goal of viewing read 'pile-ups' on a genome browser track.  This can also be done using Kallisto, but requires a few other programs and steps to get from the Kallisto alignment to bigwig. 

{% include warning.html content="If you've been using your laptop thus far, now would be a good time to consider finding some more compute resources. Working with .bam files may be too much for your laptop to handle." %}

Stranded alignment using pseudobam. SAM creation is also possible at this step.
```
kallisto quant -i [yourindex] -o [outputname] --fr-stranded -b 60 --pseudobam [input1] [input2] | samtools view -Sb - > [kallisto.fr.bam]
kallisto quant -i [yourindex] -o [outputname] --rf-stranded -b 60 --pseudobam [input1] [input2] | samtools view -Sb - > [kallisto.rf.bam]
```

Sort and index using [samtools](http://samtools.sourceforge.net/)
```
samtools sort -@ 24 [kallisto.fr.bam] [kallisto.fr.sorted]
samtools sort -@ 24 [kallisto.rf.bam] [kallisto.rf.sorted]
samtools index [kallisto.fr.sorted.bam]
samtools index [kallisto.fr.sorted.bam]
```

BAM to BigWig conversion using [deeptools](https://deeptools.readthedocs.io/en/latest/)
```
bamCoverage –b [kallisto.fr.sorted.bam] –o [kallisto.fr.sorted.bw] -p max
bamCoverage –b [kallisto.rf.sorted.bam] –o [kallisto.rf.sorted.bw] -p max
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
