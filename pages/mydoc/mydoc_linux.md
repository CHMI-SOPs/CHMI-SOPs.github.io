---
title: CHMI linux cluster
tags: [bioinformatics]
keywords:
summary: "CHMI maintains a custom configured compute server that runs Linux Ubuntu 16.04 LTS.  This machine has two 6-core Intel Xeon E5-2643v4 CPUs (12 cores total), 512 Gb of RAM and 18Tb of RAID1 storage.  If you are a PennVet lab and wish to use this machine, please contact Dan Beiting (beiting@upenn.edu) for more information."
sidebar: mydoc_sidebar
permalink: mydoc_linux.html
folder: mydoc
---

## General rules
Use of the cluster is free-of-charge to approved labs.  However, to protect the cluster from abuse and prevent issues with storage, we have a few rules all users must follow.  Failure to adhere to these rules will result in a warning. Additional rule violations will result in suspension of your account.  Here are the rules:

* We will set-up your account and install any software you may need.  Please do not install software yourself.
* In addition to your home account which is located at ```/home/username``` on the server, you will also be given a data folder that is located on ```/data/username```.  All data must be stored in this directory **not** your ```/home/username``` folder.
* Data storage space is limited (18Tb goes quickly!), so we periodically montior storage space and may request that data not currently in use be moved off the cluster.
* We require a strong password for each account.  We will set this password for you, and ask that you do not change it.

## RStudio server
As much as possible, we prefer to use R for managing, analyzing and plotting data.  This preference is largely motivated by the excellent community support for R, the exceptional RStudio interface for interacting with R, and the growing number of bioinformatics tools within the [bioconductor]() suite of applications.

Although we frequently use RStudio on our personal computers, we also provide access to a server version of RStudio.  This can be useful when your work requires more computing power.  Click [**here**]() to access our RStudio server directly in your web browser.  Login with the same credentials you use to access the linux machine.  Feel free to customize your RStudio server by installing any packages you need for your work.

## Creating and managing user accounts (CHMI only)

### Add a new user
First, add a new user to the home directory
```
sudo adduser [username] 
```
Then give the new user sudo priveledges
```
usermod -aG sudo username 
```
### Delete a user
```
sudo deluser --remove-home [username]
```

### Delete a directory and its contents
```
sudo rm -rf [directory]
```

## Installing software (CHMI only)
* All software *must* be installed only in ```/usr/local/bin/```
* Once installed, you'll need to add the path to the executable to your PATH variable. To do this, open the system profile (a text document, so it can be opened with either the nano or vim text editors, both of which are built into the linux system)
```
sudo nano /etc/profile
```
* scroll to the bottom of the ```/etc/profile``` file in nano and add the path to the new software.  For example, if you had downloaded the program kallisto, you would add ```export PATH=$PATH:/usr/local/bin/kallisto``` to the bottom of the ```/etc/profile``` document.
* now your program will be available to any user, regardless of the directory they are working in.

## Connecting to the Linux server

```
ssh username@130.91.255.137
#you'll be prompted to enter your password and then you'll be connected
#once connected you'll see a new prompt with username@ubuntu1604
```


## Available software

| software                                                                    | category                             | how to run                                                                                |
|-----------------------------------------------------------------------------|--------------------------------------|-------------------------------------------------------------------------------------------|
| [mothur](https://www.mothur.org/)                                           | 16S marker gene                      | ```mothur```                                                                              |
| [QIIME2](https://qiime2.org/)                                               | 16S marker gene                      | ```source activate qiime2```                                                              |
| [Sunbeam](https://github.com/eclarke/sunbeam/blob/master/Readme.md)         | metagenomics                         | ```source activate sunbeam```                                                             |
| [MetaPhlAn](https://bitbucket.org/biobakery/metaphlan2)                     | metagenomics                         | ```metaphlan2.py```                                                                       |
| [Humann2](https://huttenhower.sph.harvard.edu/humann2)                     | metagenomics                         | ```humann2```                                                                       |
| [GraPhlAn](https://bitbucket.org/nsegata/graphlan/wiki/Home)                | metagenomics, visualization          | ```graphlan.py``` or ```graphlan_annotate.py```                                                                         |
| [anvi'o](https://github.com/merenlab/anvio)                                 | metagenomics, visualization          | ```source activate anvio3```                                                              |
| [Circos](http://circos.ca/)                                                 | general visualization                | ```circos```                                                                              |
| [Cytoscape](http://www.cytoscape.org/)                                      | network analysis                     | navigate to /home/shared/softwares/Cytoscape_v3.5.1 folder.  Double click to open program |
| [bowtie2](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml)            | sequence alignment                   | ```bowtie2```                                                                             |
| [bwa](http://bio-bwa.sourceforge.net/)                                      | sequence alignment                   | ```bwa```                                                                                 |
| [Star](https://github.com/alexdobin/STAR)                                   | sequence alignment                   | ```STAR``` (all caps)                                                                     |
| [kallisto](https://pachterlab.github.io/kallisto/)                          | mapping reads to transcripts         | ```kallisto```                                                                            |
| [rsem](https://github.com/deweylab/RSEM)                                    | mapping reads to transcripts         | ```rsem-(function)```                                                                     |
| [SPAdes](http://cab.spbu.ru/software/spades/)                                    | genome assembly from illumina short reads         | ```spades.py [options] -o <output_dir>```                                                                     |
| [Mash](http://mash.readthedocs.io/en/latest/)                               | comparative genomics                 | ```mash```                                                                                |
| [Nextflow](https://www.nextflow.io)                                         | workflow management                  | ```nextflow```                                                                            |
| [Trinity](https://github.com/trinityrnaseq/trinityrnaseq/wiki)              | de novo transcriptome assembly       | ```Chrysalis``` (uppercase 'C'), ```inchworm```                                           |
| [Picard tools](http://broadinstitute.github.io/picard/)                     | handling HTS file formats            | ```java -jar /usr/local/bin/picard/build/libs/picard.jar```                                                                              |
| [samtools](http://samtools.sourceforge.net/)                                | handling HTS file formats            | ```samtools```                                                                            |
| [seqtk](https://github.com/lh3/seqtk)                                       | handling HTS file formats            | ```seqtk```                                                                               |
| [deeptools](https://deeptools.readthedocs.io/en/latest/)                    | analysis of HTS data                 | ```deeptools```                                                                           |
| [bcftools](https://samtools.github.io/bcftools/bcftools.html)               | SNP/variant discovery and genotyping | ```bcftools```                                                                            |
| [genome analysis toolkit (gatk)](https://software.broadinstitute.org/gatk/) | SNP/variant discovery and genotyping | ```gatk```                    |
| [blast](https://blast.ncbi.nlm.nih.gov/Blast.cgi)                           | sequence search                      | option include ```blastn```, ```blastp```, or ```blastx```                                |
| [diamond](https://github.com/bbuchfink/diamond)                           | Accelerated BLAST compatible local sequence aligner                     | ```diamond```                                |
| [clust](https://github.com/BaselAbujamous/clust)                            | co-expression modules                | ```clust```                                                                               |
| [MinPath](http://omics.informatics.indiana.edu/MinPath/)                            | biological pathway reconstructions using protein family predictions                | ```MinPath1.4.py```                                                                               |
{% include links.html %}

