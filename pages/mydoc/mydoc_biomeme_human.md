---
title: Biomarker panel for field work on human cutaneous leishmaniasis
tags: [QPCR, mobile, diagnostics]
keywords:
summary: "Protocol for detection of Leishmania braziliensis, skin commensals and host pro-inflammatory gene expression from lesion swabs in human cases of cutaneous leishmaniasis "
sidebar: mydoc_sidebar
permalink: mydoc_biomeme_human.html
folder: mydoc
---

## Supplies
* [Biomeme M1 bulk sample prep kit for RNA](http://CHMI-sops.github.io/papers/Biomeme_M1kit_RNA.pdf)
* [Biomeme lyoRNA mastermix](http://CHMI-sops.github.io/papers/LyoRNA.pdf)
* [Biomeme homogenization sample collection kit](http://CHMI-sops.github.io/papers/Biomeme_homogenizationKit.pdf)
* Biomeme skin swabs (4 swabs per patient)
* well calibrated pipettors
* pipette tips for low vol (2-3ul), and standard volumes (~10-20ul, ~100ul, ~1ml)
* DNA loBind Eptubes
* 1cc and 20cc syringes (1 of each per sample you intend to process)
* 20x mix of primers and probes
* ice and ice packs for transport

## Sample collection

### swabs

For each patient, two sterile swabs (provided by Biomeme) are held together and used to swab the inner border and ulcer of the lesion (encircled 20x).  A second pair of swabs is used to sample from normal skin on the contralateral side of the same patient.  Swabs are then processed as follows: 

1. Immerse each pair of swabs into separate eptubes containing 1ml BLB/tube from Biomeme M1 RNA kit, twirl in media for approx. 1 min, discard swabs.
2. Attach standard lab 1cc syringe to Biomeme filter tip. Pump lysate up/down 10x, expel volume
3. Immediately move to **BPW** protein wash (1ml), pump up/down **3x**, expel volume
4. Immediately move to **BWB** wash buffer (1ml), pump up/down **1x**, expel volume
5. Immediately move to **BDW** drying wash (1ml), pump up/down **1x**, expel volume and excess BDW
6. Discard syringe but **keep filter tip**
7. Attach 20cc and pump up and down with air 10x to dry the column.
8. remove and discard the syringe.  Connect new Biomeme 'slip-tip' 1 cc syringe to the column and draw up 150 ul of Biomeme Elution Buffer (BEB).  Pump up/down 3x with BEB.
9. Expel the elution buffer into a final collection tube.  Typical elution volume is ~120ul, and contains both RNA and DNA.  We use appox. 15ul of this for any of the assays listed below, which means a single eluate is enough for at least 6 QPCR assays.

### fine needle aspirate (FNA)

After the physician has applied local anesthesia to the site of the lesion, a FNA is collected and dispensed into 1ml of BLB and processed in the same way as swabs (detailed above)

### biopsy

1/3 to 1/2 of a 4-5mm punch biopsy is placed into a 5ml screw-cap sample collection tube containing 1/2-inch ball bearing (from homogenization sample collection kit) and 2ml of BLB buffer (from M1 sample prep kit).  Samples are then processed as follows:

* with cap tightened, vigorously shake 5ml screw-cap by hand for 30sec to disrupt tissue in BLB
* let sit at room temp until all other patients and samples have been processed
* vigorously shake for another 30sec when ready to resume processing
* allow particulate to settle to bottom of tube
* use sample tip from M1 sample prep kit to draw up 1ml.  Avoid drawing up particulates.
* move to an empty eptube and process extract as indicated above for swabs. 

## Inflammation panel
The primers and probes below are for the detection of host transcripts present in cellular material on recovered from swabs, FNAs, or biopsies.

{% include note.html content="The 18S assay is included as a positive extraction control.  The primers recognize an exon in the 18S gene, so there will be some signal from DNA in the reaction (the Biomeme RNA extraction isolates both RNA and DNA), however, given the large copy number for 18S transcripts, there should be much stronger signal for RNA."%}

| name | Sequence (5' -> 3') |
|-------|--------|
| hIL1B fwd | CAA AGG CGG CCA GGA TAT AA |
| hIL1B rev | CTA GGG ATT GAG TCC ACA TTC AG |
| hIL1B probe | */56-FAM/*AGA GCT GTA */ZEN/* CCC AGA GAG TCC TGT*/3IABkFQ/* |
| hGZMB fwd | GTA CCA TTG AGT TGT GCG TG |
| hGZMB rev | CAT GCC ATT GTT TCG TCC ATA G |
| hGZMB probe | */56-FAM/*CCT CCA GAG */ZEN/* TCC CCC TTA AAG GAA GT*/3IABkFQ/* 
| h18S (+ control) fwd | provided by Biomeme |
| h18S (+ control) rev | provided by Biomeme |
| h18S (+ control) probe | provided by Biomeme |


## Microbial panel 
The primers and probes below are used for detection of *Staphylococcus aureus (Saur)*, *Streptococcus pyogenes (Spyo)* and *Leishmania braziliensis (Lbra)*

{% include note.html content="All of these targets are DNA, so be sure to use appropirate lysis buffer (BLB from DNA bulk extraction kit) and mastermix (LyoDNA)." %}

{% include note.html content="We prepare a standard curve for the *S. aureus* assay using genomic DNA provided by Biomeme.  Stock is ~100,000 *S. aureus* genomes per ul, and curve is 100000, 10000 and 1000 copies.  We prepare a similar standard curve from *L. braziliensis* promastigotes, with a stock that is also ~100,000 genome copies per ul.  When running a standard curve on the Two3 device, always put the tube containing the lowest amount of target in the center well.  This position is closest to the sensor, and therefore provides a bit more sensitivity."%}

* *Leishmania braziliensis* primer/probes are from [Weirather et al., 2011](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3209110/)
* *Streptococcus pyogenes* primer/probes were adapted from CDC [here](https://www.cdc.gov/streplab/protocols.html)
* *Staphylococcus aureus* primers and probes were provided by Biomeme Inc.


| name | Sequence (5' -> 3') |
|-------|--------|
| *Saur* fwd | provided by Biomeme |
| *Saur* rev | provided by Biomeme |
| *Saur* probe | provided by Biomeme |
| *Spyo* fwd | GCA CTC GCT ACT ATT TCT TAC CTC AA |
| *Spyo* rev | GTC ACA ATG TCT TGG AAA CCA GTA AT |
| *Spyo* probe | */56-FAM/*CCG CAA CTC */ZEN/* ATC AAG GAT TTC TGT TAC CA*/3IABkFQ/* |
| *Lbra* fwd | TGC TAT AAA ATC GTA CCA CCC GAC A |
| *Lbra* rev | AAA TGG CAT ACA GAA ACC CCG TTC |
| *Lbra* probe | */56-FAM/*GCC TCT GGG */ZEN/* TAG GGG CGT TCT GCA A*/3IABkFQ/* |





{% include links.html %}
