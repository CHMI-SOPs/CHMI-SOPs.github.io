---
title: Single Cell RNAseq – encapsulation
tags: [transcriptomics, single_cell_genomics]
keywords: transcriptomics
summary: "Using the 10X Chromium Controller to encapsulate individual cells for single cell genomic experiments"
sidebar: mydoc_sidebar
permalink: mydoc_10X_prep.html
folder: mydoc
---

# Day 1

## Documentation
We use the [10X Chromium Controller platform](https://assets.ctfassets.net/an68im79xiti/1eX2FPdpeCgnCJtw4fj9Hx/7cb84edaa9eca04b607f9193162994de/CG000204_ChromiumNextGEMSingleCell3_v3.1_Rev_D.pdf) to encapsulate and barcode single cells. The following protocol describes the steps for single cell mRNA-seq, but the platform is capable of other analyses including cell surface protein expression, ATAC-seq, dual RNAseq/ATACseq, and Spatial Transcriptomics on intact tissue sections. Refer to the corresponding protocols for these and ensure you are using the appropriate protocol and reagents for your experiment.

## What you'll need
{% include important.html content="Our machine is only compatible with v3.1 Next GEM reagents.  Earlier versions of kits/reagents will not be compatible" %}

### 10X reagents (included):
* Chromium Next GEM Single Cell 3ʹ GEM, Library & Gel Bead Kit v3.1 (2 boxes in -20C Freezer and 1 box in -80C Freezer)
* Chromium Next GEM Chip G Single Cell Kit (Room Temp)
* Single Index Kit T Set A (-20C Freezer)

### Not included in the 10X kits:
* Cell Suspension (See following Instructions)
* 50% glycerol solution (Room Temp)
* Nuclease-free water (Room Temp)
* 10% Tween 20 (Room Temp)
* Buffer EB (Room Temp)
* SPRI Select Reagent (Room Temp)

## Cell Preparation 

The optimal input cell concentration is 700-1,200 cells/µl. Depending on your concentration, you will need 2.1-23.6 uL of cell suspension as input for each sample. Refer to the Cell Suspension Volume Calculator Table on the next page of this protocol. 

While a high concentration of cells is desirable, it also increases the rate of 'multiplets'. Multiplets occur when a single oil droplet contains 1 barcoded bead and two or more cells. Since each bead has a single barcode, transcripts from multiplets will appear as though they are from the same cell. 10X Genomics recommends 700-1,200 cells/µl in order to maximize cell encapsulation while avoiding excessive multiplets. 

For more detail on cell preparation, refer to 10X’s literature, which covers:

* [General preparation for limited samples](https://support.10xgenomics.com/single-cell-gene-expression/sample-prep/doc/demonstrated-protocol-single-cell-protocols-cell-preparation-guide)

* [Preparation from cultured cell lines](https://support.10xgenomics.com/single-cell-gene-expression/sample-prep/doc/demonstrated-protocol-single-cell-suspensions-from-cultured-cell-lines-for-single-cell-rna-sequencing)
 
* [General workflow](https://assets.ctfassets.net/an68im79xiti/2Sd6Fyx0YMqCC4m2uocS2u/9d9f785740ba0a1f34133de45db5115e/CG000126_Cell_counting_flowchart_RevA.pdf)

* [Other details](https://support.10xgenomics.com/single-cell-gene-expression/sample-prep).




{% include links.html %}
