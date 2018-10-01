---
title: Bioinformatics Software
tags: [bioinformatics]
keywords:
summary: "A summary of the bioinformatics software currently installed on our Linux cluster."
sidebar: mydoc_sidebar
permalink: mydoc_software.html
folder: mydoc
---

## Available software
We have a lot of software already installed on the server that covers applications ranging from QC analysis and preprocessing of raw sequence data, transcriptome analysis from RNAseq data, 16S and shotgun metagenomics pipelines, WGS tools, and more.  If you have an account on our cluster, then you already have access to all of the software below, so get started!

If you're looking for a piece of software and don't find it below, just reach out to Dan Beiting to inquire about getting it installed.

| software                                                                    | category                             | how to run                                                                                |
|-----------------------------------------------------------------------------|--------------------------------------|-------------------------------------------------------------------------------------------|
| [anvi'o](https://github.com/merenlab/anvio)                                 | metagenomics, visualization          | ```source activate anvio4```                                                              |
| [bcftools](https://samtools.github.io/bcftools/bcftools.html)               | SNP/variant discovery and genotyping | ```bcftools```                                                                            |
| [bcl2fastq2](https://support.illumina.com/downloads/bcl2fastq-conversion-software-v2-20.html)               | tools for working with genomic interval files (BAM, BED, GFF/GTF, etc.) | ```bedtools```                                                                            |
| [bedtools](https://bedtools.readthedocs.io)                                 | metagenomics, visualization          | ```source activate anvio4```                                                              |
| [blast](https://blast.ncbi.nlm.nih.gov/Blast.cgi)                           | sequence search                      | option include ```blastn```, ```blastp```, or ```blastx```                                |
| [bowtie2](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml)            | sequence alignment                   | ```bowtie2```                                                                             |
| [bwa](http://bio-bwa.sourceforge.net/)                                      | sequence alignment                   | ```bwa```                                                                                 |
| [Circos](http://circos.ca/)                                                 | general visualization                | ```circos```                                                                              |
| [clust](https://github.com/BaselAbujamous/clust)                            | co-expression modules                | ```clust```                                                                               |
| [Cytoscape](http://www.cytoscape.org/)                                      | network analysis                     | navigate to /home/shared/softwares/Cytoscape_v3.5.1 folder.  Double click to open program |
| [deeptools](https://deeptools.readthedocs.io/en/latest/)                    | analysis of HTS data                 | ```deeptools```                                                                           |
| [diamond](https://github.com/bbuchfink/diamond)                           | Accelerated BLAST compatible local sequence aligner                     | ```diamond```                                |
| [EMIRGE](https://github.com/csmiller/EMIRGE)                           | Reconstruct full length rRNA genes from short read data                     | ```emirge.py``` or ```emirge_amplicon.py```                               |
| [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)                                   | generates quality control reports for fastq files.                   | ```fastqc```                                                                     |
| [FastQ Screen](https://www.bioinformatics.babraham.ac.uk/projects/fastq_screen/)                                   | screening fastq files against multiple reference genomes.                   | ```fastq_screen```                                                                     |
| [genome analysis toolkit (gatk)](https://software.broadinstitute.org/gatk/) | SNP/variant discovery and genotyping | ```gatk```                    |
| [GraPhlAn](https://bitbucket.org/nsegata/graphlan/wiki/Home)                | metagenomics, visualization          | ```graphlan.py``` or ```graphlan_annotate.py```                                                                         |
| [Humann2](https://huttenhower.sph.harvard.edu/humann2)                     | metagenomics                         | ```humann2```                                                                       |
| [HTSeq](https://htseq.readthedocs.io/en/release_0.10.0/)                            | great for summarizing alignments to get counts per gene/exons                | ```htseq-count``` or ```htseq-qa```                                                                               |
| [iRep](https://github.com/christophertbrown/iRep)                            | determines replication rates for bacteria from metagenomics                | ```iRep``` or ```bPTR```                                                                              |
| [Kallisto](https://pachterlab.github.io/kallisto/)                          | mapping reads to transcripts         | ```kallisto```                                                                            |
| [KneadData](https://bitbucket.org/biobakery/kneaddata/wiki/Home)                          | removes host or 'contaminating' reads from dataset         | ```kneaddata```                                                                            |
| [Kraken2](https://ccb.jhu.edu/software/kraken/)                          | taxonomic classification system         | ```kraken2```                                                                            |
| [LotuS](http://psbweb05.psb.ugent.be/lotus/documentation.html)                          | taxonomic classification system for 16S data       | ```Perl lotus.pl [options]```                                                                            |
| [Mash](http://mash.readthedocs.io/en/latest/)                               | comparative genomics                 | ```mash```                                                                                |
| [MetaPhlAn](https://bitbucket.org/biobakery/metaphlan2)                     | metagenomics                         | ```metaphlan2.py```                                                                       |
| [MinPath](http://omics.informatics.indiana.edu/MinPath/)                            | biological pathway reconstructions using protein family predictions                | ```MinPath1.4.py```                                                                               |
| [Mothur](https://www.mothur.org/)                                           | 16S marker gene                      | ```mothur```                                                                              |
| [MultiQC](http://multiqc.info)                                   | summarizes log files produced by other tools (*e.g.* STAR, kallisto, FastQC, etc).                   | ```multiqc```                                                                     |
| [Nextflow](https://www.nextflow.io)                                         | workflow management                  | ```nextflow```                                                                            |
| [Picard tools](http://broadinstitute.github.io/picard/)                     | handling HTS file formats            | ```java -jar /usr/local/bin/picard/build/libs/picard.jar```                                                                              |
| [Prokka](https://github.com/tseemann/prokka)                     | genome annotation for prokaryotes            | ```prokka```                                                                              |
| [QIIME2](https://qiime2.org/)                                               | Microbial ecology pipeline for 16S rRNA data                      | ```source activate qiime2```                                                              |
| [QUAST](http://quast.sourceforge.net/index.html) | Quality Assessment Tool for Genome Assemblies | ```quast.py```                                                              |
| [rsem](https://github.com/deweylab/RSEM)                                    | mapping reads to transcripts         | ```rsem-(function)```                                                                     |
| [samtools](http://samtools.sourceforge.net/)                                | handling HTS file formats            | ```samtools```                                                                            |
| [seqtk](https://github.com/lh3/seqtk)                                       | handling HTS file formats            | ```seqtk```                                                                               |
| [Sickle](https://github.com/najoshi/sickle)                            | quality trimming of raw sequences                | ```sickle se``` or ```sickle pe```                                                                               |
| [Sourmash](https://github.com/dib-lab/sourmash)                            | Compute and compare MinHash signatures for DNA data              | ```source activate sourmash_env```                                                                               |
| [SPAdes](http://cab.spbu.ru/software/spades/)                                    | genome assembly from illumina short reads         | ```spades.py [options] -o <output_dir>```                                                                     |
| [SQUID](https://github.com/Kingsford-Group/squid)                                    | find trascriptomic structural variants from RNAseq data         | ```squid```                                                                     |
| [SRA toolkit](https://github.com/ncbi/sra-tools/wiki/Downloads)                                    | tools for accessing sequence data stored on SRA         | e.g. ```fasterq_dump```, and many more                                                                     |
| [Star](https://github.com/alexdobin/STAR)                                   | sequence alignment                   | ```STAR``` (all caps)                                                                     |
| [Sunbeam](https://github.com/eclarke/sunbeam/blob/master/Readme.md)         | metagenomics                         | ```source activate sunbeam```                                                             |
| [Trimmomatic](http://www.usadellab.org/cms/?page=trimmomatic)                            | quality trimming of raw sequences                | ```java -jar /usr/local/bin/trimmomatic-0.33.jar```                                                                               |
| [Trinity](https://github.com/trinityrnaseq/trinityrnaseq/wiki)              | de novo transcriptome assembly       | ```Chrysalis``` (uppercase 'C'), ```inchworm```                                           |
{% include links.html %}

