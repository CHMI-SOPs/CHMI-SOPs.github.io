---
title: Illumina TruSeq Stranded mRNA Sample Preparation Protocol
tags: [library_prep, transcriptomics]
keywords: transcriptomics, library preparation
summary: "Preparation of mRNA libraries for sequencing on an Illumina platform"
sidebar: mydoc_sidebar
permalink: mydoc_TruSeq.html
folder: mydoc
---

# Day 1

## Documentation
[TruSeq Stranded mRNA Sample Prep Guide](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/samplepreps_truseq/truseq-stranded-mrna-workflow/truseq-stranded-mrna-workflow-reference-1000000040498-00.pdf). This method makes a cDNA library of the polyadenylated mRNA in your eukaryotic samples of interest.

## What you'll need for Day 1

{% include important.html content="The following items are included in the Illumina kit.  We recommend kits be stored as received in the original manufacterer's boxes and not unpacked to organize in a reagent box.  When kits go bad, it is much easier to contain the damage if reagents were stored as received." %}

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
* We use the Low Sample ‘LS’ protocol as we are typically working with fewer than 48 samples at a time  
- The recommended starting amount of total RNA is 100 ng - 4 ug, but we usually try to stay away from the extreme ends of this spectrum.  
- The lowest input of RNA we have successfully used in this protocol is 70 ng.  
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


## Step 1: Isolate mRNA

1. Dilute total RNA in RNase-free water to final volume of 50 ul. Do this in a 96-well PCR plate (even if you have a few samples).

2. Add 50 uL RNA purification beads to each well. Gently pipette up and down 6 times. Seal the plate with an adhesive seal.

{% include warning.html content="Do not store mRNA purification beads on ice!  We have observed that the beads are very sensitive to cold temperatures.  Beads stored at < 2degC may deteriorate, resulting in poor binding of mRNA, and therefore poor library prep that is heavily contaminated with excess adapter." %}

3. Place the sealed plate in the thermal cycler. Select the mRNA denaturation program (65C for 5 min, 4C hold).

4. Remove the plate when it reaches 4C and incubate the plate at room temperature for 5 minutes.

5. Remove the adhesive seal and place the plate on the magnetic stand at room temperature for 5 minutes

6. Remove and discard the supernatant from each well of the plate

7. Remove the plate from the magnetic stand and wash the beads by adding 190 uL bead washing buffer in each well. Gently pipette up and down 6 times.

{% include warning.html content="The TruSeq manual indicates that 200 uL should be used, however, the maximum volume of our 96-well plates is 200 uL, thus we use less so the wells do not overflow." %}

8. Place the plate on the magnetic stand at room temperature for 5 minutes

9. Remove and discard the supernatant from each well.

10. Remove the plate from the magnetic stand.

11. Add 50 uL Elution Buffer to each well and gently pipette up and down 6 times. Seal the plate with an adhesive seal.

12. Place the plate in the thermal cycler. Choose the program “mRNA elute” (80C for 2 min, 25 C hold).

13. Remove the plate when the thermal cycler reaches 25C. Place the plate on the bench at room temperature and remove the seal.

14. Add 50 uL Bead Binding Buffer to each well. Gently pipette up and down 6 times. Incubate the plate at room temperature for 5 minutes.

15. Place the plate on the magnetic stand at room. Incubate the plate at room temperature for 5 minutes. Remove and discard the supernatant from each well.

16. Wash the beads by adding 190 uL bead washing buffer. Gently pipette up and down 6 times to mix.

17. Place the plate on the magnetic stand at room temp for 5 min. Remove and discard the supernatant from each well.

18. Remove the plate from the magnetic stand and add 19.5 uL Fragment, Prime, Finish Mix to each well. Gently pipette up and down 6 times to mix.

19. Seal the plate with an adhesive film. Place the sealed plate on the thermal cycler. Select the Elute2Frag program (94C for 8 min, 4C hold).

{% include tip.html content="For degraded mRNA or mRNA isolated from FFPE samples, you may shorten the fragmentation time. See the Illumina TruSeq instruction manual for suggested times." %}

* If RNA is degraded and you do not want to Fragment, place samples on thermal cycler at 65C for 5 mins, 4C hold. This will elute the mRNA from the beads without degrading the RNA. 

20. Remove the plate once it reaches 4C, centrifuge briefly, and then proceed immediately through the next steps.

21. Remove the adhesive seal and place the plate on a magnetic stand at room temperature for 5 min.

22. Remove 17 uL supernatant from each well into corresponding wells in a new plate. This contains your purified mRNA.

## Step 2: 1<sup>st</sup> strand cDNA synthesis

23. Remove First Strand Synthesis Act D Mix from -20C and thaw at RT. Centrifuge this reagent at 600 x g for 5 sec.

