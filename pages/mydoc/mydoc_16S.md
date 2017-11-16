---
title: 16S rRNA gene sequencing
tags: [library construction]
keywords:
summary: "Preparation of V4 region, 16S dual-indexed libraries for sequencing on an Illumina platform"
sidebar: mydoc_sidebar
permalink: mydoc_16S.html
folder: mydoc
---

## Before starting 
This protocol is derived from Pat Schloss' Laboratory at the University of Michigan. Please cite their work.  If you use the protocol below, please cite [their manuscript on the dual-index sequencing strategy](http://aem.asm.org/content/early/2013/06/17/AEM.01043-13).  Also, see the [Supplemental materials](http://aem.asm.org/content/early/2013/06/17/AEM.01043-13/suppl/DCSupplemental) for a detailed look at the primer design for this strategy.

## Materials
* Order primers from IDT
* [SequalPrep Normalization Kit, Invitrogen, A10510-01](https://www.thermofisher.com/order/catalog/product/A1051001)
* RT-PCR Grade Water, Ambion, AM9935
* AccuPrime PFX Supermix, Invitrogen, 12344040

## Step 1: Initial Setup

1. Reconstitute indexed primers to 100 μM. See [Appendix D of the supplement](http://aem.asm.org/content/early/2013/06/17/AEM.01043-13/suppl/DCSupplemental) from the Schloss lab paper for primer design.  We purchase our primers from IDT with standard purification and no additonal modifications. 

{% include important.html content="Use high quality nuclease-free water that is PCR grade. Any contaminations in your primer will be carried into your experimental setup." %}

2. Array aliquots into four 96 well plates using the scheme below. Into each well of these plates, aliquot 1.5 uL of a 700 primer, 1.5 uL of a 500 primer, and 27 uL water. The final primer concentration is 10 μM. Label the primer plates and store at -20C:
* plate a: A701 – A712 with A501 – A508
* plate b: A701 – A712 with B501 – B508
* plate c: B701 – B712 with B501 – B508
* plate d: B701 – B712 with A501 – A508

3. Extract template DNA and array in 96-well format leaving two wells open (one for a negative water control and another for the positive Mock Community control).

{% include note.html content="Depending on your thermocycler, plates or seals, you may experience problems with evaporation around the edges of plates.  To avoid having this confound your PCR reaction, consider leaving the border wells empty (rows A and H, columns 1 and 12), leaving 60 samples per plate." %}

{% include note.html content="We use the Qiagen PowerSoil DNA kit to extract DNA from our samples. You may use this method or a different method, just make sure to choose a consistent method for all of your experiments to minimize experimental variation and subsequent problems with data analysis." %}

## Step 2: PCR

{% include note.html content="These steps may be performed using an epMotion or similar automated pipetting system." %}

{% include important.html content="Perform each reaction in duplicate to minimize experimental error and jackpotting." %}
 
1. Dispense 17 μl of Accuprime Pfx Supermix into each well of a new 96 well plate.

2. Using a multichannel pipette, transfer 2 μl of each paired set of index primers to the corresponding well on the PCR plate. Be sure to follow the layout chosen in the sample sheet.

3. Using a multichannel pipette, transfer 1 μl of template DNA per well to the corresponding well on the PCR plate.

4. Add 1 μl of PCR grade dH2O to the negative control well, and 1 μl of Mock Community to the positive control well.
    - I sometimes use other sequencing controls, such as DNA extracted from a pure culture. 

5. Repeat for up to four 96-well plates. Seal plates, vortex briefly and spin down contents.

6. Place in thermocycler and run the following program (bold denotes steps to be run for 30 cycles)

| Temp (C) | Time (min:sec) |
|-------|--------|
| 95 | 2:00 |
| **95** | **0:20** |
| **55** | **0:15** |
| **72** | **5:00** |
| 72 | 10:00 |
| 4 | hold |


### Gel Electrophoresis
1. A random row of wells should be selected from each PCR plate and run on a gel to confirm success of the PCR.
2. Use 2 μl of sample, 4 μl of loading dye in a 1% agarose gel.
3. Run at 100v for 30 minutes alongside a standard ladder.
4. Photograph gel under UV. Check to be sure there is a band for every well.
    - I do not typically do this anymore as I perform the reactions in duplicate.

## Step 3: Cleanup, Normalization, and Pooling

Use the SequalPrep Normalization Plate Kit to normalize concentrations of PCR reactions prior to pooling

1. Pool duplicate PCR reactions (20 μl + 20 μl for a total of 40 μl).

2. Transfer 18 μl of pooled PCR product from plate to corresponding well on the normalization plate.

3. Add 18 μl/well of Binding Buffer. Mix by pipetting, then seal, vortex, and spin briefly.

4. Incubate at room temperature for 60 minutes.

{% include note.html content="can incubate overnight if needed, however this extra time does not improve binding." %}

5. Aspirate liquid from the wells, being careful not to scrape the sides of the wells.

6. Add 50 μl of Wash Buffer and pipette up and down twice, then aspirate *immediately*. Ensure there is no residual wash buffer in any wells.

7. Add 20 μl of Elution Buffer. Mix by pipetting up and down 5 times. Seal, vortex, and spin briefly.

8. Incubate at room temperature for 5 minutes.

9. Create a pool from each plate. Take 5 μl of each well to pool. The use of an empty 96-well plate may facilitate the use of multichannel pipettes.

10. Freeze the remaining sample for later use.

## Step 4: Library QC and normalization

### Agilent Tapestation
Use Agilent HS DNA 1000 Tapes.  If significant primer peaks are seen (~120 bp), these can be removed by cleaning up with 1 round of purification using AMPureXP beads at a volume ratio of 0.6: 1 (beads:volume DNA). 

### Qubit
use the high sensitivity DNA assay.  Create normalized pools from each plate by diluting all samples down to match the least concentrated plate. Create a single final pool by adding equal amounts of each post PCR normalized pool. Final pool must be >10μl in total volume. 40-80μl is ideal.  The target concentration is 1 or 2 nM. 

## Step 5: MiSeq Sequencing

### Run set-up
1. Remove a 500 cycle reagent cartridge from the -20 °C freezer. Place in room temperature water bath for one hour. Place HT1 buffer tube in the 4 °C fridge.

2. Copy sample sheet to sample sheet folder on MiSeq. Rename sample sheet to match barcode of reagent cartridge.
    - I use dummy barcodes AAAAAAAA and AAAAAAAA. The files can be downloaded from Basespace in an "undetermined.fastq.gz" format, and I use these files and then perform the demultiplexing in QIIME.

3. When the reagent cartridge has thawed, dry bottom with paper towel. Invert the cartridge repeatedly to check each well is thawed. This also serves to mix the reagents. Place in hood.

4. Thaw library, PhiX, and sequencing primers. Check to make sure HT1 is thawed.

5. Place 3 μl of the Read 1 Sequencing Primer(s) into a clean PCR tube. Repeat in separate tubes for the Index Primer(s) and Read 2 Sequencing Primer(s).

6. Using a 1000 μl pipette tip, break the foil over wells 12, 13, 14, and 17.

7. Use an extra long 100 μl tip with the pipettor set on 75 μl to transfer the 3 μl of Read 1 Sequencing Primer to the bottom of well 12 and pipette 10X to mix. Repeat this process spiking the Index Primer into well 13 and the Read 2 Sequencing Primer into well 14.

8. Prepare a fresh dilution of 0.2N NaOH.

9. To a 1.5ml tube add 10 μl of library, and 10 μl of 0.2N NaOH. To a separate tube add 2 μl PhiX, 3 μl PCR grade water, and 5 μl of 0.2N NaOH. Vortex both tubes to mix and spin for 1 minute at 400rcf. Note: NaOH concentration on the flow cell must remain under 0.001N. Adjusting the concentration of the NaOH used to denature the DNA to 0.1N may be necessary.

10. Allow the tubes to incubate at room temperature for 5 minutes. Immediately add 980 μl of HT1 to the library tube, and 990 μl HT1 to the PhiX tube.

11. Use HT1 to dilute both the library and PhiX to 10pM. For a 5% PhiX run, combine 950 μl of 3.5pM Library and 50 μl PhiX in a final tube. Vortex. Load 600 μl of this solution into well 17 on the reagent cartridge. See example below:
* (1.45 nM library x 10 μl) + (0.2N NaOH x 10 μl) + 980 μl HT1 = 14.5pM Lib, 0.002N NaOH
* (14.5pM lib x 241.38 μl) + 758.62 μl HT1 = 3.5pM lib, 0.00048N NaOH
* [(10nMPhiXx2μl)+3μlH2O]+(0.2NNaOHx5μl)+990μlHT1=20pMPhiX,
0.001N NaOH
* (20pM PhiX x 175 μl) + 825 μl HT1 = 3.5pM PhiX, 0.0000175N NaOH
* (3.5pM Lib x 950 μl) + (3.5M PhiX x 50 μl) = solution loaded
* Solution loaded is 3.5pM overall with a 3.325pM Library concentration, 0.175pM
PhiX concentration, and 0.0000457N NaOH

13. Set reagent cartridge aside. Unbox flow cell and PR2 bottle.

14. Thoroughly rinse the flow cell with Milli-Q water. Carefully dry by blotting with lint free wipes (Kimwipes). Give special attention to the edges and points of intersection between the glass and plastic.

15. Wet a new wipe with 100% alcohol and wipe the glass on both sides avoiding the rubber intake ports.

16. Visually inspect the flow cell to ensure there are no blemishes, particles, or fibers on the glass.

17. Follow on screen instructions and load the flow cell, reagent cartridge, and PR2 bottle. Empty and replace the waste bottle.

18. Ensure the machine recognizes the correct sample sheet and the run parameters are correct.

19. Wait for the MiSeq to perform its pre-run checks, and press start.

### Run Monitoring

1. The run should be monitored periodically using Illumina Sequence Analysis Viewer.

2. Ideal parameters for a 95% 16S run:
* Cluster density 700-800k/mm2
* greater than 85% clusters passing filter
* 5% aligned (amount of PhiX)
* No spikes in corrected intensity plot
* All indices identified following index reads
* Final >Q30 score of >70%

### Final Steps

1. Perform post run wash.

2. Dispose of liquid waste in appropriate hazardous jug and reagent cartridge in hazardous
bucket.

3. When MiSeq Reporter finishes, copy the fastq files from the analysis folder to the run folder
on the NAS drive.

4. Perform maintenance wash if required.

5. Confirm with investigator that data are of sufficient quality and quantity.


{% include note.html content="We recommend sequencing the libraries within 3 weeks." %}

{% include links.html %}

