---
title: Kallisto
tags: [bioinformatics, transcriptomics]
keywords:
summary: "Kallisto is our first choice for aligning reads because it combines speed, accuracy, and the ability to leverage bootstraps for modeling technical variance"
sidebar: mydoc_sidebar
permalink: mydoc_kallisto.html
folder: mydoc
---

## Intro
[Kallisto](https://pachterlab.github.io/kallisto/about) is a relatively new tool from Lior Pachter's lab at UC Berkeley and is described in [this 2016 Nature Biotechnology paper](http://CHMI-sops.github.io/papers/Kallisto.pdf). Kallisto and other tools like it (e.g. [Salmon](https://combine-lab.github.io/salmon/)) have revolutionized the analysis of RNAseq data by using extremely lightweight 'pseudomapping' that effectively allows analyses to be carried out on a standard laptop.  If you are reluctant to try pseudomapping out of concern that it won't produce accurate quantifications of transcripts, [rest assured it will](https://www.nature.com/articles/s41467-017-00050-4). 

## Installing Kallisto on a Mac OS

If you're running a Mac OS, then begin by downloading and installing [Homebrew](https://brew.sh/) with this single line of code: 

```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Now, installing Kallisto is simple:

```shell
brew tap homebrew/core
brew install kallisto
```

Test whether Kallisto is properly installed by typing ```kallisto```, and you should see this output

```shell
kallisto 0.45.0

Usage: kallisto <CMD> [arguments] ..

Where <CMD> can be one of:

    index         Builds a kallisto index 
    quant         Runs the quantification algorithm 
    bus           Generate BUS files for single cell data 
    pseudo        Runs the pseudoalignment step 
    merge         Merges several batch runs 
    h5dump        Converts HDF5-formatted results to plaintext
    inspect       Inspects and gives information about an index
    version       Prints version information
    cite          Prints citation information

Running kallisto <CMD> without arguments prints usage information for <CMD>
```

## Installing Kallisto on a Windows OS

1. Obtain administrative access for your computer
2. You will need to be able to unzip files.  If you don't have software that can do this, you can download [WinRAR](https://www.win-rar.com/start.html?&L=0) and install it in Program Files.
3. Download the latest windows release of [Kallisto](https://pachterlab.github.io/kallisto/download) (v0.46, for Spring 2020)
4. Right click the downloaded zip file and choose "extract here" or "extract all". A new folder will appear called "kallisto". Move it to your "Program Files" directory.
5. Kallisto is now installed on your computer but cannot be accessed from any location in the command prompt (Windows equivalent of Terminal) until you add it to your computer’s PATH system variable. 
6. Add the kallisto directory to your PATH to allow for access from any directory
* Open the Control Panel and navigate to System and security -> System -> Advanced System Setting -> Environmental Variables
* Under System Variables (**not** User Variables), click PATH -> Edit -> New
Note: You'll see a list of folders, as this example for my system shows: C:\Program Files\Windows Resource Kits\Tools\; etc
* Add the path to your kallisto folder to System Variables by copying the path from File Explorer (e.g. C:/Program Files\kallisto) and pasting it into the prompt.
8. Relaunch command prompt (or your RStudio session if you are working in the RStudio Terminal). Check for proper installation by typing ‘kallisto’ (without quotes) into Command Prompt (or RStudio Terminal).
9. Although not required for running kallisto, you should install [Cygwin](https://www.cygwin.com/) to give your PC some linux functionality (like running shell scripts).

## Build an index from reference transcriptome .fasta file

{% include note.html content="If you are working on the PennVet CHMI linux cluster, we have prebuilt kallisto indicies from mouse, human and several other species located in /data/reference_db/kallisto" %}

Get reference transcriptome files from [here](http://useast.ensembl.org/info/data/ftp/index.html)
Search for your organism, select cDNA, then download the file that ends in “cDNA.all.fa.gz”

Build the index

```shell
kallisto index -i inputFastaName.index inputFastaName.fasta
```

{% include note.html content="It's a good idea to name you index exactly the same as your input fasta file, just replacing .fasta or .fa, with .index.  This naming convention makes it clear to others (and your future self) exactly which reference transcriptome was used for mapping." %}

## align single-end reads

Run the following command for pseudoalignment of single-end reads to index. 

```shell
kallisto quant -i inputFastaName.index -o sample1_kallisto -b 60 —-single -l 275 -s 30 sample1_read1.fastq.gz
```
Once read mapping is complete, you will see a short report printed to your screen that indicates the number of reads kallisto saw in the fastq file, and the number of these that mapped to the reference.  Often times it is useful to automatically store this information in a log file so that it can be parsed by other programs, such as the incredibly useful [multiQC](http://multiqc.info/).  To do this, simply append the code below at the end of your alignment bit above. The outcome will be the same, but instead of displaying on the screen it will be piped to a log file.

```shell
&> sample1_kallisto.log
```

{% include warning.html content="avoid putting hyphens in the name of the kallisto output, as this could cause problems later" %}

{% include important.html content="bootstrapping (-b command in the line above) adds significant time to the mapping, but is essential for accurate quantification. With a typical reference index for the mouse or human transcriptome, I find it takes about 15sec per bootstrap. So expect this to add ~30 min to the mapping time for each sample." %}

{% include important.html content="If you want a .bam file output with your alignment, use ```--pseudobam```." %}

{% include important.html content="If you have multiple cores on your computer, you can speed up the aligment with the ```-t``` argument followed by the number of threads you have on your machine.  If you're on a mac, you can find out the number of virtual cores (i.e. threads) using the ```sysctl hw.ncpu``` command directly in the terminal" %}


## align paired-end reads

```shell
kallisto quant -i inputFastaName.index -o sample1_kallisto -b 100 sample1_read1.fastq.gz sample1_read2.fastq.gz
```

## stranded alignments and bigwigs
In some cases, you may want to carry out a stranded alignment with the end goal of viewing read 'pileups' on a genome browser track.  This can also be done using Kallisto, but requires a few other programs and steps to get from the Kallisto alignment to bigwig. 

{% include warning.html content="If you've been using your laptop thus far, now would be a good time to consider finding some more compute resources. Working with .bam files may be too much for your laptop to handle." %}

Stranded alignment using pseudobam. SAM creation is also possible at this step.

```shell
kallisto quant -i [yourindex] -o [outputname] --fr-stranded -b 60 --pseudobam [input1] [input2] | samtools view -Sb - > [kallisto.fr.bam]
kallisto quant -i [yourindex] -o [outputname] --rf-stranded -b 60 --pseudobam [input1] [input2] | samtools view -Sb - > [kallisto.rf.bam]
```

Sort and index using [samtools](http://samtools.sourceforge.net/)

```shell
samtools sort -@ 24 [kallisto.fr.bam] [kallisto.fr.sorted]
samtools sort -@ 24 [kallisto.rf.bam] [kallisto.rf.sorted]
samtools index [kallisto.fr.sorted.bam]
samtools index [kallisto.fr.sorted.bam]
```

BAM to BigWig conversion using [deeptools](https://deeptools.readthedocs.io/en/latest/)

```shell
bamCoverage –b [kallisto.fr.sorted.bam] –o [kallisto.fr.sorted.bw] -p max
bamCoverage –b [kallisto.rf.sorted.bam] –o [kallisto.rf.sorted.bw] -p max
```

## install Sleuth
Open RStudio and install the [rhdf5 package](http://bioconductor.org/packages/release/bioc/html/rhdf5.html) from the BioC website

install the [devtools package](https://cran.r-project.org/web/packages/devtools/README.html) (if you don’t already have it)

install the [Sleuth package](https://github.com/pachterlab/sleuth) directly from Lior Pachter's github page using:

```shell
devtools::install_github("pachterlab/sleuth")
```

## Using Sleuth

* open Rstudio and load the Sleuth package ```library(sleuth)```
* read in a study design file with column called 'path' which lists the path to each Kallisto output folder
* set-up a study design using the model.matrix function in R, with an intercept: ```myDesign <- model.matrix(~treatment)```


{% include links.html %}
