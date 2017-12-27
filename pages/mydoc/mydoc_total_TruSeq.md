---
title: Illumina TruSeq Stranded total Sample Preparation Protocol
tags: [library_prep, transcriptomics]
keywords: transcriptomics, library preparation
summary: "Preparation of total transcriptome libraries for sequencing on an Illumina platform"
sidebar: mydoc_sidebar
permalink: mydoc_total_TruSeq.html
folder: mydoc
---
# Day 1


## Documentation

[TruSeq Stranded Total RNA Sample Prep Guide](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/samplepreps_truseq/truseqstrandedtotalrna/truseq-stranded-total-rna-sample-prep-guide-15031048-e.pdf). This method makes a cDNA library of all RNA molecules present in your sample after rRNA depletion.

{% include important.html content="the success of this kit is dependent on the ability of Illumina's rRNA depletion beads to bind rRNAs in your target species.  Check [this list](https://www.illumina.com/products/selection-tools/ribo-zero-kit-species-compatibility.html#hmr) for compatability of the mouse/rat/human rRNA 'riboGold' depletion reagent with other species." %}


## What you'll need for Day 1

{% include important.html content="The following items are included in the Illumina kit" %}

* RNA purification beads (These are the beads for rRNA depletion) (bring these to room temperature before use)
* rRNA removal mix
* rRNA binding buffer
* Elute, Prime, Fragment High mix
* First strand synthesis (in a brown tube)
* Second strand marking mix
* Resuspension buffer

{% include important.html content="The following items are NOT included with the Illumina kit and must be purchased separately" %}

* RNase-free water
* Magnetic plate for a 96-well tray
* 96-well trays
* 80% ethanol (make this fresh the day of use)
* 70% ethanol (make this fresh the day of use)
* Superscript II (Invitrogen)
* RNAClean XP beads (Beckman-Coulter) (bring these to room temperature before use)
* AMPureXP beads (Beckman-Coulter)

## A few important comments before you start

* We use the Low Sample ‘LS’ protocol as we are typically working with fewer than 48 samples at a time  
* The recommended starting amount of total RNA is 100 ng - 1 ug, but we usually try to stay away from the extreme ends of this spectrum.  
* Split this protocol into two days, stopping on the first day after you have double stranded cDNA. On second day, do the A-tailing, adapter ligation, PCR, cleanup, and quality control steps.  
* For 12 samples, you will need approximately 6-7 hours on the first day, and 6-7 hours the second day.  
* Keep all reagents on ice unless otherwise stated.  
* We typically remove the reagents from storage during an incubation period in the previous step.  
* Have the beads at room temperature at least 30 minutes prior to use.  
* Aliquot the reagents that arrive in large quantities (such as the resuspension buffer and the bead washing buffer) into 2 mL Eppendorf tubes.  
* We do not perform any of the in-line controls.  
* We do not use the plate barcode stickers that come with the kit.  
* Use only filter pipette tips and clean your area so it is free of RNases.  
* Ensure that the AMPureXP beads are mixed well immediately prior to use.  
* There are many mixing steps in this protocol - I frequently use a multi-channel pipette to help speed up this process, particularly if many libraries are being prepared.  
* We use a Tapestation or a BioAnalyzer to assay the input RNA quality. Ribosomal integrity numbers of 7 and higher are preferred.  
* We quantify the input RNA using a Qubit fluorometer.

## Step 1: Deplete rRNA

* Dilute the RNA with RNase-free water to a final volume of 10 uL per sample.

* Add 5 uL of rRNA binding buffer and 5 uL of rRNA removal mix to each well. Pipette up and down 6 times.

* Seal the plate and place the plate in the thermocycler and run the "RNA DENATURATION PROGRAM" (68C for 5 min).

* Remove the plate from the thermocycler and leave on the bench at room temperature for 1 minute. 

* Vortex the rRNA removal beads (Illumina) and add 35 uL of beads to each well of a new plate.

{% include warning.html content="Don't skip this step by adding the beads to the sample in the old plate. Adding the sample to the beads will ensure optimal performance." %}

* Remove the adhesive seal from the plate and add the sample (20 uL each) to the beads. Quickly pipette up and down 20 times to mix thoroughly.
* Incubate at room temperature for 1 minute.
* Place the plate on the magnetic stand for 1 minute.
* Transfer the supernatant to a new plate.
* Vortex the RNAClean XP beads to resuspend. Add 99 ul of beads directly to the ribo-depleted RNA samples from above. Mix gently by pipetting 10 times.

