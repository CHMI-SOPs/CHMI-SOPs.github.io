---
title: Illumina TruSeq Stranded mRNA Sample Preparation Protocol
tags: [library construction]
keywords: transcriptomics, library preparation
summary: "Preparation of mRNA libraries for sequencing on an Illumina platform"
sidebar: mydoc_sidebar
permalink: mydoc_TruSeq.html
folder: mydoc
---

# Day 1 (sorting)

## Documentation
[Clontech SMART V4 kit](http://www.clontech.com/US/Products/cDNA_Synthesis_and_Library_Construction/Next_Gen_Sequencing_Kits/Single_cell_RNA_Seq_Kits_for_mRNA_seq/ibcGetAttachment.jsp?cItemId=104008&fileId=7349924&sitex=10020:22372:US) for making cDNA, and the [Illumina NexteraXT kit](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/samplepreps_nextera/nextera-xt/nextera-xt-library-prep-reference-guide-15031942-02.pdf) for preparing a sequencing library from cDNA.

{% include important.html content="This protocol is for siuations when you sort less than 1000 cells per sample. If you are sorting many more cells/sample, you can sort direc" %}

## What you'll need for Day 1

{% include important.html content="The following items are included in the Clontech kit" %}

* RNA purification beads (These are the oligo dT beads) (bring these to room temperature before use)
* Bead washing buffer
* Bead binding buffer
* Fragment prime finish mix
* First strand synthesis (in a brown tube)
* Second strand marking mix
* Resuspension buffer

{% include important.html content="The following items are NOT included with the Illumina kit and must be purchased separately" %}

* RNase-free water
* Magnetic plate for a 96-well tray
* 96-well trays
* 80% ethanol (make this fresh the day of use)
* Superscript II (Invitrogen)
* AMPureXP beads (Beckman-Coulter)

## A few important comments before you start

{% include callout.html content="
- The biggest factor that determines how you process your sorted cells is number of cells you will sort.  type="primary" %}


## Step 1: Prepare reaction buffer and sort

1. Make 10X Reaction Buffer:
 * 19ul:1ul ratio of 10X Lysis and RNAse inhibitor (make 20ul per 18-20 samples)
 * 95ul 10X lysis+ 5ul RNAse Inhibitor

2. Make 1X Reaction buffer:
 * 9.5ul H2O + 1ul 10X reaction buffer/sample

3. For 88 +10% samples:
 * 920 H2O + 96.8ul 10X reaction buffer

4. Add 5ul buffer to each collection eppendorf and Sort into these tubes

5. After sort, add 5.5ul additional buffer and spin down.

6. freeze -80C 

# Day 2

## What you'll need for Day 2

{% include important.html content="The following items are included in the Clontech kit" %}

* Thaw 10x Lysis Buffer
* Thaw RNAse inhibitor
* Thaw 5X Ultra Low First Strand Buffer
* Thaw SMARTSeq4 Oligonucleotide
* Thaw 3’ SMART-Seq CDS Primer (both primers labeled IIA) on ice. 

Make additional 1X Reaction Buffer:
0.5ul x 96 wells = ~50ul.  
(90.5% H20, 9.5% 10x Reaction buffer  45.24ul H20 and 4.75ul 10X reaction buffer)

Transfer samples to a plate format:
-	Thaw samples on ice.
-	
- Distribute <5.9ul 1X Reaction buffer to each of an 8 well trip tube.  
- Pipette 0.5ul Reaction buffer to each well of a 96 well plate, kept in pre-chilled plate cooling block

(Preheat Thermalcycler to 72°)

-Transfer 10ul from each sample to 96 well plate (samples should have 10.5ul to start, leave 0.5 behind).  

(10.5ul)
*** If transferring to plate directly post-sort, start here:
OPEN and RT:
Viscosity required hand-pipetting each well rather than the bulk listed below:
(Distribute 108 ul 3’ SMART-Seq CDS Primer across strip tubes, 13ul / strip tube)

Add 1ul CDS primer to each well.  Seal, spin.  
(11.5ul)

Transfer to preheated 72deg Thermal cycler x 3 minutes  ice x 2 minutes. 
Preheat Thermal cycler to 42° with RT protocol




Make Master Mix  ( Make enough for 88 well + 10% overage) 

	O 4ul  5x ultra low buffer (387.2ul)
	O 1ul   SMART-Seq oligonucleotide (96.8ul)
	0.5ul  RNAse Inhibitor (48.4ul)
------------------------------------------
5.5ul   or 532.4ul

Just before use: 
O 2ul Add SMARTScribe RT  (193.6ul)
(pipette to mix gently and spin)
726ul

Dispense (86.4ul) per strip tube. 

Add 7.5ul RT MM to each sample.  
 (19ul)

Run RT script
42 x 90
70 x 10
4 hold
------------------- can be stopped overnight

AMPLIFY:
Thaw on ice:
O 2x SeqAmp PCR buffer
O PCR Primer II A

Make PCR MM:
30ul/sample + 10%

25ul SeqAmp PCR buffer (2.42mL)
O  1ul PCR (both primers labeled primer IIA) (96.8ul)
3ul PCR water (290.4ul)
Add last to MM just before pipetting into samples:
1ul SeqAmp DNA polymerase (96.8ul)
(remove directly from freezer, gently mix (no vortex)
---------------------
(2,904ul)

Dispense 344ul per 8 strip tube
Add 30ul PCR MM to each sample, Mix, spin. 
(49ul

Thermal cycler:
95 x 1 min
Cycle (18 cycles per the Hutch, Takara recommends 9-10):
	98 x 10sec
	65 x 30 sec
	68 x 3 min
72 x 10min
4 hold

------------------- can be stopped overnight
  
*Remainder on bench*


Bead purification


{% include important.html content="Congratulations! You're done!...well, almost" %}

{% include note.html content="Perform quality control steps - we use a Tapestation to determine the library size and qubit to quantify the libraries." %}

{% include note.html content="We recommend sequencing the libraries within 3 weeks." %}

{% include links.html %}
