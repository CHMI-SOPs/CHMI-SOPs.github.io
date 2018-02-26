---
title: Portable QPCR
tags: [QPCR, mobile, diagnostics]
keywords:
summary: "Most of the projects we work on, whether profiling host gene expression or micobial communities, often yield at a candidate list of genes or organisms that we believe are linked to some phenotype.  Increasingly, we are interested in methods and technology that let us *quantitiatively* measure these features, particularly in a way that is portable and could be used deployed 'stall-side' in a barn just as easily as at a lab bench.  For this, we've been using the Biomeme platform for end-to-end QPCR-based detection in the field"
sidebar: mydoc_sidebar
permalink: mydoc_biomeme.html
folder: mydoc
---

## Before starting
The protocols below detail how we've been using [Biomeme Inc's](http://biomeme.com/) bulk reagents for QPCRs.  Once you've optimized the assays using bulk reagents, assays can then be manufactured as room-temp stable QPCR assays for use in the field.  For the most part, we keep our mastermix and PCR conditions the same across all assays.  The variations come with the primer/probe design and optimizing extaction of DNA or RNA from different sample types.  So far, we've had good success with the primers/probes listed below and with extraction of nucleic acid from nasal and skin swabs.

{% include note.html content="The only difference between DNA and RNA protocols are the BLB buffer in the extraction kit, and the type of master mix you will use (LyoDNA versus LyoRNA)." %}

### Mastermix
Resuspend bulk lyophilized **LyoDNA** or **LyoRNA** Biomeme master mix with 132 ul of PCR grade water + 18 ul of glycerol.  This is a 10x stock.  Addition of glyceral allows leftover mastermix to be frozen for reuse later.  LyoRNA master mix contains a reverse transcriptase for QPCR assays where the target is a RNA molecule.  Each resuspended vial contains enough mastermix for 60 reactions of 20ul/rxn.

### Reaction
A typical QPCR reaction on the biomeme platform contains the following elements

{% include important.html content="20x primer/probe stock contains 4uM of the forward primer and probe, and 8uM of the reverse primer in TE pH 8.0.  Final concentrations in the PCR reaction will be 200nM of forward and probe, 400nM of reverse" %}


| Reagent | vol (ul) |
|-------|--------|
| 20x primer/probe | 1 |
| 10x LyoDNA or LyoRNA mastermix | 2 |
| isolated DNA or RNA | 5-17 |
| water | qs to 20 |


### Thermocycling conditions

| Temp (C) | Time (min:sec) |
|-------|--------|
| 45 | 10:00 |
| 95 | 10:00 |
| **95** | **0:15** |
| **60** | **1:00** |

**Bold** steps are repeated for 40 cycles total


## Avian assays

### Tracheal swabs
All avian assays begin with tracheal swabs collected in brain-heart infusion (BHI) media.  We typically have 11 swabs all stored in a single vial containing 5.5 ml of BHI media.  These swabs could be from multiple birds or from a single bird sampled multiple times, and this vial can be assayed fresh or after storage at -80C.  Here's our procotol for rapid, 1 minute DNA extraction using Biomeme reagents:

1. thaw vial containing BHI media and swabs
2. take 100 ul aliquot of sample for DNA or RNA extraction (might be quite viscous due to mucous)
3. add 100 ul sample to 1 ml of Biomeme Lysis Buffer (BLB) (if you plan to assay for IBV, use BLB from RNA kit)
4. with a 1cc syringe affixed to a Biomeme extraction column, push the extraction sample mix up and down 10 times
5. after expelling the volume the 10th time, wash the column by drawing up 500 ul of Biomeme Protein Wash (BPW) 1 time, then expel again.
6. draw up 1 ml of Biomeme Wash Buffer (BWB) and expel volume
7. draw up 1 ml of Biomeme Drying Wash (BDW) and expel volume
8. remove and discard the 1cc syringe, and attach a new 50cc syringe to the same column.  Pump up and down with air vigorously to dry the column.
9. remove and discard the 50cc syringe.  Connect new 1 cc syringe to the column and draw up 125 ul of Biomeme Elution Buffer (BEB).
10. Expel the elution buffer into a final collection tube.  Typical elution volume is 50-70 ul.  We use 5ul of this DNA for any of the assays listed below, which means a single eluate is enough for at least 9-10 QPCR assays.


### Primers and probes

#### Infectious Bronchitis Virus (IBV)

{% include note.html content="IBV is an RNA virus, so be sure to use the appropriate lysis buffer (BLB from RNA bulk extraction kit) and mastermix (LyoRNA)." %}

| name | Sequence (5' -> 3') |
|-------|--------|
| fwd | GCT TTT GAG CCT AGC GTT |
| rev | GCC ATG TTG TCA CTG TCT ATT G |
| probe | *FAM*-CAC CAC CAG AAC CTG TCA CCT C-*BHQ-1* |



#### *Mycoplasma gallisepticum* and *Mycoplasma synoviae* (Mg/Ms)

{% include note.html content="Mg and Ms targets are DNA, so be sure to use appropirate lysis buffer (BLB from DNA bulk extraction kit) and mastermix (LyoDNA)." %}

The primer and probe sequences below are from [Raviv and Kleven, 2009](http://www.bioone.org/doi/10.1637/8469-091508-Reg.1?url_ver=Z39.88-2003&rfr_id=ori:rid:crossref.org&rfr_dat=cr_pub%3dpubmed)

| name | Sequence (5' -> 3') |
|-------|--------|
| Mg fwd | TTG GGT TTA GGG ATT GGGA TT |
| Mg rev | CCA AGGG ATT CAA CCA TCT T |
| Mg probe | *5TexRd-XN*-TGA TGA TCC AAG AAC GTG AAG AAC ACC *BHQ-2* |
| Ms fwd | CTA AAT ACA ATA GCC CAA GGC AA |
| Ms rev | CCT CCT TTC TTA CGG AGT ACA |
| Ms probe | *FAM*-AGC GAT ACA CAA CCG CTT TTA GAA T-*BHQ-1* |


## Cutaneous Leishmaniasis assay

### Lesion swab
For each patient, two sterile swabs (provided by Biomeme) are held together and used to swab the inner border of lesion (encircled 20x).  This will be used for DNA targets (bacteria).  Repeat with two new swabs (20x), and use this second set of swabs for RNA targets (host genes).  

1. Immerse swabs intended for DNA in 1ml of a 1:1 mix of BLB from DNA kit (0.5ml) and water (BEB; 0.5ml), twirl in media for 1 min, discard swabs.
2. Immerse swabs intended for RNA in 1ml of BLB from the RNA kit, twirl in media for 1min, discard swabs
2. Attach standard lab 1cc syringe to Biomeme filter tip. Pump lysate up/down 10x, expel volume
3. Immediately move to **BPW** wash, pump up/down 1x, expel volume
4. Immediately move to **BWB** wash, pump up/down 1x, expel volume
5. Immediately move to **BDW** wash, pump up/down 1x, expel volume
6. Pump air up/down repeatedly 10x, discard syringe but **keep filter tip**
7. attach 25cc or 50cc syringe to the same filter tip.  Pump up and down with air vigorously to dry the column.
8. remove and discard the syringe.  Connect new Biomeme 'slip-tip' 1 cc syringe to the column and draw up 150 ul of Biomeme Elution Buffer (BEB).  Pump up/down 3x with BEB.
9. Expel the elution buffer into a final collection tube.  Typical elution volume is ~120ul.  We use 17ul of this DNA for any of the assays listed below, which means a single eluate is enough for at least 6 QPCR assays.

### Primers and probes

#### Skin-resident microbes 
The primers and probes below are used for detection of *Staphylococcus aureus (Sa)*, *Streptococcus pyogenes (Sp)* and *Leishmania braziliensis (Lb)*

{% include note.html content="All of these targets are DNA, so be sure to use appropirate lysis buffer (BLB from DNA bulk extraction kit) and mastermix (LyoDNA)." %}

* *Leishmania braziliensis* primer/probes are from [Weirather et al., 2011](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3209110/)
* *Streptococcus pyogenes* primer/probes were adapted from CDC [here](https://www.cdc.gov/streplab/protocols.html)
* *Staphylococcus aureus* primers and probes were provided by Biomeme Inc.

| name | Sequence (5' -> 3') |
|-------|--------|
| *Sa* fwd | provided by Biomeme |
| *Sa* rev | provided by Biomeme |
| *Sa* probe | provided by Biomeme |
| *Sp* fwd | GCA CTC GCT ACT ATT TCT TAC CTC AA |
| *Sp* rev | ATT ACT GGT TTC CAA GAC ATT GTG AC |
| *Sp* probe | */56-FAM/*CCG CAA CTC */ZEN/* ATC AAG GAT TTC TGT TAC CA*/3IABkFQ/* |
| *Lb* fwd | TGC TAT AAA ATC GTA CCA CCC GAC A |
| *Lb* rev | AAA TGG CAT ACA GAA ACC CCG TTC |
| *Lb* probe | */56-FAM/*GCC TCT GGG */ZEN/* TAG GGG CGT TCT GCA A*/3IABkFQ/* |


#### Human transcripts
The primers and probes below are for the detection of host transcripts present in cellular material on the swab

{% include note.html content="All of these targets are mRNAs, so be sure to use appropirate lysis buffer (BLB from RNA bulk extraction kit) and mastermix (LyoRNA)." %}

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



{% include links.html %}
