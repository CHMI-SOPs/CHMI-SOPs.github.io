---
title: Single Cell RNAseq – library prep
tags: [transcriptomics]
keywords: transcriptomics
summary: "post-encapsulation steps for preparing sequence-ready libraries for scRNAseq"
sidebar: mydoc_sidebar
permalink: mydoc_scRNAseq_libraryPrep.html
folder: mydoc
---

## Before you start

### Overview

**Day 1** - thaw samples, enzymatic digestion to remove the unwanted nucleic acids and primer dimers, then second strand synthesis. Linear amplification of the dsDNA made during second stand synthesis that takes place over night (between 13-15 hour incubation). 

**Day 2** - Check library on tapestation/bioanalyzer, amplified RNA is fragmented and used for second reverse transcription reaction to convert sample back to DNA and to add a read primer binding site to each molecule. Clean up with Ampure XP beads, amplified by PCR. qPCR is performed to determine optimal amount of cycles for the final PCR; once final PCR is finished, library can be QCed by tapestation and Qubit. 

Bead clean ups are performed after every enzymatic step

{% include warning.html content="AMpure XP beads need to be brought to room temperature for at least 30 minutes prior to use. Vortex beads well for at least 2 minutes before use." %}

Full protocol can be found [here](https://1cell-bio.com/wp-content/uploads/2017/03/InDrop_LibraryPrep_Protocol_v1.2.pdf) 

### Reagents
* [Nuclease-free water, Life Technologies, cat. no. 10977-023](https://www.thermofisher.com/order/catalog/product/10977023)
* [Agencourt AMPure XP magnetic beads, Beckman Coulter, cat. no. A63881](https://www.fishersci.com/shop/products/ampure-xp-60ml/nc9933872)
* [Exonuclease I, ExoI; 20,000 U/mL; NEB, cat. no. M0293L](https://www.neb.com/products/m0293-exonuclease-i-e-coli#Product%20Information)
* [FastDigest HinFI restriction endonuclease, HinFI; Thermo Fisher/Life Technologies, cat. no. FD0804](https://www.thermofisher.com/order/catalog/product/FD0804)
* [FastDigest Buffer 10x, ThermoFisher/Life Technologies, cat. no. B64](https://www.thermofisher.com/order/catalog/product/B64?SID=srch-hj-B64)
* [NEBNext® mRNA Second Strand Synthesis Module, NEB, cat. no. E6111S](https://www.neb.com/products/e6111-nebnext-ultra-ii-non-directional-rna-second-strand-synthesis-module#Product%20Information)
* [HiScribeTM T7 High Yield RNA Synthesis Kit, NEB, cat. no. E2040S](https://www.neb.com/products/e2040-hiscribe-t7-high-yield-rna-synthesis-kit#Product%20Information)
* [RNA Fragmentation Reagents, Ambion/Life technologies, cat. no. AM8740](https://www.thermofisher.com/order/catalog/product/AM8740)
* [PrimeScriptTM Reverse Transcriptase, Takara Clontec, cat. no. 2680A](https://www.takarabio.com/products/cdna-synthesis/reverse-transcriptases/primescript?catalog=2680B)
* [RNaseOUT Recombinant Ribonuclease Inhibitor, RNaseOUT,ThermoFisher Scientific, cat. no. 10777-019](https://www.thermofisher.com/order/catalog/product/10777019)
* [Deoxynucleotide (dNTP) Solution Mix, 10 mM each; NEB, cat. no. N0447L](https://www.neb.com/products/n0447-deoxynucleotide-dntp-solution-mix#Product%20Information)
* [Kapa 2x HiFi Hot Start PCR mix, Kapa Biosystems, cat. no. KK2601](https://www.kapabiosystems.com/product-applications/products/pcr-2/kapa-hifi-pcr-kits/#accordion-order)
* [Eva Green Dye, 20x in water; Biotium, cat. no. 31000-T](https://biotium.com/product/evagreen-dye-20x-in-water/)
* 100 μM PE2-N6 primer (1Cell)
* 5 μM PE1/PE2 primer mixture with indices (1Cell)
* 100 μM Custom read 1, read2, and index primers (1Cell)
* [Corning Costar Spin-X tube filters, Sigma-Aldrich, cat. no. CLS8162](https://www.sigmaaldrich.com/catalog/product/sigma/cls8162?lang=en&region=US)
* Bioanalyzer RNA and HSDNA chips and reagents *or* Agilent TapeStation HSRNA and HSD1000screen tapes and reagents (Aglient)

### Equipment
* Magnetic racks for PCR and/or 1.5 ml tubes
* Centrifuge (e.g., Eppendorf AG, Cat. No. 5424R)
* Thermo-conductive tube rack (VWR Scientific Cat. No. 95045-464) 
* Thermal cycler
* qPCR machine
* Thermomixer or dry bath for 1.5 ml tubes
* BioAnalyzer (Agilent) or Tapestation (Agilent)
 
### RNA Elution Buffer (RE)
* **150 uL** of 1 M Tris-HCl pH 7.5
* **3 uL** of 0.5 M EDTA
* Add nuclease-free water to bring the final volume to 15 mL
* This can be aliquoted into nuclease-free tubes and aliquots can be stored at 4C short term or -20C long term. 

### DNA Suspension Buffer (DS)
* **150 uL** of 1 M Tris-HCl pH 8.0
* **3 uL** of 0.5 M EDTA
* Add nuclease-free water to bring the final volume to 15 mL
* This can be aliquoted into nuclease-free tubes and aliquots can be stored at 4C short term or -20C long term. 

### Blocking Buffer (BB) 
used to block the pipet tips so your solution will not stick to the outside or the inside of your tip, block tip for all steps that you are pipetting just your sample):

* **100 uL** of 1 M Tris-HCl pH 8.0
* **2 uL** of 0.5 M EDTA
* **500 uL** of 10% Tween 20 (vol/vol) 
* **500 uL** of 2% BSA (wt/vol)
* **8898 uL** of Sterile Water
Total volume is 10 mL, aliquot into 1.5 mL tubes with approximately 0.5 mL per tube, store at -20C and thaw before library prep

{% include note.html content="Do not reuse an aliquot of blocking buffer once it was thawed for the day. Take out an aliquot a day and discard after use.." %}

**80% Ethanol**
* Make fresh each day for Ampure XP bead clean ups 

## Day 1

### Enzymatic Digestion (2hrs)

1. Thaw post-RT libaries on ice
2. Centrifuge at 4C for 5 mins at 19,000 rcf to pellet any cell debris in the tube, this will bring down any material more dense than your samples.
3. Prepare the Digestion Mix. For every 70uL of post-RT material, prepare 100uL of Digestion Mix (1000 cells is approximately equal to 35uL of post-RT material so if you sorted 3000 cells, make 150uL of Digestion Mix)

**Volumes for Digestion Mix:**

|                        | 1000 cells | 2000 cells | 3000 cells |
|------------------------|------------|------------|------------|
| ddH2O                  | 39.5 uL    | 79 uL      | 118.5 uL   |
| 10X Fast Digest Buffer | 4.5 uL     | 9 uL       | 13.5 uL    |
| Exonuclease I          | 2.5 uL     | 5 uL       | 7.5 uL     |
| HinFI                  | 3.5 uL     | 7 uL       | 10.5 uL    |
|                        | **50 uL**  | **100 uL** | **150 uL** |

{% include important.html content="All steps before linear amplification before in vitro transcription should be performed with a blocked tip. This miminizes the material loss due to adsorption. Immerse pipet tip into block buffer, pipet up and down once and the tip is ready for use.." %}

4. Without aspirating HFE-7500 oil from the bottom of the tube, carefully transfer the post-RT material from each sample to its own Costar Spin-X tube filter.

5. Add Digestion mix made in previous step to the top of your old tube with the HFE-7500 oil to wash off any residual sample that may still be on the top of the oil. Then transfer the digestion buffer mix to the Costar-x spin tube. 

6. Centrifuge the filter column at 4C for 5 mins at >5000 xg. 

7. Discard the filter membrane (this contains the beads and all the particles we wanted to filter out, your sample is in the supernatant in the flow through).

8. 

9. Purify the reaction by using AmpPure XP beads. At this stage, your products are RNA-cDNA hybrids. This is the general protocol for all AmpPure XP bead clean ups. Pay attention to the ratio in each step of beads: sample, the elution buffer used and the amount of elution buffer in each clean up. These will be different in the subsequent steps. 

* Ratio of AMpure XP beads to sample is 1.2X ; The elution buffer used here is **nuclease free water** at a volume of 17 uL

* Add volume of beads directly to the sample. Vortex to mix well.
* Incubate the sample at room temperature for 5 minutes. Your sample will bind to the beads in this step. 
* Briefly spin down tube. 
* Place the sample(s) on the magnetic stand for 3-5 minutes until the bead collects on the side of the well and the supernatant is clear. 
* Aspirate and discard the supernatant without disturbing the beads. 
* Keep the sample(s) on the magent and fill with 80% etoh making sure the bead is completely covered. Remove etoh from sample after 30 seconds. 
* Repeat wash step once more.
* After the second wash, spin tube down to get any excess etoh off the bead, aspirate out and discard. 
* Dry tubes at 37C with caps off for about 3 minutes or until the beads are dry. They should appear matte and begin to crack when dry.
* Add 17uL of elutent and vortex, spin down, and incubate at room temperature for 5 minutes.
* Return the tubes to the magnetic stand and incubate for 1 minute until supernatant is clear. supernatant now contains your sample. 
* Transfer the supernatant to a fresh tube, a PCR tube. 

## Day 2

### Second Strand Synthesis and In Vitro-Transciption (IVT)

Time: 16-18 hours

10. Set up Second Strand Synthesis (SSS) on ice:
* Add 2 uL of 10x SSS buffer to the 17 uL eluate from above in the PCR tube. 
* Mix by vortexing, spin down. Add 1 uL of SSS enzyme and mix gently by pipetting up and down. 
* Incubate the reaction at 16C for 2.5 hours, then 65C for 20 minutes. 

11. Make a master mix of the following components by multiplying the volume by the amount of samples you have; add 60 uL to each sample: 

| Component                                                 | Volume per rxn |
|-----------------------------------------------------------|----------------|
| Nuclease-free water                                       | 12 uL          |
| NEB T7 High Yield 10X Buffer                              | 8 uL           |
| NTP [4 different NTP buffers, ATP, UTP, CTP, GTP] (100mM) | 8 uL each      |
| NEB T7 High Yield Enzyme Mix                              | 8 uL           |
|                                                           | **60 uL**    |

12. Pipette to mix, spin plate down, and incubate at 37C for 13-15 hours with the lid heated to 50C.

* **Pause point** After 15h the IVT reaction can be kept at 4C for two hours, this is programmed into our PCR protocol on the machine. 

13. Purify the reaction by using AmpPure XP beads. This is the general protocol for all AmpPure XP bead clean ups. Pay attention to the ratio in each step of beads: sample, the elution buffer used and the amount of elution buffer in each clean up. These will be different in the subsequent steps. 

* Ratio of AMpure XP beads to sample is 1.3X (104uL of beads) ; The elution buffer used here is **RNA Elution Buffer** at a volume of 21 uL

* Add volume of beads directly to the sample. Vortex to mix well.
* Incubate the sample at room temperature for 5 minutes. Your sample will bind to the beads in this step. 
* Briefly spin down tube. 
* Place the sample(s) on the magnetic stand for 3-5 minutes until the bead collects on the side of the well and the supernatant is clear. 
* Aspirate and discard the supernatant without disturbing the beads. 
* Keep the sample(s) on the magent and fill with 80% etoh making sure the bead is completely covered. Remove etoh from sample after 30 seconds. 
* Repeat wash step once more.
* After the second wash, spin tube down to get any excess etoh off the bead, aspirate out and discard. 
* Dry tubes at 37C with caps off for about 3 minutes or until the beads are dry. They should appear matte and begin to crack when dry.
* Add 21uL of elutent and pipette to mix, spin down, and incubate at room temperature for 5 minutes.
* Return the tubes to the magnetic stand and incubate for 1 minute until supernatant is clear. supernatant now contains your sample. 
* Transfer 9uL of supernatant to a new PCR tube. Transfer 10uL to a LoBind tube. This can be stored in the -80C for up to 6 months, labeled as post-IVT back up.

14. Run a HS RNA Tapestation on the post-IVT back up before transferring to the -80C freezer. 

**Fragmentation of Amplified RNA**

Time: 20 mins

15. Prepare Fragmentation Stop Mix for each sample: 

| Component                                     | Volume per rxn |
|-----------------------------------------------|----------------|
| RNA Elution Buffer                            | 9.8 uL         |
| AMPure Beads                                  | 26.4 uL        |
| Stop Solution from the RNA fragementation kit | 1.2uL          |
|                                               | Total  37.4 uL |

16. Vortex the solution from above and place on ice. 

17. Allow the thermalcycler to reach 70C (lid at 100-110C)

18. On ice, add 1 uL of 10X RNA Fragmentation reagent to 9 uL of purified of IVT product in plate from step 12.

19. Spin down plate and fragment on thermalcycler at 70C for about 1-3 minutes, depending on what your post IVT tapestation looked like. Here is how to determine the fragmentation time:

* 1cellbio's general rule is fragment for around 1 min if the bulk of the sample is below 1000nt, 2 mins if the bulk of the sample is between 1000-2000nt, and 3 mins if the majority of your sample is above 2000nt.

20. Cool the fragmentation reaction on ice and immediately add 34uL of Fragmentation Stop Mix (prepared in step 14) to each sample and pipette up and down to mix well. Spin plate very briefly. 

21. Incubate samples on ice for 5 minutes. 

22. Plate samples on magnetic rack and continue through the AMPure XP bead clean up steps below: 

 Ratio of AMpure XP beads to sample is 1.3X (104uL of beads) ; The elution buffer used here is **RNA Elution Buffer** at a volume of 21 uL

* Place the sample(s) on the magnetic stand for 3-5 minutes until the bead collects on the side of the well and the supernatant is clear. 
* Aspirate and discard the supernatant without disturbing the beads. 
* Keep the sample(s) on the magent and fill with 80% etoh making sure the bead is completely covered. Remove etoh from sample after 30 seconds. 
* Repeat wash step once more.
* After the second wash, spin tube down to get any excess etoh off the bead, aspirate out and discard. 
* Dry tubes or plate at 37C with caps off for about 3 minutes or until the beads are dry. They should appear matte and begin to crack when dry.
* Add 10uL of elutent and pipette to mix, spin down, and incubate at room temperature for 5 minutes.
* Return the tubes to the magnetic stand and incubate for 1 minute until supernatant is clear. Supernatant now contains your sample. 
* Transfer 8uL of supernatant to a new well. 

**Reverse Transcription using Random Hexamers**

Time: 2.5 hours

23. On ice, combine the following: 

| Component                                            | Volume per rxn |
|------------------------------------------------------|----------------|
| Purified Fragmented amplified RNA from previous step | 8 uL           |
| dNTP (10mM)                                          | 1 uL           |
| PE2-N6 primer (100uM)                                | 2uL            |
|                                                      | Total  11 uL   |

24. Pipette to mix, spin down. Incubate at 70C (lid at 105C) for exactly 3 minutes and cool immediately on ice. 

25. On ice, add the following components to the mix to bring the total volume to 20uL: 

| Component                                     | Volume per rxn |
|-----------------------------------------------|----------------|
| Nuclease-free water                           | 3.5 uL         |
| 5x Prime Script Buffer                        | 4 uL           |
| RNase OUT (40 U/uL)                           | 1 uL           |
| Prime Script Reverse Transcriptase (200 U/uL) | 0.5 uL         |
|                                               | Total  9 uL    |

26. Mix gently by pipetting and incubate the reaction at 30C for 10 minutes followed by 42C for 1 hour then 70C for 15 minutes to heat inactivate the enzyme. 

27. Add 20uL of nuclease-free water, mix by pipetting, and save 20 uL as "pre-PCR back-up" in a LoBind tube. This back up can be stored at -80C for up to 6 months.

28. Purify the reaction with AMPure XP Beads

* Ratio of AMpure XP beads to sample is 1.2X (24 uL) ; The elution buffer used here is **DNA elution buffer** at a volume of 12 uL

* Add volume of beads directly to the sample. Pipette to mix well.
* Incubate the sample at room temperature for 5 minutes. Your sample will bind to the beads in this step.  
* Place the sample(s) on the magnetic stand for 3-5 minutes until the bead collects on the side of the well and the supernatant is clear. 
* Aspirate and discard the supernatant without disturbing the beads. 
* Keep the sample(s) on the magent and fill with 80% etoh making sure the bead is completely covered. Remove etoh from sample after 30 seconds. The ethanol should fully cover the bead in this step, in a plate add 180 uL of the 80% ethanol.
* Repeat wash step once more.
* After the second wash, use a P10 to get remaining ethanol out of sample and discard. 
* Dry samples at 37C with no cover for about 3 minutes or until the beads are dry. They should appear matte and begin to crack when dry.
* Add 12uL of elutent and pipette to mix. 
* Incubate at room temperature for 5 minutes.
* Return the tubes to the magnetic stand and incubate for 1 minute until supernatant is clear. Supernatant now contains your sample. 
* Transfer 10 uL of supernatant to a new well.  

**Diagnostic qPCR**

Time: 1.5-2 hours

29. Perform a quantitative PCR (qPCR) to determine the correct number of PCR amplification cycles in the next step. Combine the following components on ice: 

| Component                      | Volume/ rxn  |
|--------------------------------|--------------|
| Nuclease-free water            | 6.5 uL       |
| Eluate from step 27            | 0.5 uL       |
| 2x Kapa HiFi Hot Start PCR Mix | 10 uL        |
| 20x Eva Green Dye              | 1 uL         |
| PE1/PE2 primer mix (5uM)       | 2 uL         |
|                                | Total  20 uL |

{% include important.html content="Use primers 6 and 12 first. If only running one sample, use primer 6, located in A6 on the well of the primer plate supplied by 1cellBio. If running two samples, use primer 6 and primer 12 (A6 and A12). If running more than two samples, once primers 6 and primer 12 are used, it does not matter which primer is used." %}

30. Perform the following qPCR thermalcycling program: 

Eva green uses the same excitation and emission settings as SYBR Green.

Italics denote steps to be run for 2 cycles.

Bold denotes steps to be run for 24 cycles. 

| Temp (C) | Time (min:sec)                 |
|----------|--------------------------------|
| 98       | 2:00                           |
| *98*     | *0:20*                         |
| *55*     | *0:30*                         |
| *72*     | *0:40*                         |
| **98**   | **0:20**                       |
| **65**   | **0:30**                       |
| **72**   | **0:40** with fluorescent read |

31. Set the qPCR threshold within the exponential phase of amplification, but closer to where the signal starts to emerge from the noise to avoid the possibilty of over-amplification. 
- To account for the differences of input material between the qPCR and the PCR amplification of our samples, we will calculate the amount of PCR cycles to amplify our sample with now.
- The library input is 19 times higher than the qPCR input, therefore the difference corresponds to log2^19 = 4.25 cycles. For example, if the number of cycles determines by the qPCR is 2 + 12.67, the required number of PCR cycles for library amplification is 2 + (12.67 -4.25) = 2 + 8.

**Library Amplification**

Time: 2 hours

32. Combine the following components on ice: 

| Component                      | Volume/ rxn  |
|--------------------------------|--------------|
| Nuclease-free water            | 0.5 uL       |
| Eluate from step 27            | 9.5 uL       |
| 2x Kapa HiFi Hot Start PCR Mix | 12.5 uL      |
| PE1/PE2 primer mix (5uM)       | 2.5 uL       |
|                                | Total  25 uL |

{% include important.html content="Use the same primer numbers that were used in the qPCR step. Again, use A6 and A12 first before using any other primer sets on the plate supplied by 1cellbio." %}

{% include important.html content="Every sample needs to have a unique primer set from this plate because this is how the samples will be determined from one another after sequencing is finished." %}

33. Perform thermal cycling protocol shown in step 29, also shown again below: 

Italics denote steps to be run for 2 cycles.

Bold denotes steps to be run for amount of cycles determined by qPCR. 

| Temp (C) | Time (min:sec) |
|----------|----------------|
| 98       | 2:00           |
| *98*     | *0:20*         |
| *55*     | *0:30*         |
| *72*     | *0:40*         |
| **98**   | **0:20**       |
| **65**   | **0:30**       |
| **72**   | **0:40**       |
| 72       | 5:00           |

- If working with multiple libraries that require different cycle numbers, set the thermal cycler to the maximum number of cycles needed, then manually remove each individual sample when they have reached the desired cycle number. 
- Move the individual libraries to an ice bucket while the rest of the libraries are amplifying. 

- Once every library has been amplified for the correct amount of cycles, transfer all libraries back to the PCR machine for the final step, 72C for 5 minutes. 

34. Add 25 uL of DNA Elution Buffer to the PCR product. 

35. Purify using AMPure XP beads. 

* Ratio of AMpure XP beads to sample is 0.7X (35 uL) ; The elution buffer used here is **DNA elution buffer** at a volume of 22 uL

* Add volume of beads directly to the sample. Pipette to mix well.
* Incubate the sample at room temperature for 5 minutes. Your sample will bind to the beads in this step.  
* Place the sample(s) on the magnetic stand for 3-5 minutes until the bead collects on the side of the well and the supernatant is clear. 
* Aspirate and discard the supernatant without disturbing the beads. 
* Keep the sample(s) on the magent and fill with 80% etoh making sure the bead is completely covered. Remove etoh from sample after 30 seconds. The ethanol should fully cover the bead in this step, in a plate add 180 uL of the 80% ethanol.
* Repeat wash step once more.
* After the second wash, use a P10 to get remaining ethanol out of sample and discard. 
* Dry samples at 37C with no cover for about 3 minutes or until the beads are dry. They should appear matte and begin to crack when dry.
* Add 22uL of elutent and pipette to mix. 
* Incubate at room temperature for 5 minutes.
* Return the tubes to the magnetic stand and incubate for 1 minute until supernatant is clear. Supernatant now contains your sample. 
* Transfer 20 uL of supernatant to a new well.  

This eluate is the final sequencing-ready library. 

36. Test library by running on the HS D1000. The library should look like a smooth hump starting at 200bp and ending at 1.5kb with an average size between 400 and 600bp. 

37. Perform Qubit on samples using the HS DNA assay to get the concentration for pooling and sequencing.

**Pause Point**: store the libraries at -80C or -20C. They should be stable for at least 1 year.

{% include links.html %}
