---
title: Portable QPCR
tags: [QPCR, mobile, diagnostics]
keywords:
summary: "Most of the projects we work on, whether profiling host gene expression or micobial communities, often yield at a candidate list of genes or organisms that we believe are linked to some phenotype.  Increasingly, we are interested in methods and technology that let us quantitiatively measure these features, particularly in a way that is portable and could be deployed 'stall-side' in a barn just as easily as at a lab bench.  For this, we've been using the Biomeme platform for end-to-end QPCR-based detection in the field"
sidebar: mydoc_sidebar
permalink: mydoc_biomeme.html
folder: mydoc
---

## Before starting
The protocols below detail how we've been using [Biomeme Inc's](http://biomeme.com/) bulk reagents for QPCRs.  Once you've optimized the assays using bulk reagents, assays can then be manufactured as room-temp stable QPCR assays for use in the field.  For the most part, we keep our mastermix and PCR conditions the same across all assays.  The variations come with the primer/probe design and optimizing extaction of DNA or RNA from different sample types.  So far, we've had good success with the primers/probes listed below and with extraction of nucleic acid from nasal and skin swabs.

{% include note.html content="The only difference between DNA and RNA protocols are the BLB buffer in the extraction kit, and the type of master mix you will use (LyoDNA versus LyoRNA)." %}

## Devices
The hand-held QPCR device made by Biomeme, called the 'three9', accomodates 9 tubes and three colors/tube: FAM, Cy5/ATTO647N and TexasRed.  ATTO647N is the brightest channel on the three9, so consider designing the target you anticipate being present in the lowest concentration and/or least sensitive PCR on that channel. FAM is the next brightest, followed by TexasRedX. If you are designing a triplex assay for use with the three9 that includes a positive control, use TexasRedX for the positive control.

## Preparing mastermix
Resuspend bulk lyophilized [LyoDNA](http://CHMI-sops.github.io/papers/LyoDNA.pdf), [LyoRNA](http://CHMI-sops.github.io/papers/LyoRNA.pdf) or [LyoGreen](http://CHMI-sops.github.io/papers/LyoGreen.pdf) master mix with 135 ul of PCR grade water (BEB buffer from the DNA extraction kits is water). This is a 10x stock.  Add 18 ul of glycerol to allow leftover mastermix to be frozen for reuse later.  LyoRNA master mix contains a reverse transcriptase for QPCR assays where the target is a RNA molecule.  Each resuspended vial contains enough mastermix for 60, 20ul reactions.


## Reaction set-up with LyoDNA or LyoRNA
A typical QPCR reaction on the biomeme platform contains the following components

| Reagent | vol (ul) |
|-------|--------|
| 20x primer/probe | 1 |
| 10x LyoDNA, LyoRNA or LyoGreen mastermix | 2 |
| isolated DNA or RNA | 5-17 |
| water | qs to 20 |

{% include important.html content="20x primer/probe stock contains 4uM of the forward primer and probe, and 8uM of the reverse primer in TE pH 8.0.  Final concentrations in the PCR reaction will be 200nM of forward and probe, 400nM of reverse.  If starting with 100 uM stocks, then add 84 uL TE, 4 uL of forward, 4 uL of probe and 8 uL of reverse, to get a 100 ul stock of 20x" %}


## Run set-up

* To begin, launch the Biomeme app on the iPhone connected to your device.
* To run any assays, you'll need to set up a data folder by selecting the 'data management' button on the main screen.  Name your folder, create any subfolders if necessary and save.
* Back on the main screen, choose 'protocol management' to set up a protocol that will contain your thermocycling conditions.  

{% include important.html content="Be sure to select a RT step at the start of a protcol if you are testing for RNA targets" %}

We've always used the standard thermocycling conditions that come pre-set on the device as follows:

| Temp (C) | Time (min:sec) |
|-------|--------|
| 45 | 10:00 |
| 95 | 10:00 |
| **95** | **0:15** |
| **60** | **1:00** |

**Bold** steps are repeated for 40 cycles total

* Give your protocol a name and select 'save' in the upper right corner of the app

* To begin a run, go back to the main screen of the app and choose 'start run'.  Choose your protocol and data folder, then follow the on screen instructions to begin the run.


{% include links.html %}
