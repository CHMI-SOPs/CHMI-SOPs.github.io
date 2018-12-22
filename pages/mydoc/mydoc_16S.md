---
title: 16S rRNA gene sequencing
tags: [library_prep, microbiome]
keywords:
summary: "Preparation of V4 region, 16S dual-indexed libraries for sequencing on an Illumina platform"
sidebar: mydoc_sidebar
permalink: mydoc_16S.html
folder: mydoc
---

## Before starting 
This protocol is derived from Pat Schloss' Laboratory at the University of Michigan. Please cite their work.  If you use the protocol below, please cite [their manuscript on the dual-index sequencing strategy](http://aem.asm.org/content/early/2013/06/17/AEM.01043-13).  Also, see the [Supplemental materials](http://aem.asm.org/content/early/2013/06/17/AEM.01043-13/suppl/DCSupplemental) for a detailed look at the primer design for this strategy.

## Materials
* Order primers from IDT/
* [PicoGreen dsDNA Assay Kit, ThermoFisher, P7589](https://www.thermofisher.com/order/catalog/product/P7589)
* [Fluotrac 200 plates- clear bottom, black, medium bind, USA Scientific, 5665-5096](https://www.usascientific.com/96-well-fluotrac-200-clear-bottom-black-plate.aspx)
* RT-PCR Grade Water, Ambion, AM9935
* AccuPrime PFX Supermix, Invitrogen, 12344040

## Step 1: Initial Setup

* Reconstitute indexed primers to 100 μM. See [Appendix D of the supplement](http://aem.asm.org/content/early/2013/06/17/AEM.01043-13/suppl/DCSupplemental) from the Schloss lab paper for primer design.  We purchase our primers from IDT with standard purification and no additonal modifications. 

{% include important.html content="Use high quality nuclease-free water that is PCR grade. Any contaminations in your primer will be carried into your experimental setup." %}

* Array aliquots into four 96 well plates using the scheme below. Into each well of these plates, aliquot 1.5 uL of a 700 primer, 1.5 uL of a 500 primer, and 27 uL water. The final primer concentration is 10 μM. Label the primer plates and store at -20C:
* plate a: A701 – A712 with A501 – A508
* plate b: A701 – A712 with B501 – B508
* plate c: B701 – B712 with B501 – B508
* plate d: B701 – B712 with A501 – A508

* Extract template DNA and array in 96-well format leaving two wells open (one for a negative water control and another for the positive Mock Community control).

{% include note.html content="Depending on your thermocycler, plates or seals, you may experience problems with evaporation around the edges of plates.  To avoid having this confound your PCR reaction, consider leaving the border wells empty (rows A and H, columns 1 and 12), leaving 60 samples per plate." %}

{% include note.html content="We use the Qiagen PowerSoil DNA kit to extract DNA from our samples. You may use this method or a different method, just make sure to choose a consistent method for all of your experiments to minimize experimental variation and subsequent problems with data analysis." %}

## Step 2: PCR

{% include note.html content="These steps may be performed using an epMotion or similar automated pipetting system." %}
 
* Dispense 17 μl of Accuprime Pfx Supermix into each well of a new 96 well plate.

* Using a multichannel pipette, transfer 2 μl of each paired set of index primers to the corresponding well on the PCR plate. Be sure to follow the layout chosen in the sample sheet.

* Using a multichannel pipette, transfer 1 μl of template DNA per well to the corresponding well on the PCR plate.

* Add 1 μl of PCR grade dH2O to the negative control well, and 1 μl of Mock Community to the positive control well.
    - I sometimes use other sequencing controls, such as DNA extracted from a pure culture. 

* Repeat for up to four 96-well plates. Seal plates, vortex briefly and spin down contents.

* Place in thermocycler and run the following program (bold denotes steps to be run for 30 cycles)

| Temp (C) | Time (min:sec) |
|-------|--------|
| 95 | 2:00 |
| **95** | **0:20** |
| **55** | **0:15** |
| **72** | **5:00** |
| 72 | 10:00 |
| 4 | hold |


### Agilent TapeStation 4200
* A random sample from each row should be selected from each PCR plate and run on the tapestation to confirm success of the PCR.
* Use D1000 screen tape and reagent.

## Step 3:  Normalization, Pooling, and Clean up

Use the PicoGreen dsDNA Assay Kit to normalize concentrations of PCR reactions prior to pooling

{% include note.html content="20x TE Buffer comes in PicoGreen kit, dilute this to 1x TE Buffer" %}

{% include note.html content="PicoGreen Assay uses 5uL of DNA per sample." %}

* Thaw and spin down DNA plate

* Dilute PicoGreen reagent in 15 mL or 50 mL tube
	- For 1.5 DNA plates: 
		-15 mL 1 X TE Buffer
		-75 uL PicoGreen reagent

	-For 2 full DNA plates:
		-23 mL 1 X TE Buffer
		-115 uL PicoGreen reagent

{% include important.html content="Keep out of light and use within 1 hour, we cover these tubes with aluminum foil to keep out of light." %}

* Prepare standards:

{% include note.html content="We run one standard per Miseq run, you do not need to run one standard for each plate if using Promega Glomax Plate Reader. These standards are kept on an excel spreadsheet and the samples are compared to the standards using Prism or Excel. If using a different plate reader, it may require you to run a standard with every plate." %}

* Prepare 2 μg/mL lambda DNA standard in a 1.5 mL Eppendorf tube and MIX WELL (this is enough for two full columns):
	-	5 μL 100 μg/mL lambda DNA
	-   245 μL 1 X TE 


| Well | TE (μl) | 2 ug/mL lambda DNA (μl)| Final conc. (μg/mL) |
|------|---------|------------------------|---------------------|           
| A1 (BLANK) | 100 | 0 | 0 |
| B1 (BLANK) | 100 | 0 | 0 |
| C1 (BLANK) | 100 | 0 | 0 |
| D1 | 99 | 1 | 0.01 (10 ng/uL) |
| E1 | 98 | 2 | 0.02 (20 ng/uL) |
| F1 | 95 | 5 | 0.05 (50 ng/uL) |
| G1 | 90 | 10 | 0.1  (100 ng/uL) |
| H1 | 25 | 75 | 0.75 (750 ng/uL) |

* Add 95 uL 1 X TE Buffer and 5 uL of DNA to every other well you will be using.

* Add 100 uL of diluted PicoGreen Reagent that was made in the first step to all wells and pipette to mix several times.

* Incubate at room temperature for 5 minutes out of the light. 

{% include note.html content="We cover the plate with alumnium foil while incubating at room temperature" %}

* Wipe bottom of plate with KimWipe and load into fluorescent plate reader. 

* Promega Glomax Plate Reader will export the RFU per sample on an excel sheet. 

* Open Prism and choose "Interpolate unknowns from a linear standard curve" and make three columns labeled sample well, Final concentration (ng/uL) and RFU

* Copy and paste your standards at the top of this Prism page with the corresponding concentration from the table above and the RFU measured by the plate reader.

* Copy and paste the RFU values from your samples with the concentration column blank.

* Click "Analyze" found in the grey tab above the columns under Analysis, and choose "Linear Regression" under XY analyses, then in the following pop-up window check the box under "Interpolate" that reads "Interpolate unknowns from standard curve." A new file will appear on the left hand side under Results, entitled "Interpolated X values" and this is where your concentration of your samples can be found. 

* Pool the samples based off the concentration that was interpolated by either Prism or Excel for each plate. 

{% include note.html content="Make a different pool for every plate." %}

* Once you have the concentration, plug in the ng/uL and set the average base pair length to 460 into our [nM conversion calculator](https://docs.google.com/spreadsheets/d/1OfMuBNeNYJg1Umr3Xo58TgpqBmkn6zHcadwph_hyOIc/edit?usp=sharing)
* This will calculate your nM for each sample, once you have these numbers, compare them to each other and determine what your range is. We will choose the lowest number to normalize to within the range of your samples; if you have any outliers do not take these into account.

{% include note.html content="See Example Sheet on [nM conversion calculator](https://docs.google.com/spreadsheets/d/1OfMuBNeNYJg1Umr3Xo58TgpqBmkn6zHcadwph_hyOIc/edit?usp=sharing)" %}

* Start by adding the total volume of water to your Eppendorf tube first, then add each sample to this tube for your final pool of each plate.

* Proceed to cleaning up each pool:

* Vortex AMPure XP beads before each use.  Vortex AMPure XP beads frequently to make sure that beads are evenly distributed.

* Add AMPureXP beads at a volume ratio of 1.8: 1 (beads:volume DNA) to each pool and pipette up and down 10 times to mix well.

* Incubate at room temperature for 5 minutes.

* Place on a magnetic stand and wait until the liquid is clear (~2 minutes).

* Remove and discard all supernatant from each well.

* Wash 2 times as follows:
- Add 190 μl fresh 80% EtOH to each well.
- Incubate on the magnetic stand for 30 seconds.
- Remove and discard all supernatant from each well.

* Using a 20 μl pipette, remove residual 80% EtOH from each well.

* Air-dry on the magnetic stand for 15 minutes.

* Remove from the magnetic stand.

* Add 52.5 μl RSB to each well, pipette up and down 10 times to mix well.

* Incubate at room temperature for 2 minutes.

* Place on a magnetic stand and wait until the liquid is clear (~2 minutes).

* Transfer 50 μl supernatant to a new plate.

## Step 4: Library QC and normalization

### Agilent Tapestation
Use Agilent DNA 1000 Screentape and reagent.  If significant primer peaks are seen (~120 bp), these can be removed by cleaning up with 1 round of purification using AMPureXP beads at a volume ratio of 0.6: 1 (beads:volume DNA). 

### Qubit
use the high sensitivity DNA assay.  Create normalized pools from each plate by diluting all samples down to match the least concentrated plate. 

* Create a single final pool by adding the Qubit concentration and TapeStation average base pair length to the nM conversion chart for each pool then follow the same steps to normalize to a value of 8nM. Once you pool, Qubit again and check the final nM of your final pool from all the plates together.

* Final pool must be >10μl in total volume. 

## Step 5: MiSeq Sequencing

### Run set-up
* Remove a 500 cycle reagent cartridge from the -20 °C freezer. Place in room temperature water bath for one hour. Place HT1 buffer tube in the 4 °C fridge.

* Copy sample sheet to sample sheet folder on MiSeq. Rename sample sheet to match barcode of reagent cartridge.
    - use dummy barcodes AAAAAAAA and AAAAAAAA. The files can be downloaded from Basespace in an "undetermined.fastq.gz" format, and I use these files and then perform the demultiplexing in QIIME.

* When the reagent cartridge has thawed, dry bottom with paper towel. Invert the cartridge repeatedly to check each well is thawed. This also serves to mix the reagents. Place in hood.

* Thaw library, PhiX, and sequencing primers. Check to make sure HT1 is thawed.

* Place 3 μl of the Read 1 Sequencing Primer(s) into a clean PCR tube. Repeat in separate tubes for the Index Primer(s) and Read 2 Sequencing Primer(s).

* Using a 1000 μl pipette tip, break the foil over wells 12, 13, 14, and 17.

* Use a disposable transfer pipette to transfer the 3 μl of Read 1 Sequencing Primer to the bottom of well 12 and pipette 10X to mix. Repeat this process spiking the Index Primer into well 13 and the Read 2 Sequencing Primer into well 14.

* Prepare a fresh dilution of 0.2N NaOH.

* To a 1.5ml tube add 5 μl of library, and 5 μl of 0.2N NaOH. Pipette up and down 10 times to mix well.

* Incubate at room temperature for 5 minutes.

* Add 990 uL chilled HT1 to the tube containing the denatured library.

* Dilute the denatured library in HT1 to 8 pM loading molarity in a volume of 700 uL:
	- X nM undenatured library * 5 = Y pM Denatured library
	- [8 pM loading concentration * 700 uL]/ Y pM Denatured Library = Z uL Denatured Libary
	- 700 uL - Z uL of denatured library = amount of HT1 to add. 

* Add 123.5 uL of 8 pM denatured PhiX to this 700 uL of denatured and diluted library. 	

* Add 600 uL of sample (from step above) to well 17. 

* Set reagent cartridge aside. Unbox flow cell and PR2 bottle.

* Thoroughly rinse the flow cell with Milli-Q water. Carefully dry by blotting with lint free wipes (Kimwipes). Give special attention to the edges and points of intersection between the glass and plastic.

* Visually inspect the flow cell to ensure there are no blemishes, particles, or fibers on the glass.

* Follow on screen instructions and load the flow cell, reagent cartridge, and PR2 bottle. Empty and replace the waste bottle.

* Ensure the machine recognizes the correct sample sheet and the run parameters are correct.

* Wait for the MiSeq to perform its pre-run checks, and press start.

### Run Monitoring

* The run should be monitored periodically using Illumina Sequence Analysis Viewer.

* Ideal parameters for a 95% 16S run:
	* Cluster density 700-800k/mm2
	* greater than 85% clusters passing filter
	* 5% aligned (amount of PhiX)
	* No spikes in corrected intensity plot
	* All indices identified following index reads
	* Final >Q30 score of >70%

### Final Steps

* Perform post run wash.

* Dispose of liquid waste in appropriate hazardous jug and reagent cartridge in hazardous
bucket.

* When MiSeq Reporter finishes, copy the fastq files from the analysis folder to the run folder
on the NAS drive.

* Perform maintenance wash if required.

* Confirm with investigator that data are of sufficient quality and quantity.


{% include note.html content="We recommend sequencing the libraries within 3 weeks." %}

{% include links.html %}

