---
title: SMARTer Stranded Total RNA-Seq Kit v2- Pico Input Mammalian 
tags: [library_prep, transcriptomics]
keywords: transcriptomics, library preparation
summary: "This protocol walks you through preparing a total transcriptome RNA library for RNAseq when your starting amount of RNA is less than ~50ng or if you are working with degraded/FFPE RNA samples"
sidebar: mydoc_sidebar
permalink: mydoc_FFPE_RNAseq.html
folder: mydoc
---

## Documentation
[Clontech Pico v2 kit](https://www.takarabio.com/products/next-generation-sequencing/rna-sequencing/pico-input-strand-specific-total-rna-seq-for-illumina?utm_source=marketo&utm_medium=email&utm_campaign=SG_SMARTer_Pico_Tech_Note&utm_content=prodpg&mkt_tok=3RkMMJWWfF9wsRogv6rOZKXonjHpfsX%2b4u8uT%2frn28M3109ad%2brmPBy%2b2YUGT9Q%2fcOedCQkZHblFnVoLTq2sVbYNr6wM).  This  uses random hexamer priming, rather than polyT, to make cDNA.  This means that it works very well when your starting material is highly degraded (e.g. fixed cells or tissues).  The random priming also means that this kit amplifies cDNA from *all* transcripts, including highly abundant RNA molecules such as rRNAs.  We tend to use this kit if 1) investigators are working with highly degraded starting material, particularly FFPE tissues, or 2) if they really prefer to study total transcriptomes, rather than mRNAs.

The protocol below uses the SMARTer Stranded Total RNA-Seq Kit, however another option for cDNA generation when starting with low-input is the [Clontech 'SMART Seq HT' for High-throughput single-cell mRNA-seq](http://www.clontech.com/US/Products/cDNA_Synthesis_and_Library_Construction/Next_Gen_Sequencing_Kits/Single_cell_RNA_Seq_Kits_for_mRNA_seq/High-throughput_single-cell_mRNA-seq?sitex=10020:22372:US). This is an excellent kit for preparing cDNA very low amounts of RNA (as little as 1-100 cells).  This kit is analgous to the well-known Clontech SMART-v4 kit, but is a faster/abbreviated workflow which combines RT/PCR steps and is roughly 30% lower cost compared to SMART-V4.  

## What you'll need

{% include important.html content="The following items are included in the Clontech SMART-Seq HT kit and are stored at -20C" %}
* ZapR v2
* RNase inhibitor (40U/ul)
* SeqAmp DNA Polymerase
* SeqAmp CB PCR Buffer (2x)
* SMART-Seq HT Oligonucleotide
* SMART Pico Oligos Mix v2 
* 5x First-strand Buffer
* Nuclease-Free Water
* SMARTScribe RT (100 U/uL)
* ZapR Buffer (10X)
* Tris Buffer (5mM)
* PCR2 Primers v2

{% include important.html content="The following items are included in the Clontech SMART-Seq HT kit and are stored at -80C" %}
* SMART TSO Mix v2
* R-probes v2
* Control Total RNA (1 ug/uL)

Not included in kit:
* [Eppendorf LoBind DNA tubes](https://online-shop.eppendorf.us/US-en/Laboratory-Consumables-44512/Tubes-44515/DNA-LoBind-Tubes-PF-56252.html)
* AMPure XP Beads (4C)

## A few important comments before you start
Input RNA Quality and Quantity:
* Purified total RNA samples cannot be resuspended in TE Buffer or have any EDTA in them. They should be resuspended in nuclease-free water. Any EDTA will interfere with RNA fragmentation and will decrease the efficiency of the reverse transcription.
* Samples must be DNAse I treated.
* If working with high quality RNA (RIN score >4), follow Option 1 which includes fragmentation; the fragmentation time will vary depending in the RIN score.
* If working with FFPE samples or highly degraded RNA, follow Option 2 which does not include fragmentation.


{% include important.html content="Always use a positive and a negative control. There is Control Total RNA included with this kit and stored in our -80C freezer in box J8. Dilute the stock or use one of the dilutions in this box to match your input of RNA samples for your positive control. Use nuclease-free water for your negative control." %}

{% include warning.html content="R-probes v2 cannot be freeze/thawed more than 3 times. These are also aliquoted in our -80C in box J8." %}

{% include important.html content="Add all enzymes to reaction mixtures last and thoroughly pipette up and down to mix these master-mixes." %}

## Diluting Control RNA
* To 50 ng/uL
	38 uL nuclease-free water
  + 2 uL control RNA

* To 5 ng/uL 
	45 uL nuclease-free water
  + 5 uL diluted Control RNA at 50 ng/uL

 * To 0.25 ng/uL
 	95 uL nuclease-free water
  + 5 uL diluted Control RNA at 5 ng/uL

## Option 1: With Fragmentation (RIN > 4)
1. Mix the following on ice: 
Reagent      | Volume per rxn (uL)
-----------------|---------------------
RNA [5-50 ng input]| 1-8 uL
Nuclease-free water | 0-7 uL
SMART Pico Oligos Mix v2 | 1 uL 
5x First-Strand Buffer | 4 uL
*Total Volume | 13 uL*

2. Incubate tubes at 94C in preheated, hot-lid thermal cycler for the amount of time recommended below:

| RIN Score of Input RNA | Minutes to Fragment  |
|-----------------------------------------|------------------------------|
| RIN >7               | 4 minutes |
| RIN 5-6             | 3 minutes |
| RIN 4               | 2 minutes |

3. Immediately place samples on ice for 2 minutes. 

4. Prepare enough First-Strand Master Mix for all reactions plus 10% by combining the following on ice: 

Kit reagent | Volume per rxn (uL)
-----------------------------|---------------------
SMART TSO Mix v2 (very viscous, mix well) | 4.5
RNase Inhibitor | 0.5
SMARTScribe Reverse Transcriptase | 2.0
*Total Volume per reaction | 7.0*

5. Add 7 uL of the First Strand Master Mix to each PCR strip tube, vortex for about 2 seconds, spin down briefly.

6. Incubate the tubes in a preheated hot-lid thermal cycler with the following program (OPT1_FRAG):

| Temp (C) | Time (min:sec) |
|----------|----------------|
| 42       | 90:00          |
| 70C      | 10:00          |
| 4        | hold           |


7. Leave the samples in the thermal cycler at 4C until the next step
{% include important.html content="Safe stopping point. Leave the samples overnight in the thermal cycler at 4C or store the cDNA in the -20C freezer for up to 2 weeks." %}

## Option 2: Without Fragmentation (RIN< 4 or FFPE Samples)
1. Mix the following on ice: 

Reagent      | Volume per rxn (uL)
-----------------|---------------------
RNA [5-50 ng input]| 1-8 uL
Nuclease-free water | 0-7 uL
SMART Pico Oligos Mix v2 | 1 uL 
*Total Volume | 9 uL*

2 Incubate tubes at 72C preheated, hot-lid thermal cycler for exactly 3 minutes.

3. Immediately place samples on ice for 2 minutes. 

4. Prepare enough First-Strand Master Mix for all reactions plus 10% by combining the following on ice: 

Kit reagent | Volume per rxn (uL)
-----------------------------|---------------------
SMART TSO Mix v2 (very viscous, mix well) | 4.5
RNase Inhibitor | 0.5
SMARTScribe Reverse Transcriptase | 2.0
5x First-Strand Buffer | 4.0
*Total Volume per reaction | 11.0*

5. Add 11 uL of the First Strand Master Mix to each PCR strip tube, vortex for about 2 seconds, spin down briefly.

6. Incubate the tubes in a preheated hot-lid thermal cycler with the following program ():
| Temp (C) | Time (min:sec) |
|----------|----------------|
| 42       | 90:00          |
| 70C      | 10:00          |
| 4        | hold           |

7. Leave the samples in the thermal cycler at 4C until the next step
{% include important.html content="Safe stopping point. Leave the samples overnight in the thermal cycler at 4C or store the cDNA in the -20C freezer for up to 2 weeks." %}

## PCR1- Addition of Illumina Adapters and Indexes
Important: If Purification of RNA-seq Library using AMPure Beads will be performed the same day, take aliquots of beads out of 4C to allow them to reach room temperature

1. Prepare enough PCR1 Master Mix for all reactions plus 10% by combining the following reagents in the order shown below, vortex, then spin down:

Kit reagent | Volume per rxn (uL)
-----------------------------|---------------------
Nuclease-free water | 2
SeqAmp CB PCR Buffer 2X  | 25
SeqAmp DNA Polymerase | 1
*Total Volume per reaction | 28*
					  
2. Add 28 uL of PCR Master Mix to each sample 

3. Add 1 uL of each 5' PCR Primer HT to each sample

4. Add 1 uL of each 3' PCR Primer HT to each sample 

5. Tap PCR strip tubes to mix and spin down briefly

6. Place tubes on preheated hot-lid thermal cycler for the following program: (**bold** denotes steps to be run for 5 cycles)

| Temp (C) | Time (min:sec) |
|----------|----------------|
| 94       | 1:00           |
| **98**   | **0:15**       |
| **55**   | **0:15**       |
| **68**   | **0:30**       |
| 62       | 2:00           |
| 4        | hold           |

{% include important.html content="Safe stopping point. Leave the samples overnight in the thermal cycler at 4C or store the cDNA in the -20C freezer for up to 2 weeks." %}

## Purification of RNA-seq Library using AMPure Beads
{% include important.html content="Do not start this section unless you have enough time to perform all steps up to PCR2: Final Library Amplification; there are no safe stopping points until then." %}

{% include important.html content="Remove ZapR Buffer from -20C storage and thaw at room temperature in preparation for next section. " %}

1. Allow AMPure XP beads to come to room temperature for about 30 minutes before use. Vortex beads for 2 minutes to mix well. Make sure samples are in a 96 well plate that will fit on our magnetic stand. Prepare fresh 80% ethanol, you will about 400 uL per sample. 

2. Add 40 uL of AMPure beads to each sample and pipette 10 times to mix. 

3. Incubate at room temperature for 8 minutes to allow the DNA to bind to the beads. 

4. Place plate on magnetic stand for 5 minutes or longer until the solution is completely clear. 

5. While samples are on magnetic stand, remove and discard supernatant. Do not disrupt beads. 

6. Keeping samples on magnetic stand, add 180 uL of freshly made 80% ethanol to each sample without disturbing beads. Wait 30 seconds and carefully pipette out and discard supernatant. cDNA will remain bound to beads during the washing process. 

7. Repeat wash step above 1 more time. 

8. Let samples air dry for about 1 minute on magnetic stand then remove any excess ethanol with a P20. 

9. Air dry samples on magnetic stand for 3-5 minutes at room temperature until pellets appear dry and matte. Once you start to see pellets crack, take off magnetic stand to ensure you do not overdry your samples. 

10. Once beads are dry, remove from magentic stand and add 52 uL of Nuclease- free water to cover beads, pipette to mix thoroughly until the beads are resuspended. 

11. Incubate at room temperature for 5 minutes. 

12. Place plate back on magnetic stand for 1 minute or longer until the supernatant is clear. 

13. Pipette 50 uL of supernatant to new plate

14. Add 40 uL of vortexed AMPure XP beads to each sample and pipette to mix thoroughly 10 times. 

15. Incubate at room temperature for 8 minutes to allow DNA to bind to the beads. During incubation, proceed to next section. 

## Depletion of Ribosomal cDNA with ZapR v2 and R-Probes v2
In this section, the library fragments originating from rRNA (18S and 28S) and mitochondrial rRNA (m12S and m16S) are cut by ZapR v2 in the presence of R-Probes v2 (mammalian-specific). These R-probes hybridize to ribosomal RNA and mitochondrial rRNA sequences.

* Must make fresh aliquot of 80% ethanol if doing on different day than previous section, you will need 400 uL per sample. 

1. Thaw R-probes v2 (-80C, Box J8) and ZapR Buffer (-20C) at room temperature. Once R-probes v2 thaw, place immediately on ice but keep ZapR Buffer at room temperature. Thaw ZapR v2 (-20C) on ice and keep on ice at all times, return to freezer immediately after use. 

2. Preheat PCR machine to 72C

3. Once 8 minute incubation of samples and AMPure XP beads is finished, place samples on magnetic stand for 5 minutes or longer until the solution is completely clear.

4. During the 5 minute incubation, pipette 1.5 uL of R-Probes v2 +10% per reaction into a PCR Strip tube on ice and immediately return R-Probes v2 to -80C freezer. 

5. Incubate the PCR strip tube of R-probes v2 at 72C in preheated hot-lid thermal cycler using the following program: 
| Temp (C) | Time (min:sec) |
|----------|----------------|
| 72       | 2:00           |
| 4   | hold      |
					  
6. The PCR strip tube of R-probes should be held at 4C for anywhere between 2-10 minutes. It must be held for at least 2 minutes but not for more than 15 minutes. 

7. Once the 5 minute incubation of RNA samples is finished on magnetic stand, pipette and discard clear supernatant without disturbing the beads. 

8. Keeping the samples on the magnetic stand, add 180 uL of freshly made 80% ethanol to each sample without disturbing beads. Wait 30 seconds and carefully pipette out and discard supernatant. cDNA will remain bound to beads during the washing process. 

9. Repeat wash step above 1 more time. 

10. Let samples air dry for about 1 minute on magnetic stand then remove any excess ethanol with a P20.

11.  Air dry samples on magnetic stand for 1-2 minutes at room temperature until pellets appear dry and matte. Once you start to see pellets crack, take off magnetic stand to ensure you do not overdry your samples. 

12. While beads are drying, prepare the ZapR Master Mix for all reactions plus 10% by combining the following reagents in the order shown below at room temperature, vortex, then spin down:

Kit reagent | Volume per rxn (uL)
-----------------------|---------------------
Nuclease-free water | 16.8
10X ZapR Buffer  | 2.2
ZapR v2 | 1.5
R-Probes v2, heated | 1.5
*Total Volume per reaction | 28*

13. Take plate off magnetic stand. To each well of dried AMPure XP beads, add 22 uL of ZapR Master Mix and pipette to mix thoroughly until the beads are resuspended. 

14. Incubate at room temperature for 5 minutes.

15. Place plate back on magnetic stand for 1 minute or longer until the supernatant is clear. 

16. Pipette out 20 uL of clear supernatant, without disturbing beads, to a new PCR strip tube. 

17. Incubate PCR strip tubes containing supernatant in a preheated hot-lid thermal cycler using the following program: 
| Temp (C) | Time (min:sec) |
|----------|----------------|
| 37       | 60:00          |
| 72C      | 10:00          |
| 4        | hold           |

* Samples can be held at 4C for up to 1 hour but it is recommended that you proceed immediately to next section. 

## PCR2- Final RNA-Seq Library Amplification 
In this section, the library fragments not cleaved by the ZapR reaction will be further enriched in a second round of PCR. Illumina barcodes have already been added to the libraries so this step includes a single pair of primers that are used for all libraries. 

1. Prepare a PCR2 Master Mix for all reactions plus 10% by combining the ollowing reagents in the order shown below, vortex, then spin down:
Kit reagent | Volume per rxn (uL)
-----------------------|---------------------
Nuclease-free water | 26
SeqAmp CB PCR Buffer  | 50
PCR2 Primers v2 | 2.0
SeqAmp DNA Polymerase | 2.0
*Total Volume per reaction | 80*

2. Add 80 uL of PCR2 Master Mix to each tube. Mix by tapping gently and spin down.

% Important: our thermal cycler only holds 50uL so after adding the master mix, vortexing and spinning down, split each sample into two separate PCR strip tubes with 50 uL in each one. 

3. Place tubes in preheated hot-lid thermal cycler for the following program: PCR2:
94C 1 min
	9-16 cycles of:
	98C 15 sec
	55C 15 sec
	68C 30 sec
4C forever

%note: The number of PCR cycles corresponds to the starting material. Do not perform more than 16 cycles as it can lead to amplification of background material. Use the following table below to choose appropriate cycles
Amount of Input RNA (ng) Number PCR Cycles, Regular RNA Number PCR Cycles, FFPE RNA
50	9-10	13
10	12		15-16
1	14-15	16
0.5	16		-

%important Safe stopping point, samples can be left overnight at 4C. If not processed within the next day, freeze the PCR prodcuts at -20C for up to 2 weeks. 

## Purificationo of Final RNA-Seq Library Using AMPure Beads 

% Important: move samples to a 96 well plate before beginning this step. We do not have a magnetic stand that holds PCR strip tubes. 

1. Allow AMPure XP beads to come to room temperature for about 30 minutes before use. Vortex beads for 2 minutes to mix well. Make sure samples are in a 96 well plate that will fit on our magnetic stand. Prepare fresh 80% ethanol, you will about 400 uL per sample. 

2. Add 100 uL of AMPure beads to each sample and pipette 10 times to mix. [This is a 1:1 ratio; if you kept each sample separated into 2 wells, add 50 uL of beads. If all 100uL of PCR product is one a single well, add 100uL of beads very carefully because this will completely fill the wells.]

3. Incubate at room temperature for 8 minutes to allow the DNA to bind to the beads. 

4. Place plate on magnetic stand for 5 minutes or longer until the solution is completely clear. 

5. While samples are on magnetic stand, remove and discard supernatant. Do not disrupt beads. 

6. Keeping samples on magnetic stand, add 180 uL of freshly made 80% ethanol to each sample without disturbing beads. Wait 30 seconds and carefully pipette out and discard supernatant. cDNA will remain bound to beads during the washing process. 

7. Repeat wash step above 1 more time. 

8. Let samples air dry for about 1 minute on magnetic stand then remove any excess ethanol with a P20. 

9. Air dry samples on magnetic stand for 3-5 minutes at room temperature until pellets appear dry and matte. Once you start to see pellets crack, take off magnetic stand to ensure you do not overdry your samples. 

10. Once beads are dry, remove from magentic stand and add 20 uL of **Tris Buffer** to cover beads, pipette to mix thoroughly until the beads are resuspended. 

11. Incubate at room temperature for 5 minutes. 

12. Place plate back on magnetic stand for 1 minute or longer until the supernatant is clear. 

13. Pipette 18 uL of supernatant to LoBind Tubes. This is the final product. 

## Quality Check of Final Product

1. Run samples on HSD1000 Tapestation Assay.

2. Measure concentration with HS dsDNA Qubit assay.
