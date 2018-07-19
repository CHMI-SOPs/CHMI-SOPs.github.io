---
title: QPCR assays for avian pathogens on the Biomeme platform
tags: [QPCR, mobile, diagnostics]
keywords:
summary: "Biomeme protocol for detection of Infectious Bronchitis Virus (IBV), Mycoplasma gallisepticum (MG) and Mycoplasma synoviae (MS) from tracheal swabs"
sidebar: mydoc_sidebar
permalink: mydoc_biomeme_avian.html
folder: mydoc
---

## Field extraction of tracheal swabs
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


## Infectious Bronchitis Virus (IBV)

{% include note.html content="IBV is an RNA virus, so be sure to use the appropriate lysis buffer (BLB from RNA bulk extraction kit) and mastermix (LyoRNA)." %}

| name | Sequence (5' -> 3') |
|-------|--------|
| fwd | GCT TTT GAG CCT AGC GTT |
| rev | GCC ATG TTG TCA CTG TCT ATT G |
| probe | *FAM*-CAC CAC CAG AAC CTG TCA CCT C-*BHQ-1* |


## *Mycoplasma gallisepticum* and *Mycoplasma synoviae* (Mg/Ms)

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




{% include links.html %}