{% include note.html content="If your starting RNA sample is degraded, use 193 uL RNAClean XP beads." %}

* incubate at RT for 15 min.
* Place the plate on the magnetic stand at RT for 5 min.
* Remove and discard the supernatant.
* With the plate still on magnet, add 190 ul of fresh 70% EtOH to each well without disturbing the beads.

{% include warning.html content="The TruSeq manual indicates that 200 uL should be used, however, the maximum volume of our 96-well plates is 200 uL, thus we use less so the wells do not overflow." %}

* Incubate EtOH wash for 30 sec, then discard the supernatant.
* let the samples sit on the magnet for 15min to dry. Remove excess EtOH with a p10 pipette.
* Remove the plate from the magnet, gently add 11 ul of Elution Buffer to each well. Mix thoroughly by pipetting up and down 10 times. You will have to work to get the dried beads off the side of the well and resuspended in the buffer.
* Incubate the plate at RT for 2 minutes.
* Place the sample on the magnet for 2 minutes.

## Step 2: fragment RNA

This is a non-enzymatic and uses heat and divalent metal cations (magnesium or zinc) to fragment your RNA.  If your starting RNA was degraded, you can shorten the the length of time used in the Elu2Frag Program, or skip the fragmentation step altogether. 

* Transfer 8.5 uL of the supernatant from each well to a new PCR plate.
* Add 8.5 uL Elute, Prime, Fragment High mix to each well. Mix by pipetting up and down 10 times. 
* Place the wells in the thermocyler and run the Elu2Frag program.

{% include note.html content="If your RNA is degraded, you may shorten the fragmentation time. See Appendix A in the Illumina TruSeq Total RNA Handbook." %}

* Remove the plate once it reaches 4C, centrifuge briefly, and then proceed immediately through the next steps.

## Step 3: 1<sup>st</sup> strand cDNA synthesis

* Remove First Strand Synthesis Act D Mix from -20C and thaw at RT. Centrifuge this reagent at 600 x g for 5 sec.
* Add 50 ul SuperScript II to the First Strand Synthesis Act D Mix well. If you’re not going to use the entire well of mix, then add SuperScript at a ratio of 1 ul SuperScript for every 9 ul of First Strand reagent.  For example, for 12 reactions, mix 90 ul with 10 ul of SS II.  Excess mix can be stored in the -20C freezer.
* Add 8 ul of First Strand SuperScript mix to each well containing the mRNA.
* Place the plate in thermocycler and run the “Synthesize 1st Strand” program (25C for 10 min, 42C for 15 min, 70C for 15 min, hold at 4C).

{% include note.html content="This step takes 40 minutes and is your first large break." %}

## Step 4:  2<sup>nd</sup> strand cDNA synthesis

{% include important.html content="When the first strand synthesis is completed, immediately proceed to the second strand synthesis" %}

* Add 20 uL second strand marking mix and 5 uL resuspension buffer to each well. Pipette up and down 6 times.
* Centrifuge the plate at 600 x g for 30 sec.
* Place plate in thermocycler and run the ‘2nd strand’ reaction - 16C for 1hr, with the lid set to 30C.

{% include note.html content="This is your second large break of the day." %}

## Step 5: Reaction clean-up

* When the reaction is complete, add 90 ul of well-mixed AMPure XP beads to each well containing 50 ul of double stranded cDNA. Incubate RT for 15 min.
* Place the plate on the magnet and let sit for 5 min.
* Remove and discard 135 ul per well, being careful not to disturb the beads.
* Wash beads on magnet by adding 190 ul of 80% EtOH to each well, without disturbing the beads incubate 30 sec at RT.
* Remove and discard the supernatant, repeat the wash step and remove the supernatant again. Let the plate stand on the magnet at RT for 15 min to dry.

{% include important.html content="Use a p10 pipette to remove any residual ethanol from the bottom of the well." %}

* Add 17.5 ul of Resuspension Buffer to each well and pipette up and down 10 time to mix. Incubate for 2 min at RT.

{% include note.html content="The beads may be dry and you may have to pipette up and down more than 10 times until the beads are fully resuspended." %}

* Place the plate on the magnetic stand for 5 minutes.
* Transfer 15 ul of the supernatant (contains the ds cDNA) to new a new plate.

{% include note.html content="This is a safe-stopping place. You can cover the plate and store at -20C until you are ready to continue to the second day of the protocol." %}

{% include warning.html content="Do not store your DNA at this stage for longer than a week. We usually perform the rest of the protocol the next day." %}

# Day 2

