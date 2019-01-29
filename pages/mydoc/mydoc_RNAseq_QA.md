---
title: Project management and quality assurance for RNAseq projects
tags: [bioinformatics, transcriptomics]
keywords:
summary: "Managing your RNAseq project and checking the quality of raw data are essential first steps in the analysis of any RNAseq experiment.  The protocol below outlines our best practices to keep  projects and data transparent, reproducible and robust."
sidebar: mydoc_sidebar
permalink: mydoc_RNAseq_QA.html
folder: mydoc
---

## Step 1: project set-up

Quality assurance (QA) can mean many things – to us QA means not only that the raw data files are examined for any issues that could compromise downstream analyses, but also that the data is organized in a way that others can understand what was done for a given project.  This greatly improves transparency and reproducibility.  To ensure that the different file types and analyses for your RNAseq project remain clear and organized, we recommend an approach we call [MinimAl Directory for Rnaseq AnalysiS (MADRAS)](http://github.com/dpbisme/MADRAS).  MADRAS is just a directory structure that provides a simple framework for organizing your experiment.  You can download a skeletal version of this directory **[here](http://CHMI-sops.github.io/images/MADRAS.zip)** 

```
|-- DATA
    |-- raw
        |-- sample1_mergedLanes.fastq.gz
        |-- sample2_mergedLanes.fastq.gz
        |-- ...
    |-- processed
        |-- preprocessing.sh
        |-- sample1_mergedLanes_trim.fastq.gz
        |-- sample2_mergedLanes_trim.fastq.gz
        |-- ...
|-- ANALYSIS
    |-- code
        |-- myProject.Rproj
        |-- step1.R
        |-- step2.R
        |-- ...
        |-- projectSummary.rmd
        |-- projectDashboard.rmd
    |-- readmapping
        |-- readmapping.sh
        |-- reference.fasta
        |-- reference.index
|-- QA
    |-- library_prep
        |-- RNAquality_tapestation.pdf
        |-- Library_tapestation.pdf
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

```

## Step 2: Connect to a CHMI linux cluster

Once you have your directory structure set-up, you're ready to begin using some software tools for investigating the quality of the reads in your fastq files.  These software run best on a machine with a fair amount of RAM and disk storage.  We use our [linux machine](https://chmi-sops.github.io/mydoc_linux.html).

{% include important.html content="if you do not have an account on our cluster and would like to get one, please contact Dan Beiting" %}

```
ssh username@130.91.255.137
```

## Step 3: Check data quality

Begin by using [fastqc](https://www.bioinformatics.babraham.ac.uk/projects/download.html) to check the quality of each of your fastq files.  Throughout this protocol, we'll assume you use a directory structure like the one outlined above.  The file paths below reference this directory structure.

```
# navigate to the folder with your raw fastq files
cd data/raw
# run fastqc on all files, putting the outputs into the QA/fastqc folder
fastqc *.gz -t 24 -o ../QA/fastqc 
```

## Step 4: Summarize QA results

[MultiQC](https://multiqc.info/) is a fantastic piece of software for aggregating and summarizing the outputs from many different kinds of bioinformatics programs in one convenient and interactive html file.  In this case, we'll use it to summarize the output from fastqc.

```
# use the -d command to tell multiqc to look in all folders (data, analysis and qa) to find log files
cd MADRAS/
multiqc -d .
```

You should now see a multiqc_report.html file in your project directory.  Move this to your data/qa folder.  You can also copy it from our server to your local computer using an FTP client (e.g. FileZilla), then double click and explore!


## Optional: 'Are my .fastq files contaminated?'

Often times there are questions about whether there may be reads, other than those from the intended sample source, present in a data file.  If you suspect contamination of a particular kind (e.g. other host, plasmid, rRNA, or some common bacterium used in lab), you can run [fastq_screen](https://www.bioinformatics.babraham.ac.uk/projects/fastq_screen/_build/html/index.html) to check a subsample of reads from your raw fastq file against a set of reference genomes.  

fastq_screen uses bowtie2 for aligning reads to the references, so we've provided a set of reference genomes on our cluster to which you can easily compare.

We've taken care of configurating fastq_screen so that it knows where to find bowtie2 and where to look for the reference genomes.  This information is pretty clearly outlined in the fastq_screen configuration file found at /usr/local/bin/fastq_screen_v0.12.0/fastq_screen.conf

```
cd data/raw
fastq_screen --threads 24 --outdir QA/fastq_screen *gz  
```

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

{% include note.html content="Just as you summarized the fastqc results in Step 3 using multiQC, the same can be done with the results from fastq_screen.  Rerunning multiqc will generate a new report that incorporates both fastqc and fastq_screen outputs, as long as these outputs are in the same parent directory." %}


{% include links.html %}




