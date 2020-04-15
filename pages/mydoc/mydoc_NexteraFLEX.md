---
title: Illumina Nextera Flex Sample Preparation Protocol
tags: [library_prep, transcriptomics, microbiome, metagenomics, flex]
keywords: metagenomics, transcriptomics, library preparation
summary: "Preparation of sequencing libraries from DNA or cDNA for sequencing on an Illumina platform"
sidebar: mydoc_sidebar
permalink: mydoc_NexteraFLEX.html
folder: mydoc
---

## Documentation

This protocol has been adapted from Illumina's Nextera Flex Sample Preparation, of which the full protocol can be found [here](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/samplepreps_nextera/nextera-xt/nextera-xt-library-prep-reference-guide-15031942-05.pdf). It also includes instructions for a laboratory-made version called Hackflex, which reduces reagent use and cost. The paper describing Hackflex can be found [here](https://www.biorxiv.org/content/10.1101/779215v1.full.pdf). The protocols for these are similar, but diverge at multiple points.


## What you'll need

### Option 1: Standard Nextera Flex

* Bead-Linked Transposomes (BLT) (Stored at 4C)
* Tagmentation Buffer 1 (TB1) (-20C)
* Tagment Stop Buffer (TSB) (Room Temperature)
* Tagment Wash Buffer (TWB) (Room Temperature) 
* Enhanced PCR Mix (EPM) (-20C)
* Index Adaptors (tubes or plate) (-20C)
* Resuspension Buffer (RSB) (4C)
* Freshly prepared 80% ethanol 
* Nuclease Free Water
* Sample Purification Beads (4C)

### Option 2: Hackflex
* Bead-Linked Transposomes (BLT) (Stored at 4C)
* Lab-made Tagmentation Buffer (LTB) (-20C)
* Lab-made Tagment Stop Buffer (LTSB) (Room Temperature)
* Lab-made Tagment Wash Buffer (LTWB) (Room Temperature) 
* PrimeSTAR GXL DNA Polymerase kit (-20C)
* Index Adaptors (tubes or plate) (-20C)
* Resuspension Buffer (RSB) (4C)
* Freshly prepared 80% ethanol 
* Nuclease Free Water
* Ampure XP Beads (4C)

## Before You Start

* This kit can accommodate a wide range of input. If your total input is <100ng, you must quantify your input DNA on Qubit and normalize. In your input is 100-500ng, quantification and normalization is not required. You may use 2–30 µl DNA input for Standard Nextera Flex and 10 µl DNA input for Hackflex.

## Colony-Based DNA Extraction

* One input option for this kit is DNA from colony-based extraction. This uses some of the Flex reagents and is an easy way to go from a colony directly to library preparation. It is included in the protocol here, but any standard DNA extraction technique may be used. 

* This has been adapted from the Nextera DNA Flex Microbial Colony Extraction found [here] (https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/samplepreps_nextera/nextera_dna_flex/nextera-dna-flex-colony-extraction-protocol-1000000035294-01.pdf).

###Reagents and Equipment: 

* Sample Purification Beads (SPB) (Included with Nextera FLEX kit) or AMPure XP Beads

