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
* You have access to the raw .bcls file from a single cell sequencing experiment.
* You have some other basic linux software installed on the same computer (also in your $PATH), including [wget](https://www.gnu.org/software/wget/) for downloading files.

## Prepare your reference genome file

### mouse and human

If your cells came from mice or humans, then you're in luck!  You can just download the reference file from [here]().  Alternatively, if you're working on our linux machine, then you can find these references and more in /data/reference_db/10X

### other genomes

If your cells are **not** mouse or human, then you'll need to do a bit of work to get your reference file set-up.  

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
gunzip Rattus_norvegicus.Rnor_6.0.99.chr.gtf.gz # gtf file from Ensembl
gunzip Rattus_norvegicus.Rnor_6.0.dna.toplevel.fa.gz # genome fasta from Ensembl
```

Use Cell Ranger's **[mkgtf](https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/advanced/references#mkgtf)** function to filter your original GTF file to leave only those genes that are annotated as protein coding.  

```shell
cellranger mkgtf \
Rattus_norvegicus.Rnor_6.0.99.chr.gtf \ # gtf file from Ensembl
Rattus_norvegicus.Rnor_6.0.99.chr.filtered.gtf \ # output name for filtered gtf
--attribute=gene_biotype:protein_coding # filtering on protein coding genes
```

Use Cell Ranger's **[mkref](https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/advanced/references#mkref)** function to build a index for read alignment.  This uses the splice-aware aligner, [STAR](https://github.com/alexdobin/STAR) to accomplish this.

```shell
cellranger mkref \
--genome=Rattus_norvegicus_genome_forRNA \ #output folder name
--fasta=Rattus_norvegicus.Rnor_6.0.dna.toplevel.fa \ # reference fasta file 
--genes=Rattus_norvegicus.Rnor_6.0.99.chr.filtered.gtf \ # filtered gtf file from above
--nthreads=24 # number of threads to use (set to 24 based on our linux machine)
```

## Prepare fastq files

#go to the correct folder
cd /data/brinsterlab/Fresh_Rat1_10x

Use Cell Ranger's **[mkfastq](https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/using/mkfastq)** function to convert the bcl files from your illumina sequencing run to fastq files.  mkfastq is basically a wrapper around Illumina's bcl2fastq program, but with a few extra features, namely that it handles 10X indices for demultiplexing samples, and generates some quality control metrics that are specific to the 10X platform.

```shell
cellranger mkfastq --id=fresh_rat_10x_1 \ # name you're giving to the fastq group
                   --run=/data/brinsterlab/BCLrun392 \ # the folder with your BCL files
                   --csv=/data/brinsterlab/Fresh_Rat1_10x/rat_samples_for_demultiplex.csv # csv file that contains the barcode assignments and sample names.
```

## Generate counts

### process one sample at a time

Use Cell Ranger's **[count](https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/using/tutorial_ct)** function aligns sequencing reads in FASTQ files to your reference transcriptome and generates a .cloupe file for visualization and analysis in Loupe Browser, along with a number of other outputs compatible with other publicly-available tools for further analysis.

```shell
cellranger count --id=Count_output_UnselectedRat1 \ # name for the output
                 --fastqs=/data/brinsterlab/Fresh_Rat1_10x/fresh_rat_10x_1/outs/fastq_path/HT55LBGXC/ \ # path to the fastq files, which should end in the serial number for the flow cell used.
#be aware which folder you are in when you run this command!
                 --sample=FreshRatUnselected1 \ # name of the sample to be processed. must match the name you gave in your csv file!
                 --transcriptome=/data/brinsterlab/ratReferences/Rattus_norvegicus_genome_forRNA # path to your transcriptome
```

### process multiple samples

This is useful if you have multiple samples, or if you used [feature barcoding](https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/feature-bc) to multiplex multiple samples in a single well of a 10X chip.

{% include note.html content="There are no ```sample``` or ```fastqs``` arguments when processing multiple samples, instead, there are two .csv files - one for libraries and a second for your feature reference." %}

```shell
cellranger count --id=Count_output_combined2 \
                 --libraries=/data/brinsterlab/libraries.csv \
                 --feature-ref=/data/brinsterlab/featurereference.csv \
                 --transcriptome=/home/shared/Cellranger_references/refdata-cellranger-mm10-3.0.0
```



{% include links.html %}
