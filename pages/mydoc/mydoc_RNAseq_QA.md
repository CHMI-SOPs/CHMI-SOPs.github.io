---
title: Quality assurance of raw data from RNAseq experiments
tags: [bioinformatics, transcriptomics]
keywords:
summary: "Checking the quality of your .fastq files is an essential first step in the analysis of any RNAseq experiment.  The protocol below outlines the steps and tools that we use for quality assurance."
sidebar: mydoc_sidebar
permalink: mydoc_RNAseq_QA.html
folder: mydoc
---

## Setting up your project directory

Quality assurance can mean many things, to us QA means not only that the raw data files are examined for any issues that could compromise downstream analyses, but also that the data is organized in a way that others can understand what was done for a given project.  This greatly improves transparency and reproducibility.  To ensure that the different file types and analyses for your RNAseq project remain clear and organized, we recommend an approach we call [MinimAl Directory for Rnaseq AnalysiS (MADRAS)](http://github.com/dpbisme/MADRAS).  This is just a simple directory structure as follows:

|-- **data**
    |-- raw
    |-- processed
        |-- preprocessing.sh
        |-- sample1.fastq.gz
        |-- sample2.fastq.gz
        |-- ...
|-- **analysis**
    |-- code
        |-- myProject.Rproj
        |-- step1.R
        |-- step2.R
        |-- ...
    |-- readmapping.sh
|-- **qa**
    |-- fastqc
        |-- sample1.fastqc.html
        |-- sample1.fastqc.zip
        |-- sample2.fastqc.html
        |-- sample2.fastqc.zip
        |-- ...
    |-- fastq_screen
    |-- multiqc_report.html
|-- studyDesign.txt
|-- readme.txt

## Step 1: Connect to a CHMI linux cluster

{% include important.html content="if you do not have an account on our cluster and would like to get one, please contact Dan Beiting" %}

```
ssh username@130.91.255.137
```

## Step 2: Check data quality

Begin by using [fastqc](https://www.bioinformatics.babraham.ac.uk/projects/download.html) to check the quality of each of your fastq files.  Throughout this protocol, 'path/to/your/data' indicates the path to your folder on our linux server which contains raw sequence data from your WGS or metagenomics experiment.

```
# navigate to the folder with your preprocessed fastq files (assumes the directory structure shown above)
cd data/processed
# run fastqc on all files, putting the outputs into the qa/fastqc folder
fastqc *.gz -t 24 -o ../qa/fastqc 
```

## Step 3: Summarize QA results

[MultiQC](https://multiqc.info/) is a fantastic piece of software for aggregating and summarizing the outputs from many different kinds of bioinformatics programs in one convenient and interactive html file.  In this case, we'll use it to summarize the output from fastqc.

```
# use the -d command to tell fastqc to look in all folders (data, analysis and qa) to find log files
multiqc -d .
```

If you navigate to the qa folder, you should now see a multiqc.html file in your project directory.  Move it from our server to your local computer using an FTP client (e.g. FileZilla), double click, and explore!


## Optional: 'Are my .fastq files contaminated?'

Often times there are questions about whether there may be reads, other than those from the intended sample source, present in a data file.  If you suspect contamination of a particular kind (e.g. other host, plasmid, or common bacterium used in lab), you can run [fastq_screen](https://www.bioinformatics.babraham.ac.uk/projects/fastq_screen/_build/html/index.html) to check a subsample of reads from your raw fastq file against a set of reference genomes.  

fastq_screen uses bowtie2 for aligning reads to the references, so we've provided a set of reference genomes on our cluster to which you can easily compare.

We've taken care of configurating fastq_screen so that it knows where to find bowtie2 and where to look for the reference genomes.  This information is pretty clearly outlined in the fastq_screen configuration file found at /usr/local/bin/fastq_screen_v0.12.0/fastq_screen.conf

{% include important.html content="The reference genomes listed below have already been added to the configuration file.  If you don't want a particular reference, and you are comfortable editing configuration files using the commnad line, feel free to comment out any of the references.  However, please **do not** delete the configuration file itself or *remove* any of the lines in the file!  If you want to use fastq_screen against a bowtie2 reference genome that is not listed below, please contact us for help." %}

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

{% include note.html content="Just as you summarized the fastqc results in Step 3 using multiQC, the same can be done with the results from fastq_screen.  Rerunning multiqc will generate a new report that incorporates both fastqc and fastq_screen outputs, as long as these outputs are in the same directory." %}


{% include links.html %}




