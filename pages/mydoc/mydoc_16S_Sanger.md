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
* The protocol uses three primers (two forward and one reverse) to generate amplicons for Sanger sequencing.  Combining the seqeunce data for the three amplicons generates a contiguous sequence that spans that majority of the full 16S rRNA gene, therby giving you a decent idea of bacterial identity.  PCR reactions use the [GoTaq Master Mix](https://www.promega.com/-/media/files/resources/protocols/product-information-sheets/g/gotaq-green-master-mix-protocol.pdf)

* PCR Primers are as follows:

| name | Sequence (5' -> 3') |
|-------|--------|
| 27fwd | AGA GTT TGA TCM TGG CTC AG |
| 515fwd | GTG CCA GCM GCC GCG GTA A |
| 1492rev | CGG TTA CCT TGT TAC GAC TT |

## Materials
* Promega GoTaq Green Master Mix (-20C)
* Molecular biology grade, nuclease-free water (-20C or room temperature)
* 27F Primer
* 1492R primer
* 515F primer
* QIAGEN QIAquick PCR purification kit
* 100% Ethanol

## Step 1: Obtain genomic DNA

* Extract DNA using QIAGEN DNeasy kit (bacterial protocol) or other method of bacterial DNA extraction.
* Quantify DNA using the Qubit.

## Step 2: PCR Amplify the full-length 16S rRNA gene

* Prepare the following, per sample, as a master mix:

| Component | Volume | Final Concentration |
|-------|--------|--------|
| GoTaq Green Master Mix, 2X | 25 uL | 1X |
| 27F primer, 100 uM  | 0.2 uL | 0.2 uM |
| 1492R primer, 100 uM | 0.2 uL | 0.2 uM |
| Nuclease-free water | 19.6 uL | NA |
| Total Volume | 45 uL | 

{% include note.html content="Make a master mix including all of the components except for the DNA." %}

{% include note.html content="The original IDT stock solutions of the primers are at a concentration of 100 uM. Our primers are at this concentration in the freezer. If your primers are not this concentration, adjust the volume added." %}

* In a 96-well plate, pipette 45uL of prepared master mix per sample.

* Add 5uL of extracted DNA template (~150 ng template (< 250 ng)) and pipette to mix. Each sample will have a total volume of 50uL.

* Place in thermocycler and run the following program under SANGER folder -> 16SFULL (bold indicates 30 cycles)

| Temp (C) | Time (min:sec) |
|-------|--------|
| 95 | 2:00 |
| **95** | **0:30** |
| **55** | **0:30** |
| **72** | **1:40** |
| 72 | 5:00 |
| 12 | hold |

## Step 3:  Cleanup

* Vortex AMPure XP beads before each use.  Vortex AMPure XP beads frequently to make sure that beads are evenly distributed.

* Add 50 μl of AMPure XP beads to each well.

* Pipette to mix around 15 times to ensure the beads are mixed well with PCR products.

* Incubate at room temperature for 5 minutes.

* Place on a magnetic stand and wait until the liquid is clear (~2 minutes).

* Remove and discard all supernatant from each well.

* Keeping the samples on the magnetic stand, wash 2 times as follows:
- Add 180 μl fresh 80% EtOH to each well.
- Incubate on the magnetic stand for 30 seconds.
- Remove and discard all supernatant from each well.

* Using a 20 μl pipette, remove residual 80% EtOH from each well.

* Let the plate stand on the magnet at RT until dry, usually less than 5 minutes. When dry, the beads will appear matte and cracked. 

* Remove from the magnetic stand when samples are dry.

* Add 52.5 μl RSB to each well.

* Pipette to mix well and resuspend beads.

* Incubate at room temperature for 2 minutes.

* Place on a magnetic stand and wait until the liquid is clear (~2 minutes).

* Transfer 50 μl supernatant to a new plate.

{% include note.html content="This is a safe stopping point.  If you choose to stop here, seal the plate and store at -20°C for up to 7 days. Alternatively, leave in the thermal cycler overnight" %}

## Step 4: QC on purified PCR products

* Perform Qubit quantification on all samples

* Optional: Select a few samples and run an agarose gel or tapestation (DNA 5000 tape) to ensure there is a major product at approximately 1400 bp.

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

* Assemble the sequencing reads using your favorite assembly software.  We use Geneious (commercial software) because it has an easy-to-use interface.  .Ab1 files for all three amplicons can be dragged onto the Geneious interface and the *de novo assembly* tool is used to produce a consensus contig. 

* Take the highest quality portion of the full length consensus sequence and seach for the best match using either [BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastSearch&BLAST_SPEC=MicrobialGenomes) or a recent tool called Bitsliced Genomic Signature Index (BIGSI) which is available [here](http://www.bigsi.io/) and you can read more about on the [Github page for BIGSI](https://github.com/Phelimb/BIGSI)

{% include important.html content="No database is comprehensive and there's always bias in what is represented in a database. In addition, since you're only considering one gene (16S rRNA), this also affects your specificity and resolution for identifying species." %}


{% include links.html %}

