---
title: Metagenomics in the cloud
tags: [bioinformatics, microbiome, tutorials, metagenomics]
keywords:
summary: "This 4 hour workshop takes users through setting up their own cloud computer, intalling a Snakemake-based pipeline called Sunbeam for analysis of shotgun metagenomic data, and analyzing/discussing data from Crohn's disease patients"
sidebar: mydoc_sidebar
permalink: mydoc_cloudMeta.html
folder: mydoc
---

## Workshop outline

| Start time | Description                  | Type                |
|------------|------------------------------|---------------------|
| **1pm**    | Welcome                      | talk - Kyle and Dan |
|            | Launch Instance              | activity - Dan      |
|            | intro to command line        | talk - Dan          |
|            | Install Sunbeam, get data    | activity - Kyle     |
| **2pm**    | Shotgun sequencing intro     | talk - Dan          |
|            | Initialize, configure, run   | activity - Kyle     |
|            | *Coffee break*               |                     |
| **3pm**    | Explore results, make report | activity - Kyle     |
|            | Download report              | activity - Dan      |
|            | Discuss results              | talk - Kyle and Dan |


## Before starting
In this workshop we'll use the Google Cloud to analyze raw metagenomic sequence data to identify the microbial composition of stool from heathly humans compared to Crohn's disease patients.  In addition to generating this microbial census, you'll also assemble sequences into contigs, which can then be used to infer functional potential.  To accomplish these tasks we'll use [Sunbeam](https://www.biorxiv.org/content/early/2018/05/18/326363), a snake-make based metagenomics pipeline developed by [Kyle Bittinger](https://microbiome.research.chop.edu/our-team/kyle-bittinger.html) and his group at the PennCHOP Microbiome Center.  

The code below is copied from the [Sunbeam documentation](http://sunbeam.readthedocs.io/en/latest/quickstart.html).  Please see this documentation for more detailed info about using Sunbeam for your own work. 

This tutorial provides a guide to walk you through this workshop, and provide a resource you can use to practice the material, as well as adapt for your own work.

To participate in this workshop, you'll only need a few things:
* a laptop computer
* an internet connection
* a google account (free)
* [a google cloud account](https://cloud.google.com) (free sign-up comes with a $300 credit!)

## Set-up cloud computer 

We'll begin the workshop with a demonstration of how to launch your first Google Cloud instance to build your cloud computer to have the following specs: 

* 8 cores
* 50Gb of RAM
* 100Gb solid state harddrive
* Running Linux Ubuntu 18.04 LTS operating system

Once you have finalized this instance, you have effectively rented a computer from Google, and we are all using exactly the same type of computer with the same operating system and compute resources.  In the case of the computer we set-up above, you will be charged 36 cents per hour, or about $260/month.  The more powerful the computer, the more you will be charged in rent, regardless of whether or not you actually use these resources.

{% include note.html content="This entire workshop should only take about $1 of your credit to complete." %}

{% include warning.html content="If you fail to delete your instance after the workshop, your credit card will be charged after ~1 month (when your $300 credit will have been spent)." %}

## Install Sunbeam

* Connect to your cloud computer using the 'ssh' button next to the instance.  

* Install some software using the Advanced Package Tool (apt), a free program that works with core libraries to handle the installation and removal of software on Debian, Ubuntu and other Linux distributions

```{bash}
# first, update all current packages
sudo apt-get update
# now install the R programming language 
sudo apt-get install r-base
```

* [Download Sunbeam](https://github.com/eclarke/sunbeam) from github using the code below

```{bash}
cd ~
git clone -b stable https://github.com/sunbeam-labs/sunbeam sunbeam-stable
ls
```
* Install Sunbeam

```{bash}
cd sunbeam-stable
bash install.sh
```
* notice that we got a few warnings at the end of the Sunbeam installation.  Although Conda is now installed on our cloud computer, it has not been added to our PATH. We can do this using the following code:

```{bash}
# first, take a look at what is in your PATH
echo $PATH
# now add the location of Conda to your PATH
echo "export PATH=$PATH:/home/dbeiting/miniconda3/bin" >> ~/.bashrc
```
{% include note.html content="the changes you made to your path will not take effect until you close and reoopen your SSH terminal.  You can do this now." %}

* After opening the new SSH terminal window, check your PATH again with `echo $PATH`.  Notice that it has been updated with the location of the conda environments.

* Since Sunbeam was installed as a Conda environment, we have to enter this environment to start using the software

```{bash}
source activate sunbeam
```
This is a command you'll want to remember for future sessions.  Each time you log into your cloud instance, you'll need to activate the pipeline with `source activate sunbeam`.  Upon activation, you should see that your command prompt begins with "(sunbeam)".  Anytime you want to exit out of sunbeam, simply type `source deactivate sunbeam` and hit return.

{% include note.html content="In addition to Sunbeam, there are an growing number of tools available that will install easily and quickly on cloud instances.  For example, you may want to check out [Chiron](https://github.com/IGS/Chiron), a suite of 'dockerized' tools for analysis of metagenomics data" %}


## Get data

* let's install some additional software in our environment. SRA tools will allow us to easily retrieve raw data from NCBI's [Sequence Read Archive](https://www.ncbi.nlm.nih.gov/sra) 

```{bash}
conda install -c bioconda sra-tools
```
* For this workshop, we'll use data from a [recent metagenomics study](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4633303/) in Crohn's disease.  This was a large study, but for the purpose of the workshop we'll only fetch data from 7 patients.  Note: contaminating human reads have already been removed from these files.  Let's download these data to our cloud computer using the `fasterq-dump` function from the SRA tools software.

```{bash}
cd ~
mkdir workshop-data
cd workshop-data
fasterq-dump SRR2145310
fasterq-dump SRR2145329
fasterq-dump SRR2145381
fasterq-dump SRR2145353
fasterq-dump SRR2145354
fasterq-dump SRR2145492
fasterq-dump SRR2145498
```

## Initialize project

```{bash}
cd ~
mkdir workshop-project
sunbeam init workshop-project --data_fp workshop-data
```

* Use your nano text editor to explore the samples file and configuration file.

## Download reference data

* We need two reference databases to run our analysis: a database of host DNA
sequence to remove, and a database of bacterial DNA to match against.

* We'll get the human genome data from UCSC.  Filtering against the entire human
genome takes too long, so we'll only filter against chromosome 1.

```{bash}
cd ~
mkdir human
cd human
wget http://hgdownload.cse.ucsc.edu/goldenPath/hg38/chromosomes/chr1.fa.gz
gunzip chr1.fa.gz
```

* Sunbeam requires that the host DNA sequence files end in ".fasta", so it can
find them automatically.  Let's use the `mv` command to rename this file.

```{bash}
mv chr1.fa chr1.fasta
```

* The database of bacterial genomes comes pre-built from the homepage of our
taxonomic assignment software, Kraken.  We'll download that using the `wget` program.

```{bash}
cd ~
wget https://ccb.jhu.edu/software/kraken/dl/minikraken_20171101_4GB_dustmasked.tgz
tar xvzf minikraken_20171101_4GB_dustmasked.tgz
```
## Configure Sunbeam

* Now that we have reference databases, we need to add them to our configuration
file.  We'll use `nano` to open and modify this file directly in our termial

```{bash}
cd ~
nano workshop-project/sunbeam_config.yml
```

* The configuration values are below.  You'll need to navigate to the right spot in your configuration file, and substitute the directory name "kylebittinger" with your google username.

```
host_fp: "/home/kylebittinger/human"
```

```
kraken_db_fp: "/home/kylebittinger/minikraken_20171101_4GB_dustmasked"
```

* The default configuration for Sunbeam uses 4 threads, but we have 16 threads available, since our cloud machine has 8 cores. Let's use all threads we have.

```
threads: 16
```

## Run the pipeline

* We are ready to actually run the pipeline.  All the information about how
to run the pipeline is in our configuration file, so we'll provide that to
Sunbeam (`--configfile` argument).  We'll also let Sunbeam know how many CPU
cores we'd like to use (`--jobs` argument).

```{bash}
cd ~
sunbeam run --configfile workshop-project/sunbeam_config.yml --jobs 8
```

{% include note.html content="expect the full pipeline to take about 20 minutes to complete the analysis of these samples" %}


## Generate a report

* To look at some of our results, we'll install a Sunbeam extension and generate
a report.

```{bash}
cd ~/sunbeam-stable/extensions
git clone https://github.com/sunbeam-labs/sbx_report
conda install --file sbx_report/requirements.txt
```

* Now run the extension you just installed

```{bash}
cd ~
sunbeam run --configfile workshop-project/sunbeam_config.yml final_report
```

## Explore results

* The summary report you just prepared is conveniently available as a single .html file that can be opened in any browser.  The problem is that this file resides on a google-owned harddrive and there is no simple way to open and view .html files directly in the terminal.  So, we need to transfer it to your laptop harddrive.

* Notice that your SSH terminal window has a small gear icon in the upper right-hand corner of the screen.  Click on this and choose *Download file* from the dropdown menu.

* In the pop-up box, enter the path to summary report  `/home/USERNAME/workshop-project/sunbeam_output/reports/final_report.html`, with your own username.

* To wrap-up the workshop, we'll expore and discuss the report together.  Just in case you had any issues retrieving this file from the cloud instance, you can also view a copy of the report [here](http://CHMI-sops.github.io/papers/final_report.html).

{% include important.html content="Be sure to delete your instance at the conclusion of the workshop to avoid charges to your credit card.  You google cloud account will remain active and you should still have >99% of your initial $300 credit remaining to use for analyzing your own data.)." %}

## Practice after workshop

Practice makes perfect (or at least better!).  After destroying your instance, try firing up a fresh instance and run through this entire tutorial again from start to finish, exactly as we've outlined above.  If you can do this without any issues, try the exercise below that uses a completely different dataset.

For this new exercise, you'll be using Sunbeam to analyze mouse metgenomic data from a [recently published paper](https://doi.org/10.30802/AALAS-CM-17-000084) from Dan's lab.

**A bit of background on this paper and data:**  In the summer of 2015, the University Lab Animal Resources (ULAR) group at UPenn, which oversees all veterinary care and support for research animals on campus, began to notice diarrhea in a few cages of immuno-compromised mice. If you’re not familiar with mouse models for research, there a many genetically engineered mice that lack various immune system components. The particular mice that fell ill are what we would call NSG and NSGS mice, strains that are effectively devoid of nearly all aspects of the immune system. As such, these mice are ideal recipients for xenografts (i.e. human tumor grafts) and critical for understanding cancer biology and therpeutics, but they also pose a real challenge in terms of infection control. You can probably guess where this is going. Despite the strictest precautions, what started out as a few cages of sick mice quickly became an outbreak of diarrheal disease, eventually decimating the entire suite.

After extenisve molecular and culture-based diagnostics turned up negative, shotgun metagenomics on stool samples from affected and control mice was carried out.  **Your goal is to identify putative organisms associated with the outbreak.**

A few things to note about this exercise:

* The data you'll use is summarized in the table below
* Unlike the example used in the workshop, this data was not  prefiltered to remove host before uploading to SRA, so you'll need to do this yourself. This is mouse data, so you'll need to use a the [mouse reference genome](ftp://ftp.ensembl.org/pub/release-94/fasta/mus_musculus/dna/) to filter out contaminating host reads.


| SRA ID     | description       | reads (millions) |
|------------|-------------------|------------------|
| SRR6051702 | control mouse #3  | 12,000,000       |
| SRR6051704 | control mouse #4  | 12,000,000       |
| SRR6051710 | control mouse #5  | 12,000,000       |
| SRR6051709 | control mouse #6  | 12,000,000       |
| SRR6051703 | infected mouse #1 | 12,000,000       |
| SRR6051708 | infected mouse #2 | 12,000,000       |
| SRR6051705 | infected mouse #6 | 12,000,000       |
| SRR6051706 | infected mouse #8 | 12,000,000       |

{% include links.html %}



