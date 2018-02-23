---
title: CHMI linux cluster
tags: [bioinformatics]
keywords:
summary: "CHMI maintains a custom configured compute server that runs Linux Ubuntu 16.04 LTS.  This machine has two 6-core Intel Xeon E5-2643v4 CPUs (12 cores total), 512 Gb of RAM and 10Tb of RAID1 storage.  If you are a PennVet lab and wish to use this machine, please contact Dan Beiting (beiting@upenn.edu) for more information."
sidebar: mydoc_sidebar
permalink: mydoc_linux.html
folder: mydoc
---

## General rules
Use of the cluster is free-of-charge to approved labs.  However, to protect the cluster from abuse and prevent issues with storage, we have a few rules all users must follow.  Failure to adhere to these rules will result in a warning. Additional rule violations will result in suspension of your account.  Here are the rules:

* We will set-up your account and install any software you may need.  Please do not install software yourself.
* In addition to your home account with is present at ```/home/username``` on the server, you will also be given a data folder that is located on ```/data/username```.  All data must be stored in this directory **not** your ```home/username``` folder.
* Data storage space is limited (10Tb goes quickly!), so we periodically montior storage space and may request that data not currently in use be moved off the cluster.
* We require a strong password for each account.  We will set this password for you, and ask that you do not change it.

## Configuring a new user (CHMI only)

```
sudo adduser [username] #adds a new user to the home directory
usermod -aG sudo username #gives the new user sudo priveledges
```

Give the user access to all software on the server
* navigate to ```/home/shared/softwares/``` and open the text file called ```shared_software_list```.  This contains paths to all software.  We routinely update this, so be sure to check back for new software paths:

* copy the contents of this file (highlight all, right-click, choose copy)
* open the terminal, and type ```nano .profile```.
* scroll to the bottom of this file in the terminal and paste the paths under the last line
* hit 'control x' to exit nano.  You'll be asked if you want to save changes -- select 'y' to save, then hit enter to finalize changes and close nano.
* for these changes to take effect, close the terminal, log out and then back in.  
* you should now have access to all the software listed below



## Connecting to the server

```
ssh username@130.91.255.137
#you'll be prompted to enter your password and then you'll be connected
#once connected you'll see a new prompt with username@ubuntu1604
```


## Available software

| software                                                                    | category                             | how to run                                                                                |
|-----------------------------------------------------------------------------|--------------------------------------|-------------------------------------------------------------------------------------------|
| [mothur](https://www.mothur.org/)                                           | 16S marker gene                      | ```mothur```                                                                              |
| [QIIME2](https://qiime2.org/)                                               | 16S marker gene                      | ```source activate /home/beiting/anaconda3/envs/qiime2-2018.2```                         |
| [Sunbeam](https://github.com/eclarke/sunbeam/blob/master/Readme.md)         | metagenomics                         | ```source activate sunbeam```                                                             |
| [MetaPhlAn](https://bitbucket.org/biobakery/metaphlan2)                     | metagenomics                         | ```metaphlan2.py```                                                                       |
| [GraPhlAn](https://bitbucket.org/nsegata/graphlan/wiki/Home)                | metagenomics, visualization          | ```graphlan.py```                                                                         |
| [anvi'o](https://github.com/merenlab/anvio)                                 | metagenomics, visualization          | ```source activate /home/beiting/anaconda3/envs/anvio3```                                 |
| [Circos](http://circos.ca/)                                                 | general visualization                | ```circos```                                                                              |
| [Cytoscape](http://www.cytoscape.org/)                                      | network analysis                     | navigate to /home/shared/softwares/Cytoscape_v3.5.1 folder.  Double click to open program |
| [bowtie2](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml)            | sequence alignment                   | ```bowtie2```                                                                             |
| [bwa](http://bio-bwa.sourceforge.net/)                                      | sequence alignment                   | ```bwa```                                                                                 |
| [Star](https://github.com/alexdobin/STAR)                                   | sequence alignment                   | ```STAR``` (all caps)                                                                     |
| [kallisto](https://pachterlab.github.io/kallisto/)                          | mapping reads to transcripts         | ```kallisto```                                                                            |
| [rsem](https://github.com/deweylab/RSEM)                                    | mapping reads to transcripts         | ```rsem-(function)```                                                                     |
| [Mash](http://mash.readthedocs.io/en/latest/)                               | comparative genomics                 | ```mash```                                                                                |
| [Nextflow](https://www.nextflow.io)                                         | workflow management                  | ```nextflow```                                                                            |
| [Trinity](https://github.com/trinityrnaseq/trinityrnaseq/wiki)              | de novo transcriptome assembly       | ```Chrysalis``` (uppercase 'C'), ```inchworm```                                           |
| [Picard tools](http://broadinstitute.github.io/picard/)                     | handling HTS file formats            | ```picard```                                                                              |
| [samtools](http://samtools.sourceforge.net/)                                | handling HTS file formats            | ```samtools```                                                                            |
| [seqtk](https://github.com/lh3/seqtk)                                       | handling HTS file formats            | ```seqtk```                                                                               |
| [deeptools](https://deeptools.readthedocs.io/en/latest/)                    | analysis of HTS data                 | ```deeptools```                                                                           |
| [bcftools](https://samtools.github.io/bcftools/bcftools.html)               | SNP/variant discovery and genotyping | ```bcftools```                                                                            |
| [genome analysis toolkit (gatk)](https://software.broadinstitute.org/gatk/) | SNP/variant discovery and genotyping | ```java -jar /home/shared/softwares/gatk-3.8-0/GenomeAnalysisTK.jar```                    |
| [blast](https://blast.ncbi.nlm.nih.gov/Blast.cgi)                           | sequence search                      | option include ```blastn```, ```blastp```, pr ```blastx```                                |
| [clust](https://github.com/BaselAbujamous/clust)                            | co-expression modules                | ```clust```                                                                               |
{% include links.html %}

