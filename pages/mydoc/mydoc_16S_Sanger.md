---
title: Identification of unknown bacterial isolates using Sanger sequencing of the 16S rRNA gene
tags: [microbiome]
keywords:
summary: "Identification of unknown bacterial isolates using Sanger sequencing of the 16S rRNA gene"
sidebar: mydoc_sidebar
permalink: mydoc_16S_Sanger.html
folder: mydoc
---

## Before starting
* [GoTaq Master Mix documentation](https://www.promega.com/-/media/files/resources/protocols/product-information-sheets/g/gotaq-green-master-mix-protocol.pdf)

## Materials
* Promega GoTaq Green Master Mix (-20C)
* Molecular biology grade, nuclease-free water (-20C or room temperature)
* 27F Primer
* 1492R primer
* 515F primer (optional)
* QIAGEN QIAquick PCR purification kit
* 100% Ethanol

## Step 1: Obtain genomic DNA

* Extract DNA using QIAGEN DNeasy kit (bacterial protocol) or other method of bacterial DNA extraction.
* Quantify DNA using the Qubit.

## Step 2: PCR Amplify the full-length 16S rRNA gene

* Prepare the following reaction mixture in each PCR well/tube

* Place in thermocycler and run the following program under CHMI -> PCR -> 16SFULL (bold indicates 30 cycles)


| Component | Volume | Final Concentration |
|-------|--------|--------|
| GoTaq Green Master Mix, 2X | 25 uL | 1X |
| 27F primer, 10 uM  | 1 uL | 0.2 uM |
| 1492R primer, 10 uM | 1 uL | 0.2 uM |
| DNA template | 1-5 uL | ~150 ng template (< 250 ng) |
| Nuclease-free water to | 50 uL | NA |

{% include note.html content="If I have many reactions to perform, I make a master mix including all of the components except for the DNA." %}

{% include note.html content="The original IDT stock solutions of the primers are at a concentration of 100 uM." %}


| Temp (C) | Time (min:sec) |
|-------|--------|
| 95 | 2:00 |
| **95** | **0:30** |
| **55** | **0:30** |
| **72** | **1:40** |
| 72 | 5:00 |
| 12 | hold |

## Step 3. Clean up the PCR products 

* Follow the QIAGEN QIAquick PCR purification protocol. 

## Step 4: QC on purified PCR products

* Perform Qubit quantification on all samples

* Optional: Select a few samples and run an agarose gel or tapestation (DNA 5000 tape) to ensure there is a major product at approximately 1400 bp.

{% include note.html content="There may be other amplification products, but as long as the 1400 bp product is the most dominant, the PCR products do not need to be gel purified." %}

## Step 5: Submit PCR products for sequencing

* Follow the [submission guide instructions](https://www.med.upenn.edu/genetics/dnaseq/submission.shtml) carefully for submitting to the UPenn DNA sequencing facility

* Each tube should contain the following:
	* 6 uL of PCR product at 25 ng/uL
	* 3 uL of the desired primer at 1.1 uM
	* If your DNA is not sufficiently concentrated, just submit the sample anyway, your results may be fine.
	* The sequencing facility suggests 10 ng of DNA per 100 bp.

{% include note.html content="We typically submit 3 tubes per sample: a 27F, 515F, and 1492R. These three sequencing results help me assemble the 16S gene without gaps." %}

{% include note.html content="Use strip tubes with the strip caps for easy removal if you have <52 samples. If you have more than 52 samples, submit your samples in a plate with the HT option." %}

{% include important.html content="The first tube of each 8-tube set should have 'Beiting' on it and the second tube should have your last name. Label your samples sequentially 1, 2, 3, etc...." %}

## Step 6: Interpret results

* Assemble the sequencing reads using your favorite assembly software (Geneious has an easy-to-use interface).

* Obtain the full length, consensus sequence seach for the best match using either [BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastSearch&BLAST_SPEC=MicrobialGenomes) or a recent tool called Bitsliced Genomic Signature Index (BIGSI) which is available [here](http://www.bigsi.io/) and you can read more about on the [Github page for BIGSI](https://github.com/Phelimb/BIGSI)

{% include important.html content="No database is comprehensive and there's always bias in what is represented in a database. In addition, since you're only considering one gene (16S rRNA), this also affects your specificity and resolution for identifying species." %}


{% include links.html %}

