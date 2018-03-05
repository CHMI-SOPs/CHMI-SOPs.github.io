---
title: RNAseq library prep for low input samples 
tags: [library_prep, transcriptomics]
keywords: transcriptomics, library preparation
summary: "This protocol walks you through preparing a library for RNAseq when your starting amount of RNA is less than ~75ng.  This is a useful protocol if you are working with sorted cells"
sidebar: mydoc_sidebar
permalink: mydoc_lowInput_RNAseq.html
folder: mydoc
---
# Day 1


## Documentation

[Clontech SMART-Seq v4 Ultra Low Input RNA Kit](http://www.clontech.com/US/Products/cDNA_Synthesis_and_Library_Construction/Next_Gen_Sequencing_Kits/Single_cell_RNA_Seq_Kits_for_mRNA_seq/ibcGetAttachment.jsp?cItemId=104008&fileId=7349924&sitex=10020:22372:US). This is an excellent kit for preparing cDNA very low amounts of RNA.  We have used this kit to prepare cDNA from < 100 cells.

{% include important.html content="the success of this kit is dependent on the ability of Illumina's rRNA depletion beads to bind rRNAs in your target species.  Check [this list](https://www.illumina.com/products/selection-tools/ribo-zero-kit-species-compatibility.html#hmr) for compatability of the mouse/rat/human rRNA 'riboGold' depletion reagent with other species." %}


## What you'll need

{% include important.html content="The following items are included in the Clontech SMART-v4 kit and are stored at -20C" %}

* 10x Lysis buffer
* RNase inhibitor (40U/ul)
* SeqAmp DNA Polymerase
* SeqAmp PCR Buffer
* SMART-Seq v4 Oligonucleotide (48 µM)
* 3’ SMART-Seq CDS Primer II A (12 µM) 
* PCR Primer II A (12 µM) 
* 5X Ultra Low First-Strand Buffer
* SMARTScribe™ Reverse Transcriptase (100 U/µl)
* Nuclease-Free Water
* Elution Buffer (10 mM Tris-Cl, pH 8.5)
* 10X AfaI Buffer
* 0.1% BSA
* AfaI (10 U/µl) 


## A few important comments before you start

* You'll split this protocol into three days: day 1 will be your sort and cell lysis, day 2 will be RNA isolation and cDNA generation, day 3 will be Illumina NexteraXT library prep.
* Use only filter pipette tips and clean your area so it is free of RNases.  
* Certain steps, such as 1st-strand cDNA synthesis must be carried out in a PCR clean hood
* Be sure to include the negative and positive controls that come with the kit.
* this protocol uses 0.2ml PCR tubes, but if you're working with many samples you may find it easier to use a 96-well plate

## Day 1: RNA extraction

### OPTION A: sorting cells

* Prepare 10x reaction buffer by mixing 19 uL of 10x Lysis Buffer with 1 uL of RNase inhibitor.  This is enough for ~20 samples. Scale up as needed, but be sure to maintain 19:1 ratio of lysis buffer to RNase inhibitor

{% include note.html content="The 10x lysis buffer contains detergent, so avoid creating bubbles when pipetting.%}

* Prepare 1x reaction buffer by mixing 9.5 uL nuclease-free water with 1 uL of 10x reaction buffer.  This enough to sort one sample, so be sure to scale up as needed.

* Add 5ul of 1x reaction buffer to collection eppendorf tube and sort directly into this tube.  

* Immediately after sample is sorted, add an additional 5.5 uL of 1x reaction buffer to tube.

* Store at -80C until ready to begin cDNA synthesis.  You will go directly from cell lysate to cDNA with no intermediate RNA isolation step.

### OPTION B: purified RNA

* If you have 10's or 100's of thousands of cells, it probably makes sense to isolate RNA first and then use the same amount of total RNA for the cDNA reaction.  We recommend using a kit specifically designed for efficient recovery of RNA from low numbers of cells, and have had success with the [ARCTURUS PicoPure RNA isolation kit](https://www.thermofisher.com/order/catalog/product/KIT0204).

## Day 2: cDNA preparation

{% include warning.html content="The SMART-v4 is an extremely sensitive cDNA synthesis (that's the whole point!), which means that it is imperative that you avoid even small amounts of contamination from environmental RNA.  **Today's works should be carried out in a PCR clean hood.**" %}

* Thaw the following items from the SMART-v4 kit
	* 10x Lysis Buffer
	* RNase inhibitor
	* 5X Ultra Low First Strand Buffer
	* SMARTSeq4 Oligonucleotide
	* 3' SMART-Seq CDS Primer (both primers labeled IIA) on ice. 

* Thaw your sorted samples or RNA on ice (depending on whether you did Option A or B above).

* If working with RNA, take 1-9.5 uL of your purified RNA (the kit recommends 10 ng or less), bring to 9.5 uL with water and add 1 uL of 10x reaction buffer.  If working with cells, transfer 10.5 ul of thawed lysate to new 0.2ml tube

* To each tube of RNA or cell lysate, add 2 uL of 3’ SMART-Seq CDS Primer II A

* Complete the 1st strand reaction by incubating the tubes at 72°C in a preheated, hot-lid thermal cycler for 3 minutes.

* Prepare 1x sorting buffer as you did on Day 1
	* 0.5 uL sort buffer per well x 96 wells = ~ 50 uL
	* 45.24 uL water + 4.75 uL 10x sorting buffer (90.5% water, 9.5% 10x sort buffer)



{% include links.html %}