24. Add 50 ul SuperScript II to the First Strand Synthesis Act D Mix well. If you’re not going to use the entire well of mix, then add SuperScript at a ratio of 1 ul SuperScript for every 9 ul of First Strand reagent.  For example, for 10 reactions, mix 90 ul with 10 ul of SS II.  Excess mix can be stored in the -20C freezer.

25. Add 8 ul of First Strand SuperScript mix to each well containing the mRNA.

26. Place the plate in thermocycler and run the “Synthesize 1st Strand” program (25C for 10 min, 42C for 15 min, 70C for 15 min, hold at 4C).

{% include note.html content="This step takes 40 minutes and is your first large break." %}

## Step 3:  2<sup>nd</sup> strand cDNA synthesis

{% include important.html content="When the first strand synthesis is completed, immediately proceed to the second strand synthesis" %}

28. Add 20 uL second strand marking mix and 5 uL resuspension buffer to each well. Pipette up and down 6 times.

29. Centrifuge the plate at 600 x g for 30 sec.

30. Place plate in thermocycler and run the ‘2nd strand’ reaction - 16C for 1hr, with the lid set to 30C.

{% include note.html content="This is your second large break of the day." %}

## Step 4: Reaction clean-up

31. When the reaction is complete, add 90 ul of well-mixed AMPure XP beads to each well containing 50 ul of double stranded cDNA. Incubate RT for 15 min.

32. Place the plate on the magnet and let sit for 5 min.

33. Remove and discard 135 ul per well, being careful not to disturb the beads.

34. Wash beads on magnet by adding 190 ul of 80% EtOH to each well, without disturbing the beads incubate 30 sec at RT.

35. Remove and discard the supernatant, repeat the wash step and remove the supernatant again. Let the plate stand on the magnet at RT until dry, usually less than 5 minutes. When dry, the beads will appear matte and cracked. Remove plate from magnet when all samples are dry.

{% include important.html content="Use a p10 pipette to remove any residual ethanol from the bottom of the well." %}

36. Add 17.5 ul of Resuspension Buffer to each well and pipette up and down 10 time to mix. Incubate for 2 min at RT.

{% include note.html content="The beads may be dry and you may have to pipette up and down more than 10 times until the beads are fully resuspended." %}

37. Place the plate on the magnetic stand for 5 minutes.

38. Transfer 15 ul of the supernatant (contains the ds cDNA) to new a new plate.

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

## Step 5: Adenylate cDNA ends

39. Add 12.5 ul of thawed A-tailing mix and 2.5 uL of resuspension buffer to each well. Pipette up and down 10 times.

40. Carry out A-tailing by running the thermocycler ‘ATAIL70’ program.

{% include note.html content="This step takes 35 minutes and is the first large break of the day." %}

## Step 6: ligate adapters to ends

41. Add 2.5 ul of resuspension buffer, 2.5 ul of ligation mix, and 2.5 ul of a unique RNA adapter index to each well, mix well by pipetting.

{% include note.html content="Remove the ligation mix immediately before use and return to -20C storage immediately after use." %}

{% include note.html content="I moved individual adapter index tubes to strip tubes to make it easier to add the unique indexes to the wells with a multichannel pipette." %}

{% include important.html content="Make sure to record which sample received which index adapter number." %}

42. Seal the plate and incubate at 30C in thermocycler for 10 min using the 'LIGADAPTER' program.

43. Remove the plate from the thermocycler and add 5 ul of stop ligation buffer to each reaction, mix well by pipetting.

44. Add 42 ul of AMPure XP beads to each reaction, mix well by pipetting, and incubate at RT for 15 min.

45. Place on magnetic stand for 5 min at RT.

46. With the plate on the magnetic stand, remove 79.5 ul of supernatant from each sample, being careful not to disturb the beads.

47. With the plate on the magnetic stand, wash with 190 ul 80% EtOH for 30 sec, then remove the ethanol.

48. Perform the wash step again.

49. Use a p10 pipette to remove residual ethanol. Keep the plate on the magnet at RT until dry, usually less than 5 minutes. When dry, the beads will appear matte and cracked. Remove plate from magnet when all samples are dry.

50. Remove the plate from the magnetic stand and add 52.5 ul of Resuspension Buffer to each well, and mix well by pipetting. Incubate at RT for 2 min

51. Place the plate on magnet for 5 min.

52. Recover 50 ul from each well and transfer to a new plate.

53. Carry out a second cleanup round. Add 50 uL of mixed AMPure beads to each well, mix well, incubate for 15 min at RT.

54. Place the plate on the magnetic stand for 5 min.

55. With the plate on the magnetic stand, remove and discard 95 ul of supernatant from each sample.

56. With the plate on the magnetic stand, wash the beads with 190 ul of 80% EtOH for 30 s, then remove the ethanol.

57. With the plate on the magnetic stand, wash the beads again with 190 uL of 80% EtOH for 30 s, then remove the ethanol.

58. Use a p10 pipette to remove residual ethanol. Keep the plate on the magnet at RT until dry, usually less than 5 minutes. When dry, the beads will appear matte and cracked. Remove plate from magnet when all samples are dry.