* PowerBead tubes, glass, 0.5mm (QIAGEN, catalog #13116-50)

* Disposable inoculation loop, 10μl (Fisher,catalog#12870155)

* 1.5mL microcentrifuge tubes

* Freshly made 80% ethanol

* Nuclease-free water 

* Magnetic Stand

* Vortex-Genie 2 with vortex adapter for 1.5mL tubes (24)

###Extraction
* Remove SPR or Ampure Beads from refrigerator and allow to stand for 30 minutes at room temperature. 

* Add 300ul of nuclease-free water to the PowerBead tubes containing 0.5mm glass beads.

* Using a 10 μl disposable inoculation loop, pick up to a half loopful of colonies from the bacterial culture plate. 

* Resuspend colonies in the PowerBead tube containing glass beads and nuclease-free water. 

* Fit a Vortex-Genie 2 with a vortex adapter. 

* Vortex at speed 6 for five minutes. 
	* For environmentally-resilient bacteria, vortex at max speed for 10 minutes

* Centrifuge at 20,000 × g for two minutes. Make sure that the glass beads are at the bottom of the PowerBead tube. 

* Transfer all supernatant (~150 μl) without the glass beads to a new 1.5 ml tube. 

* Transfer 50 μl of this supernatant to a new 1.5 ml tube.

{% include note.html content="The cultures we work with have very small colonies, and so we haven’t been able to test this protocol using entire half-loopfuls of bacteria. Because of the low input, we do not dilute the supernatant. However, the official protocol recommends transferring 20 μl of supernatant into a 1.5mL tube containing 30 μl of nuclease-free water. If an entire half-loopful of colonies was picked, you may have more success by diluting your supernatant." %}

* Vortex and invert beads several times to resuspend

* Add 20 μl beads to the 1.5 ml sample tube containing 50 μl supernatant. 

* Using a pipette set to 50 μl, mix ten times to thoroughly mix the beads and sample. 

* Incubate at room temperature for five minutes. 

* Place on the magnet until the beads have fully migrated to the side of the tube (~5 minutes). 

* Remove the supernatant without disrupting the bead pellet. 

* Make sure that a bead pellet is at the bottom of the tube before discarding the supernatant. 

* If the beads are accidentally aspirated: 
	* Return the sample to the tube and allow it to settle. 
	* Remove and discard the supernatant. 

* 	Wash two times as follows:
	* Add 200 μl fresh 80% EtOH to each tube. 
	* Incubate on the magnetic stand for 30 seconds. 
	* Remove and discard all supernatant from each tube. 

* Remove any residual EtOH using a P20 pipette. 

* Air-dry the tubes on the magnetic stand (~10 minutes). 

* Remove the tubes from the magnetic stand. 

* Resuspend beads in 32.5 μl of RSB. Pipette to mix. 

* Incubate at room temperature for 2 minutes. 

* Place on a magnetic stand and wait until the liquid is clear (~2 minutes). 

* Transfer 30 μl to a new 1.5 ml tube. 

We average ~10ng/ul of C. difficile using this protocol.

You can now proceed to the Tagment DNA Step for Standard Nextera Flex.
 

## Step 1: Tagment DNA

###Option 1: Standard Nextera Flex
* Allow BLT to equilibrate to room temp on the bench top for at least 30 minutes before use. Bring TB1 to room temp.

* Add 2–30 µl DNA to each well of a 96-well PCR plate so that the total input amount is 1–500 ng. If input is <100ng, quantify and normalize.

* If DNA volume < 30 µl, add nuclease-free water to the DNA samples to bring the total volume to 30 µl.

* Vortex BLT vigorously for to resuspend. Repeat as necessary.

* Prepare tagmentation master mix, per sample (overage is already included):

| Reagent | Volume (µl) |
|-------|--------|
| BLT | 11 |
| TB1 | 11 |

* Vortex the tagmentation master mix thoroughly to resuspend.

* Transfer 20 μl tagmentation master mix to each well of the plate containing a sample. If prepping a large number of samples, you may divide the mix volume equally into an 8-tube strip and use a multichannel pippette to transfer.

* Pipette each sample 10 times to resuspend.

* Seal the plate with Microseal 'B', place on the preprogrammed thermal cycler, and run the TAG
program.

### Option 2: Hackflex
* Allow BLT to equilibrate to room temp on the bench top for at least 30 minutes before use. Bring LTB to room temp.

* Add 2–10 µl DNA to each well of a 96-well PCR plate so that the total input amount is 10 ng. 

* If DNA volume < 10 µl, add nuclease-free water to the DNA samples to bring the total volume to 10 µl.

* Vortex BLT vigorously for to resuspend. Repeat as necessary.

* Prepare a 1:50 dilution of BLT in nuclease free water. You will need 11 uL of 1:50 diluted BLT per sample.

* Prepare tagmentation master mix, per sample (overage is already included):

| Reagent | Volume (µl) |
|-------|--------|
| 1:50 BLT | 11 |
| LTB | 27.5 |

* Vortex the tagmentation master mix thoroughly to resuspend.

* Transfer 35 μl tagmentation master mix to each well of the plate containing a sample. If prepping a large number of samples, you may divide the mix volume equally into an 8-tube strip and use a multichannel pippette to transfer.

* Pipette each sample 10 times to resuspend.

* Seal the plate with Microseal 'B', place on the preprogrammed thermal cycler, and run the TAG
program. Your total reaction volume will be 45μl.

## Step 2: Post-Tagmentation Cleanup

* Add 10 µl TSB (Hackflex: 10 µl LTSB) to the tagmentation reaction.

* Slowly pipette each well 10 times to resuspend the beads.

* Seal the plate with Microseal 'B', place on the preprogrammed thermal cycler, and run the PTC program.

* After removing from the thermocycler, place the plate on the magnetic stand and wait until liquid is clear (~3 minutes).

* Using a multichannel pipette, remove and discard supernatant.

* Remove the sample plate from the magnetic stand and very slowly add 100 µl TWB (Hackflex: 100uL LTWB) directly onto the beads, avoiding foaming.

* Pipette slowly until beads are fully resuspended.

* Place the plate on the magnetic stand and wait until the liquid is clear (~3 minutes).
*
* Using a multichannel pipette, remove and discard supernatant.

* Repeat this wash with TWB (Hackflex: 100uL LTWB).

* Remove the plate from the magnetic stand and use a slowly pipette to add 100 µl TWB (Hackflex: 100uL LTWB) directly onto the beads.

* Pipette each well slowly to resuspend the beads.

* Seal the plate and place on the magnetic stand until the liquid is clear (~3 minutes). Keep on the magnetic stand until the appropriate step in the next section. 


## Step 3: PCR

### Option 1: Standard Nextera Flex

* Prepare PCR master mix, per sample (overage is already included):

| Reagent | Volume (µl) |
|-------|--------|
| EPM | 22 |
| Nuclease-free water | 22 |

* Vortex, and then centrifuge the PCR master mix at 280 × g for 10 seconds.

* With the plate on the magnetic stand, use a 200 µl multichannel pipette to remove and discard supernatant.
Foam that remains on the well walls does not adversely affect the library.

* Remove from the magnet.

* Immediately add 40 µl PCR master mix directly onto the beads in each sample well.

* Immediately pipette to mix until the beads are fully resuspended. Alternatively, seal the plate and use a
plate shaker at 1600 rpm for 1 minute.

* Seal the sample plate and centrifuge at 280 × g for 3 seconds.

* Add the appropriate index adapters to each sample.

Plate index adapters: Add 10uL pre-paired adapter by piercing into the foil.
Tube index adapters: Add 5uL each of one i7 and one i5 adapter.

* Using a pipette set to 40 µl, pipette 10 times to mix. Alternatively, seal the plate and use a plate shaker at
1600 rpm for 1 minute.

* Seal the plate with Microseal 'B', and then centrifuge at 280 × g for 30 seconds. Place on the thermal cycler and run the BLT PCR program. Your reaction volume is 50uL.

### Option 2: Hackflex

* Prepare PrimeStar PCR master mix, per sample (overage is already included):

| Reagent | Volume (µl) |
|-------|--------|
| 5x GXL Buffer | 11 |
| 25mM dNTPs | 4.4 |
| PrimeStar GXL polymerse | 2.2 |
| Nuclease-free water | 20.9 |

* Vortex, and then centrifuge the PCR master mix at 280 × g for 10 seconds.

* With the plate on the magnetic stand, use a 200 µl multichannel pipette to remove and discard supernatant.
Foam that remains on the well walls does not adversely affect the library.

* Remove from the magnet.

* Immediately add 35 µl PrimeStar PCR master mix directly onto the beads in each sample well.

* Immediately pipette to mix until the beads are fully resuspended. Alternatively, seal the plate and use a
plate shaker at 1600 rpm for 1 minute.

* Seal the sample plate and centrifuge at 280 × g for 3 seconds.

* Add the appropriate index adapters to each sample.

Plate index adapters: Add 10uL pre-paired adapter by piercing into the foil.
Tube index adapters: Add 5uL each of one i7 and one i5 adapter.

* Using a pipette set to 35 µl, pipette 10 times to mix. Alternatively, seal the plate and use a plate shaker at
1600 rpm for 1 minute.

* Seal the plate with Microseal 'B', and then centrifuge at 280 × g for 30 seconds. Place on the thermal cycler and run the BLT PCR program. Your reaction volume is 45uL.

### PCR program

| Temp (C) | Time (min:sec) |
|-------|--------|
| 68 | 3:00 |
| 98 | 3:00 |
| **98** | **0:45** |
| **62** | **0:30** |
| **68** | **2:00** |
| 68 | 1:00 |
| 10 | hold |

* The bolded steps will be repeated for the appropriate number of cycles according to the following chart. 
* If doing Hackflex with 10ng of input, 12 cycles is recommended.

| Total DNA Input (ng) | Number of PCR Cycles |
|-------|--------|
| 1-9 | 12 |
| 10-24 | 8 |
| 25-49 | 6 |
| 50-99 | 5 |
| 100-500 | 5 |

{% include note.html content="This is a safe stopping point.  If you choose to stop here, seal the plate and store at 2°C to 8°C for up to 3 days. Alternatively, leave in the thermal cycler overnight" %}


## Step 4:  Library Cleanup

* Allow Sample Purification Beads or Ampure XP Beads to equilibrate to room temperature on the bench for at least 30 minutes before use.

* Vortex beads before each use and frequently during use to make sure that beads are evenly distributed.

* Centrifuge at 280 × g for 1 minute to collect contents at the bottom of the well.

* Place the plate on the magnetic stand and wait until the liquid is clear (~5 minutes).

* Transfer 45 µl supernatant from each well of the PCR plate to the corresponding well of a new plate.

* Due to Hackflex's lower PCR reaction volume, you may get slightly less supernatant here and in the proceeding steps. As long as you are not greater than 5µl off the given volumes, continue with the protocol as written.

* Add 40 µl nuclease-free water to each well containing supernatant.

* Add 45 µl beads to each well containing supernatant.

* Pipette each well 10 times to mix. Alternatively, seal the plate and use a plate shaker at 1600 rpm for
1 minute.

* Seal the plate and incubate at room temperature for 5 minutes.

* Place on the magnetic stand and wait until the liquid is clear (~5 minutes).

* During incubation, thoroughly vortex the beads, and then add 15 µl to each well of a new plate.

* Transfer 125 µl supernatant from each well of the first plate into the corresponding well of the second plate (containing 15 µl beads).

* Pipette each well in the second plate 10 times to mix. Alternatively, seal the plate and use a plate
shaker at 1600 rpm for 1 minute.

* Discard the first plate.

{% include important.html content="If your starting material is anything other than gDNA, consult the manual. Smaller input DNA lengths may require a different quantity of beads." %}

* Incubate at room temperature for 5 minutes.

* Place on a magnetic stand and wait until the liquid is clear (~5 minutes).

* Remove and discard all supernatant from each well without disturbing the beads.

* Wash 2 times as follows:
- Add 190 μl fresh 80% EtOH to each well.
- Incubate on the magnetic stand for 30 seconds.
- Remove and discard all supernatant from each well.

* Using a 20 μl pipette, remove residual 80% EtOH from each well.

* Air-dry on the magnetic stand for 5 minutes.

* Remove from the magnetic stand.

* Add 32 μl RSB to each well.

* Pipette to resuspend.

* Incubate at room temperature for 2 minutes.

* Place on a magnetic stand and wait until the liquid is clear (~2 minutes).

* Transfer 30 μl supernatant to a new plate.

{% include note.html content="This is a safe stopping point.  If you choose to stop here, seal the plate and store at -20°C for up to 7 days. Alternatively, leave in the thermal cycler overnight" %}

## Step 5: Quality Check

* Libraries with DNA Inputs of 100-500ng generated in the same experiments do not require quantification individually. These can be pooled in a microcentrifuge tube. Add 5ul of each library (up to 384), vortex to mix, and centrifuge briefly before quanitifying the pool.

* Libraries with DNA Inputs of <100ng require individual quantification.

* Use the HS DNA5000 or HS DNA1000 tape and appropriate reagent buffer. A successful library preparation will have a broad peak with an average size between 400-1000 bp.

* Quantify the sample with the HS DNA Qubit kit.



{% include links.html %}
