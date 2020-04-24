---
title: Illumina Nextera XT Sample Preparation Protocol
tags: [library_prep, transcriptomics, microbiome, metagenomics]
keywords: metagenomics, transcriptomics, library preparation
summary: "Preparation of sequencing libraries from DNA or cDNA for sequencing on an Illumina platform"
sidebar: mydoc_sidebar
permalink: mydoc_NexteraXT.html
folder: mydoc
---

## Documentation

The full protocol can be found [here](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/samplepreps_nextera/nextera-xt/nextera-xt-library-prep-reference-guide-15031942-05.pdf)


## What you'll need

{% include important.html content="The following items are included in the Illumina kit" %}

* Tagment DNA buffer (TD) (Stored at -20C)
* Amplicon Tagmentation Mix (ATM) (-20C)
* Neutralization buffer (NT) (Room Temperature)
* Nextera PCR Mix (NPM) (-20C) 
* Nextera Indexes (i5 and i7) (-20C)
* Resuspension Buffer (RSB) (-20C)
* TruSeq Index Plate Fixture (Room Temperature)

{% include important.html content="The following items are NOT included with the Illumina kit and must be purchased separately" %}

* 80% Ethanol, made fresh the same day
* Magnetic stand
* AMPureXP beads (Beckman-Coulter)
* Illumina Index Replacement Caps 

## A few important comments before you start
* All work before the PCR step should be performed in the pre-PCR designated hood. 
* The i5 and i7 indexes come as Set A, B, C, or D. On the lid of the Nextera reagents in our -20C freezer, there are images of which primers belong to which set. Using indexes from one kit makes programming the run on Basespace before sequencing a lot easier. 

## Step 1: Quantify DNA

Quantify DNA with a Qubit and then dilute each sample to 0.2 ng/uL using ultra-pure, molecular-grade water.

{% include note.html content="I usually make at least 10 uL of each diluted DNA solution for use in the next step." %}


## Step 2: Tagment DNA:

* Add the following items in the order listed to each well of a new PCR plate. Pipette to mix:

* 10 uL Tagment DNA Buffer (TD)
* 5 uL Normalized gDNA 

* 5 μl Amplicon Tagment Mix (ATM)
* Pipette to mix. Seal the plate.  The total volume should be 20 uL per well.

* Centrifuge the plate at 280 × g at 20°C for 1 minute.

* Place on the preprogrammed thermal cycler and run the tagmentation program.

{% include note.html content="This program is in the NexteraXT folder on our thermocycler and is called 55_ATM and is 5 min at 55C followed by a hold at 10C.  Immediately after the 5 min, 55C step is complete, proceed immediately to the next step."%}

* Add 5 μl NT to each well. Pipette to mix.

* Centrifuge at 280 × g at 20°C for 1 minute.

* Incubate at room temperature for 5 minutes.


## Step 3: PCR

* Set up the indexes you will be using and arrange them in the TruSeq Index Plate Fixture (see manual for images).

* Using a multichannel pipette, add 5 μl of each Index 1 (i7) adapter down each column.

{% include important.html content="Throw away the cap once you have opened the index tube and replace with a new ORANGE cap." %}

* Using a multichannel pipette, add 5 μl of each Index 2 (i5) adapter across each row.

{% include important.html content="Throw away the cap once you have opened the index tube and replace with a new WHITE cap." %}

* Add 15 μl NPM to each well containing index adapters. Pipette to mix. The total volume is now 50 uL per well.

* Centrifuge at 280 × g at 20°C for 1 minute.

* Place on the preprogrammed thermal cycler and run the "NexteraPCR" program (bold denotes steps to be run for 12 cycles).

| Temp (C) | Time (min:sec) |
|-------|--------|
| 72 | 3:00 |
| 95 | 0:30 |
| **95** | **0:10** |
| **55** | **0:30** |
| **72** | **0:30** |
| 72 | 5:00 |
| 10 | hold |


{% include note.html content="This is a safe stopping point.  If you choose to stop here, seal the plate and store at 2°C to 8°C for up to 2 days. Alternatively, leave in the thermal cycler overnight" %}


## Step 4:  Cleanup

* Vortex AMPure XP beads before each use.  Vortex AMPure XP beads frequently to make sure that beads are evenly distributed.

* Add 30 μl AMPure XP beads to each well.

{% include important.html content="If your starting material is anything other than gDNA, consult the manual. Smaller input DNA lengths may require a different quantity of AMPureXP beads." %}

* Pipette to mix around 20 times to ensure the beads are mixed well with PCR products.

* Incubate at room temperature for 5 minutes.