## What you'll need for Day 2
{% include important.html content="The following items are included in the Illumina kit" %}

* A-tailing mix
* Resuspension buffer
* Ligation mix
* Index adapters
* Stop ligation buffer
* PCR primer cocktail
* PCR master mix

{% include important.html content="The following items are not included with the Illumina kit and must be purchased separately" %}

* Magnetic plate for a 96-well tray
* 96-well trays
* 80% Ethanol (make this fresh the day of use)
* AMPureXP beads (Beckman-Coulter)

## Step 6: Adenylate cDNA ends

* Add 12.5 ul of thawed A-tailing mix and 2.5 uL of resuspension buffer to each well. Pipette up and down 10 times.
* Carry out A-tailing by running the thermocycler ‘ATAIL70’ program.

{% include note.html content="This step takes 35 minutes and is the first large break of the day." %}

## Step 7: ligate adapters to ends

* Add 2.5 ul of resuspension buffer, 2.5 ul of ligation mix, and 2.5 ul of a unique RNA adapter index to each well, mix well by pipetting.

{% include note.html content="Remove the ligation mix immediately before use and return to -20C storage immediately after use." %}

{% include note.html content="I moved individual adapter index tubes to strip tubes to make it easier to add the unique indexes to the wells with a multichannel pipette." %}

{% include important.html content="Make sure to record which sample received which index adapter number." %}

* Seal the plate and incubate at 30C in thermocycler for 10 min using the 'LIGADAPTER' program.
* Remove the plate from the thermocycler and add 5 ul of stop ligation buffer to each reaction, mix well by pipetting.
* Add 42 ul of AMPure XP beads to each reaction, mix well by pipetting, and incubate at RT for 15 min.
* Place on magnetic stand for 5 min at RT.
* With the plate on the magnetic stand, remove 79.5 ul of supernatant from each sample, being careful not to disturb the beads.
* With the plate on the magnetic stand, wash with 190 ul 80% EtOH for 30 sec, then remove the ethanol.
* Perform the wash step again.
* Use a p10 pipette to remove residual ethanol. Leave the plate on the stand to dry for 15 minutes.
* Remove the plate from the magnetic stand and add 52.5 ul of Resuspension Buffer to each well, and mix well by pipetting. Incubate at RT for 2 min
* Place the plate on magnet for 5 min.
* Recover 50 ul from each well and transfer to a new plate.
* Carry out a second cleanup round. Add 50 uL of mixed AMPure beads to each well, mix well, incubate for 15 min at RT.
* Place the plate on the magnetic stand for 5 min.
* With the plate on the magnetic stand, remove and discard 95 ul of supernatant from each sample.
* With the plate on the magnetic stand, wash the beads with 190 ul of 80% EtOH for 30 s, then remove the ethanol.
* With the plate on the magnetic stand, wash the beads again with 190 uL of 80% EtOH for 30 s, then remove the ethanol.
* With the plate on the magnetic stand, use a p10 pipette to remove residual EtOH, then let the plate air dry for 15 min.
* Resuspend beads in 22.5 ul of resuspension Buffer, mix well by pipetting, and incubate 2 min at RT.
* Transfer the plate to the magnetic stand and incubate for 5 min.
* Recover 20 ul from each well and transfer to a new plate.

## Step 8: PCR amplify library

* Add 5 ul of PCR primer cocktail and 25 ul of PCR master mix to each well, place the plate in the thermocycler and run the “PCR” program.

{% include note.html content="This is another break for 30 minutes." %}

* Add 50 ul of AMPure beads to each well and mix well by pipetting. Incubate 15 min at RT.
* Place the plate on the magnet for 5 min.
* Remove and discard 95 ul of supernatant from each well.
* Wash the beads 190 ul/well of 80% EtOH, wait 30s, remove the supernatant.
* Repeat the ethanol wash step.
* Remove residual ethanol with a p10 pipette, let the beads air dry for 15 minutes on the magnetic plate.
* Remove the plate from the magnetic stand, add 32.5 ul of resuspension buffer and mix well, by pipetting, and incubate for 2 min at room temperature.
* Place the plate back on the magnetic stand for 5 minutes.
* Remove 30 uL of supernatant from each sample and move it into a new plate. This is the final cDNA product.

{% include important.html content="Congratulations! You're done!...well, almost" %}

{% include note.html content="Perform quality control steps - we use a Tapestation to determine the library size and qubit to quantify the libraries." %}

{% include note.html content="We recommend sequencing the libraries within 3 weeks." %}

{% include links.html %}




{% include links.html %}
