---
title: RNAseq FAQs
tags: [getting_started, FAQs, RNAseq]
keywords:
summary: "information on our technology, how you gain access, how much experiments cost, and our 'hands-on' philosophy."
sidebar: mydoc_sidebar
permalink: mydoc_RNAseq_FAQs.html
folder: mydoc
---

## What sequencing hardware do you have?

We operate an Illumina NextSeq 500 machine, which is capable of producing reads ranging in length 75-150 bp.  These reads can be produced as single- or paired-end reads (dictated by the reagents, not the hardware).  The machine has two basic operating modes.  In 'mid-output' mode, approximately 130 million reads are produced (or read pairs, if paired-end reagents are used).  In high-output mode, approximately 400 million reads or read pairs are produced.  The total data output depends on library quality and clustering density (more on that below). 

## How 'deep' should I sequence each sample?

This depends on the size of the transcriptome (mammalian vs bacterial), as well as the complexity of the library that is prepared (mRNA vs total transcriptome).  That said, there is no generally accepted rule for depth of sequencing, only a range that has been reported in the literature and which serves as a useful, albeit broad, set of guidelines.  Generally, for RNAseq on mammalian cells or tissues, it would be typical to aim for 20-40 million reads per sample if you were sequencing an mRNA library, or 40-80 million reads/sample for a library with both mRNAs as well as non-coding RNAs.  The added sequencing depth in the later case helps ensure adequate coverage across the more diverse pool of molecules present in your library.  Illumina provides [this tool](https://support.illumina.com/downloads/sequencing_coverage_calculator.html) for estimating the depth required for your organism.  Remember, our machine produces about 400 million reads, so if you sequenced 10 samples on one run, your depth would ideally be about 40 million reads per sample.  For this reason, experiments involving mammalian cells or tissues will generally have 8-12 samples per run on our machine. 

## Single-end or paired-end?

My default answer to this question is almost always to go with single-end.  The reason for recommending this is that it is MUCH cheaper, and numerous studies, like [this one](http://CHMI-sops.github.io/papers/readlength.pdf), have shown that in terms of measuring gene expression, once you go beyond about 50 bp of sequence, very little is gained.  I recommend paired-end data if your reference genome is poor (or non-existent), or if your primary goal is to understand alternative splicing.  In these cases, it is worth spending the extra money.

## How many replicates should I have?

As many as you can reasonably afford.  Seriously.  When it comes to boosting your statistical power to detect differentially expressed genes, you are always better served by increasing group sizes than you are by increasing depth of sequencing.  This has been shown many times in the literaure, such as [here](http://CHMI-sops.github.io/papers/readdepth).  As a general rule, the more variance you expect in your experiment, the more replicates you should try to include.  This means that simple *in vitro* experiments with a homogenous cell line will likely need fewer replicates than would a study of primary cells derived from human subjects.  

## How much will it cost?

Costs vary widely, but are primarily driven by three factors: 1) the number of samples you plan to sequence; 2) the kind of library you will prepare from these samples; and 3) the length and depth of sequencing carried out on these samples.  The costs of consumables direclty from Illumina can be viewed [here](http://CHMI-sops.github.io/papers/Illumina_Pricelist_April2017.pdf)(note the UPenn discount price).  These prices go up each year in April, so take that into account when ordering.  Here is a schematic I prepared that shows the cost of consumables to carry out a few types of RNAseq expeirments.  

## How long will it take?

Once you have isolated high quality RNA from your samples, expect to spend 2 days preparing mRNA or total transcriptome libraries. We QC these libraries in a few minutes using our Agilent tapestation.  Barring any issues in library prep, sequencing can begin almost immediately.  Plan to devote half a day to diluting an denaturing your library, thawing the reagent pack for sequencing and setting up the sequencer.  Each run takes 16-36hrs depending on the type of sequencing being done.  Putting all these steps together and allowing for some amount of troubleshooting and scheduling around other runs, we typically take 1-2wks to get from start to finish.

## Do you analyze the data for us?

Not exactly, though we are fully capable of RNAseq data analysis.  CHMI offers a free [semester-long course](http://DIYtranscriptomics.org) on the bioinformatics associated with RNAseq data analysis.  Assistance is also available through 1:1 consultations with Dan Beiting.

## So I can just give you my samples then?

No.  CHMI does not operate as a fee-for-service core facility, but rather we function as an interdisciplinary genomics lab.  We teach *you* how to carry out every step involved in the RNAseq pipeline.  This makes for a fantastic training experience for students and postdocs, and helps build capacity for labs to be independent with RNAseq.  Finally, this hands-on approach has the added benefit of keeping costs lower, since you are providing the labor.

## Do I get RNAseq reagents from CHMI?

No.  With few exceptions, we encourage labs to order their own consumables.  This cuts down dramatically on how much time we have to devote to invoicing and inventory management.  If you have questions about exactly what you need to order, we are happy to help you navigate that process.

{% include links.html %}