* Place on a magnetic stand and wait until the liquid is clear (~2 minutes).

* Remove and discard all supernatant from each well.

* Wash 2 times as follows:
- Add 180 μl fresh 80% EtOH to each well.
- Incubate on the magnetic stand for 30 seconds.
- Remove and discard all supernatant from each well.

* Using a 20 μl pipette, remove residual 80% EtOH from each well.

* Air-dry on the magnetic stand for 15 minutes.

* Remove from the magnetic stand.

* Add 52.5 μl RSB to each well.

* Pipette to mix well.

* Incubate at room temperature for 2 minutes.

* Place on a magnetic stand and wait until the liquid is clear (~2 minutes).

* Transfer 50 μl supernatant to a new plate.

{% include note.html content="The standard Illumina protocol calls for a bead-based normalization step at this point. We typically skip this step and perform the Tapestation and Qubit for normalization calculations. You may decide to use either method." %}

{% include note.html content="This is a safe stopping point.  If you choose to stop here, seal the plate and store at -20°C for up to 7 days. Alternatively, leave in the thermal cycler overnight" %}


## Step 5: Quality Check

* Use the HS DNA5000 or HS DNA1000 tape and appropriate reagent buffer.  A successful library preparation will have a broad peak with an average size between 400-1000 bp.

* Quantify the sample with the HS DNA Qubit kit.

# Sequencing Guidelines

## Normalize and Pool

1. Quantify each of your libraries on Qubit. For most libraries, using the HS dsDNA Qubit assay with 2uL of input will yield a reading. Record the concentration in ng/uL for each library.

2. Run your samples on Tapestation with either the HSD5000 or the HSD1000 assay. Remember to allow Tapestation reagents to sit at room temperature for at least 30 minutes before use. Save your Tapestation results by going to File -> Create Report -> Save as pdf. This file can then be emailed or uploaded to Asana. For the base pair length, we usually use the value of the peak identified by the Tapestation analysis software. This value is shown both on the tracing itself and in the Peak Table for each sample. 

3. Download our nM Conversion Calculator [here](https://drive.google.com/file/d/1IOUsWLJIetkb6ZN4B-Bdfpx-IiRB1JQa/view?usp=sharing). Enter the concentration (from Qubit) and the base pair length (from Tapestation) in the appropriate cells and it will give you the nM concentration for each library. Normalize and pool all your libraries to 4, 2, 1, or 0.5 nM in a LoBind microcentrifuge tube. If you need to dilute your libraries, we recommend using at least 2uL to minimize pipetting errors. The example sheet of the calculator provides further detail.

4. Quantify your pool on Qubit and enter into the calculator sheet to check that your pool is close to the nM concentration you normalized to. 

## Setup Run in Basespace

1. Sign into Basespace, then go to the Prep tab, Biological Samples, and select Import Samples on the upper right. Use Illumina's Sample Import Template to enter information about your samples. The SampleID and Name can be the same, but make sure they are unique for each sample. Species can be left blank. Upload the completed .csv to import your samples.

2. Continue to Prep Libraries. Select your library prep kit based on the index format used. If you used our plate indexes select "IDT-ILMN Nextera UD Index Set A for Nextera XT". If you used tube indexes select "Nextera XT v2 Set A, B, C, or D." If you used another index format, you will need to use a different entry for library prep kit. The your project name as the Plate ID. For each sample, check the box next to it on the left, then drag the sample name to the appropriate index well.

3. Proceed to Pool Libraries. Select all your samples on the left, then drag and drop in the pool on the right. Name the pool your project name. 

4. Continue to Plan Run. Select NextSeq and name your run your project name. Select Single Read or Paired End Read, then enter the cycle numbers based on your selected kit. For example, if you were doing a run using a High Output 75 Cycle kit, you would select Single Read and enter 76 for Read 1 Cycles and 0 for Read 2 Cycles. 

5. Press Sequence to complete planning the run. The run will now be available for selection on the sequencer.

## Loading the Sequencer

The next step is to dilute and denature the prepared libraries. Illumina's general guidelines for this on the NextSeq can be found [here](https://support.illumina.com/content/dam/illumina-support/documents/documentation/system_documentation/nextseq/nextseq-500-550-denature-dilute-libraries-guide-15048776-15.pdf).

Illumina's system guide for the NextSeq, which covers the sequening workflow, can be found [here](https://support.illumina.com/content/dam/illumina-support/documents/documentation/system_documentation/nextseq/nextseq-500-system-guide-15046563-06.pdf). 

Your final loading concentration should be 1.5 - 1.8 pM, with most pools loaded at 1.6 or 1.7 pM.

{% include links.html %}
