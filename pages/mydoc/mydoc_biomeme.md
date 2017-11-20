---
title: Portable QPCR
tags: [getting_started, troubleshooting]
keywords:
summary: "Using the Biomeme platform for end-to-end QPCR-based detection of pathogens in the field"
sidebar: mydoc_sidebar
permalink: mydoc_biomeme.html
folder: mydoc
---

## Avian assays

### DNA extraction
All avian assays begin with tracheal swabs collected in brain-heart infusion (BHI) media.  We typically have 11 swabs all stored in a single vial containing 5.5 ml of BHI media.  These swabs could be from multiple birds or from a single bird sampled multiple times, and are assayed fresh or after storage at -80C.  Here's our procotol for rapid, 1 minute DNA extraction using Biomeme reagents:

1. thaw vial containing BHI media and swabs
2. take 100 ul aliquot of sample for DNA extraction
3. add 100 ul sample to 1 ml of Biomeme Lysis Buffer (BLB)
4. with a 1cc syringe affixed to a Biomeme extraction column, push the extraction sample mix up and down 10 times
5. after expelling the volume the 10th time, wash the column by drawing up 500 ul of Biomeme Protein Wash (BPW) 1 time, then expel again.
6. draw up 1 ml of Biomeme Wash Buffer (BWB) and expel volume
7. draw up 1 ml of Biomeme Drying Wash (BDW) and expel volume
8. remove and discard the 1cc syringe, and attach a new 50cc syringe to the same column.  Pump up and down with air vigorously to dry the column.
9. remove and discard the 50cc syringe.  Connect new 1 cc syringe to the column and draw up 125 ul of Biomeme Elution Buffer (BEB).
10. Expel the elution buffer into a final collection tube.  Typical elution volume is 50-70 ul.  We use 5ul of this DNA for any of the assays listed below, which means a single eluate is enough for at least 9-10 QPCR assays.

### Bulk master mix prep
Resuspend bulk lyophilized Biomeme master mix with 135 ul of PCR grade water.  For each reaction you intend to run, mix the following in a single tube, distribute 20ul aliquots to each reaction tube, then add DNA template to each tube

| Reagent | vol (ul) |
|-------|--------|
| fwd primer | 1 |
| rev primer | 1 |
| probe | 1 |
| master mix | 2.5 |
| water | qs to 20 |
| DNA | 5 |


### Infectious Bronchitis Virus (IBV)

| name | Sequence (5' -> 3') |
|-------|--------|
| fwd | GCT TTT GAG CCT AGC GTT |
| rev | GCC ATG TTG TCA CTG TCT ATT G |
| probe | *FAM*-CAC CAC CAG AAC CTG TCA CCT C-*BHQ-1* |


| Temp (C) | Time (min:sec) |
|-------|--------|
| 45 | 10:00 |
| 95 | 10:00 |
| **95** | **0:15** |
| **60** | **1:00** |


### *Mycoplasma gallisepticum* and *Mycoplasma synoviae* (Mg/Ms)

| name | Sequence (5' -> 3') |
|-------|--------|
| MG fwd | TTG GGT TTA GGG ATT GGGA TT |
| MG rev | CCA AGGG ATT CAA CCA TCT T |
| MG probe | *5TexRd-XN*-TGA TGA TCC AAG AAC GTG AAG AAC ACC *BHQ-2* |
| MS fwd | CTA AAT ACA ATA GCC CAA GGC AA |
| MS rev | CCT CCT TTC TTA CGG AGT ACA |
| MS probe | *FAM*-AGC GAT ACA CAA CCG CTT TTA GAA T-*BHQ-1* |

| Temp (C) | Time (min:sec) |
|-------|--------|
| 45 | 10:00 |
| 95 | 10:00 |
| **95** | **0:15** |
| **60** | **1:00** |

{% include links.html %}
