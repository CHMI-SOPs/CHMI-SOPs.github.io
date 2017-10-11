---
title: Illumina TruSeq Stranded total Sample Preparation Protocol
tags: [library construction]
keywords: transcriptomics, library preparation
summary: "Preparation of total transcriptome libraries for sequencing on an Illumina platform"
sidebar: mydoc_sidebar
permalink: mydoc_total_TruSeq.html
folder: mydoc
---
# Day 1


## Documentation

[TruSeq Stranded mRNA Sample Preparation Guide](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/samplepreps_truseq/truseqstrandedtotalrna/truseq-stranded-total-rna-sample-prep-guide-15031048-e.pdf). This method makes a cDNA library of the polyadenylated mRNA in your eukaryotic samples of interest.


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

{% include callout.html content="
- We use the Low Sample ‘LS’ protocol as we are typically working with fewer than 48 samples at a time  
- The recommended starting amount of total RNA is 100 ng - 1 ug, but we usually try to stay away from the extreme ends of this spectrum.  
- Split this protocol into two days, stopping on the first day after you have double stranded cDNA. On second day, do the A-tailing, adapter ligation, PCR, cleanup, and quality control steps.  
- For 12 samples, you will need approximately 6-7 hours on the first day, and 6-7 hours the second day.  
- Keep all reagents on ice unless otherwise stated.  
- We typically remove the reagents from storage during an incubation period in the previous step.  
- Have the beads at room temperature at least 30 minutes prior to use.  
- Aliquot the reagents that arrive in large quantities (such as the resuspension buffer and the bead washing buffer) into 2 mL Eppendorf tubes.  
- We do not perform any of the in-line controls.  
- We do not use the plate barcode stickers that come with the kit.  
- Use only filter pipette tips and clean your area so it is free of RNases.  
- Ensure that the AMPureXP beads are mixed well immediately prior to use.  
- There are many mixing steps in this protocol - I frequently use a multi-channel pipette to help speed up this process, particularly if many libraries are being prepared.  
- We use a Tapestation or a BioAnalyzer to assay the input RNA quality. Ribosomal integrity numbers of 7 and higher are preferred.  
- We quantify the input RNA using a Qubit fluorometer." type="primary" %}

## Step 1: Deplete rRNA

1. Dilute the RNA with RNase-free water to a final volume of 10 uL per sample.

2. Add 5 uL of rRNA binding buffer and 5 uL of rRNA removal mix to each well. Pipette up and down 6 times.

3. Seal the plate and place the plate in the thermocycler and run the "RNA DENATURATION PROGRAM" (68C for 5 min).

4. Remove the plate from the thermocycler and leave on the bench at room temperature for 1 minute. 

5. Vortex the rRNA removal beads (Illumina) and add 35 uL of beads to each well of a new plate.

{% include warning.html content="Don't skip this step by adding the beads to the sample in the old plate. Adding the sample to the beads will ensure optimal performance." %}

6. Remove the adhesive seal from the plate and add the sample (20 uL each) to the beads. Quickly pipette up and down 20 times to mix thoroughly.
7. Incubate at room temperature for 1 minute.
8. Place the plate on the magnetic stand for 1 minute.
9. Transfer the supernatant to a new plate.
10. Vortex the RNAClean XP beads to resuspend. Add 99 ul of beads directly to the ribo-depleted RNA samples from above. Mix gently by pipetting 10 times.

{% include note.html content="If your starting RNA sample is degraded, use 193 uL RNAClean XP beads." %}

11. incubate at RT for 15 min.
12. Place the plate on the magnetic stand at RT for 5 min.
13. Remove and discard the supernatant.
14. With the plate still on magnet, add 190 ul of fresh 70% EtOH to each well without disturbing the beads.

{% include warning.html content="The TruSeq manual indicates that 200 uL should be used, however, the maximum volume of our 96-well plates is 200 uL, thus we use less so the wells do not overflow." %}

15. Incubate EtOH wash for 30 sec, then discard the supernatant.
16. let the samples sit on the magnet for 15min to dry. Remove excess EtOH with a p10 pipette.
17. Remove the plate from the magnet, gently add 11 ul of Elution Buffer to each well. Mix thoroughly by pipetting up and down 10 times. You will have to work to get the dried beads off the side of the well and resuspended in the buffer.
18. Incubate the plate at RT for 2 minutes.
19. Place the sample on the magnet for 2 minutes.
20. Transfer 8.5 uL of the supernatant from each well to a new PCR plate.
21. Add 8.5 uL Elute, Prime, Fragment High mix to each well. Mix by pipetting up and down 10 times. 
22. Place the wells in the thermocyler and run the Elu2Frag program.

{% include note.html content="If your RNA is degraded, you may shorten the fragmentation time. See Appendix A in the Illumina TruSeq Total RNA Handbook." %}

{% include links.html %}