59. Resuspend beads in 22.5 ul of resuspension Buffer, mix well by pipetting, and incubate 2 min at RT.

60. Transfer the plate to the magnetic stand and incubate for 5 min.

61. Recover 20 ul from each well and transfer to a new plate.

## Step 7: PCR amplify library

62. Add 5 ul of PCR primer cocktail and 25 ul of PCR master mix to each well, place the plate in the thermocycler and run the “PCR” program.

{% include note.html content="This is another break for 30 minutes." %}

63. Add 50 ul of AMPure beads to each well and mix well by pipetting. Incubate 15 min at RT.

64. Place the plate on the magnet for 5 min.

65. Remove and discard 95 ul of supernatant from each well.

66. Wash the beads 190 ul/well of 80% EtOH, wait 30s, remove the supernatant.

67. Repeat the ethanol wash step.

68. Use a p10 pipette to remove residual ethanol. Keep the plate on the magnet at RT until dry, usually less than 5 minutes. When dry, the beads will appear matte and cracked. Remove plate from magnet when all samples are dry.

69. Remove the plate from the magnetic stand, add 32.5 ul of resuspension buffer and mix well, by pipetting, and incubate for 2 min at room temperature.

70. Place the plate back on the magnetic stand for 5 minutes.

71. Remove 30 uL of supernatant from each sample and move it into a new plate. This is the final cDNA product.

{% include important.html content="Congratulations! You're done!...well, almost" %}

{% include note.html content="Perform quality control steps - we use a Tapestation to determine the library size and qubit to quantify the libraries." %}

{% include note.html content="We recommend sequencing the libraries within 3 weeks." %}

# Sequencing Guidelines

## Normalize and Pool

1. Quantify each of your libraries on Qubit. For most libraries, using the HS dsDNA Qubit assay with 2uL of input will yield a reading. Record the concentration in ng/uL for each library.

2. Run your samples on Tapestation with either the D1000 or the HSD1000 assay. Remember to allow Tapestation reagents to sit at room temperature for at least 30 minutes before use. Save your Tapestation results by going to File -> Create Report -> Save as pdf. This file can then be emailed or uploaded to Asana. For the base pair length, we usually use the value of the peak identified by the Tapestation analysis software. This value is shown both on the tracing itself and in the Peak Table for each sample. 

3. Download our nM Conversion Calculator [here](https://drive.google.com/file/d/1IOUsWLJIetkb6ZN4B-Bdfpx-IiRB1JQa/view?usp=sharing). Enter the concentration (from Qubit) and the base pair length (from Tapestation) in the appropriate cells and it will give you the nM concentration for each library. Normalize and pool all your libraries to 4, 2, 1, or 0.5 nM in a LoBind microcentrifuge tube. If you need to dilute your libraries, we recommend using at least 2uL to minimize pipetting errors. The example sheet of the calculator provides further detail.

4. Quantify your pool on Qubit and enter into the calculator sheet to check that your pool is close to the nM concentration you normalized to. 

## Setup Run in Basespace

1. Sign into Basespace, then go to the Prep tab, Biological Samples, and select Import Samples on the upper right. Use Illumina's Sample Import Template to enter information about your samples. The SampleID and Name can be the same, but make sure they are unique for each sample. Species can be left blank. Upload the completed .csv to import your samples.

2. Continue to Prep Libraries. Select your library prep kit based on the index format used. If you used our plate indexes select "IDT-ILMN TruSeq DNA-RNA UD 96 Indexes." If you used another index format, you will need to use a different entry for library prep kit. The your project name as the Plate ID. For each sample, check the box next to it on the left, then drag the sample name to the appropriate index well.

3. Proceed to Pool Libraries. Select all your samples on the left, then drag and drop in the pool on the right. Name the pool your project name. 

4. Continue to Plan Run. Select NextSeq and name your run your project name. Select Single Read or Paired End Read, then enter the cycle numbers based on your selected kit. For example, if you were doing a run using a High Output 75 Cycle kit, you would select Single Read and enter 76 for Read 1 Cycles and 0 for Read 2 Cycles. 

5. Press Sequence to complete planning the run. The run will now be available for selection on the sequencer.

## Loading the Sequencer

The next step is to dilute and denature the prepared libraries. Illumina's general guidelines for this on the NextSeq can be found [here](https://support.illumina.com/content/dam/illumina-support/documents/documentation/system_documentation/nextseq/nextseq-500-550-denature-dilute-libraries-guide-15048776-15.pdf).

Illumina's system guide for the NextSeq, which covers the sequening workflow, can be found [here](https://support.illumina.com/content/dam/illumina-support/documents/documentation/system_documentation/nextseq/nextseq-500-system-guide-15046563-06.pdf). 

Your final loading concentration should be 1.3 - 1.8 pM, with most pools loaded at 1.4 or 1.5 pM.

{% include links.html %}
