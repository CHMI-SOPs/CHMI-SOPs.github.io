---
title: Cell Ranger
tags: [bioinformatics, single_cell_genomics]
keywords:
summary: "Cell Ranger is the command-line software for preprocessing raw sequence data from a 10X single cell sequencing experiment.  The output from Cell Ranger os a count matrix where rows are genes and columns are individual cells."
sidebar: mydoc_sidebar
permalink: mydoc_CellRanger.html
folder: mydoc
---

## Intro

## Before starting

The instructions below assume the following:

* You have Cell Ranger installed on a computer with [the recommended compute resources](https://support.10xgenomics.com/single-cell-atac/software/overview/system-requirements).
* Cell Ranger is in your [$PATH](https://opensource.com/article/17/6/set-path-linux).
* You have a .csv file (e.g. in Excel) that identifies samples with barcodes
* You have access to the raw .bcl file from a single cell sequencing experiment.
* You have some other basic linux software installed on the same computer and also in your $PATH, including wget, 

## Prepare your reference genome file

### mouse and human

If your cells came from mice or humans, then you're in luck!  You can just download the reference file from [here]().

### other genomes

If your cells are **not** from mouse of humans, then you'll need to do a bit of work to get your reference file set-up.  

Begin by downloading the reference genome fasta file and .gtf file for your organism of interest.  You can browse available files at the [Ensemble FTP site](https://useast.ensembl.org/info/data/ftp/index.html).

Once you've identified the fasta (.fa) and .gtf files you need, download them using wget

```shell
# using rat as an example
# first the genome fasta file
wget ftp://ftp.ensembl.org/pub/release-99/fasta/rattus_norvegicus/dna/Rattus_norvegicus.Rnor_6.0.dna.toplevel.fa.gz
# then the .gtf file
wget ftp://ftp.ensembl.org/pub/release-99/gtf/rattus_norvegicus/Rattus_norvegicus.Rnor_6.0.99.chr.gtf.gz
```

Unzip both files using gunzip

```shell
gunzip Rattus_norvegicus.Rnor_6.0.99.chr.gtf.gz
gunzip Rattus_norvegicus.Rnor_6.0.dna.toplevel.fa.gz
```

Make the GTF

```shell
cellranger mkgtf \
Rattus_norvegicus.Rnor_6.0.99.chr.gtf \
Rattus_norvegicus.Rnor_6.0.99.chr.filtered.gtf \
--attribute=gene_biotype:protein_coding
```

Make the reference 

```shell
cellranger mkref \
--genome=Rattus_norvegicus_genome_forRNA \
--fasta=Rattus_norvegicus.Rnor_6.0.dna.toplevel.fa \
--genes=Rattus_norvegicus.Rnor_6.0.99.chr.filtered.gtf 
```

## Prepare fastq files

#go to the correct folder
cd /data/brinsterlab/Fresh_Rat1_10x

#here "id" is the . "run" is t in. "csv" is a 

```shell
cellranger mkfastq --id=fresh_rat_10x_1 \ 
                    # name you're giving to the fastq group
                   --run=/data/brinsterlab/BCLrun392 \ 
                    # the folder with your BCL files
                   --csv=/data/brinsterlab/Fresh_Rat1_10x/rat_samples_for_demultiplex.csv
                    # csv file that contains the barcode assignments and sample names.
```

## Generate counts

### process one sample at a time

Here we have a few variables to define

"id" is a name for the output
#"fastqs" is the path to the fastq files, which should end in the serial number for the flow cell used.
#"sample" is the name of the sample to be processed - this has to match the name you gave in your csv file!
#"transcriptome" is the path to your transcriptome
#be aware which folder you are in when you run this command!

cellranger count --id=Count_output_UnselectedRat1 \
                 --fastqs=/data/brinsterlab/Fresh_Rat1_10x/fresh_rat_10x_1/outs/fastq_path/HT55LBGXC/ \
                 --sample=FreshRatUnselected1 \
                 --transcriptome=/data/brinsterlab/ratReferences/Rattus_norvegicus_genome_forRNA

cellranger count --id=Count_output_EpCAMrat1 \
                 --fastqs=/data/brinsterlab/Fresh_Rat1_10x/fresh_rat_10x_1/outs/fastq_path/HT55LBGXC/ \
                 --sample=FreshRatEpCAM1 \
                 --transcriptome=/data/brinsterlab/ratReferences/Rattus_norvegicus_genome_forRNA


### process multiple samples

This is useful if you have multiple samples, or if you used [feature barcoding](https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/feature-bc)to multiplex multiple samples in a single well of a 10X chip.

{% include note.html content="There are no ```sample``` or ```fastqs``` arguments when processing multiple samples, instead, there are two .csv files - one for libraries and a second for your feature reference." %}

cellranger count --id=Count_output_combined2 \
                 --libraries=/data/brinsterlab/libraries.csv \
                 --feature-ref=/data/brinsterlab/featurereference.csv \
                 --transcriptome=/home/shared/Cellranger_references/refdata-cellranger-mm10-3.0.0




{% include links.html %}
