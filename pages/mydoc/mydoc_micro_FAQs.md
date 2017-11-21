---
title: Microbiology FAQs
tags: [getting_started, FAQs, microbiome]
keywords:
summary: "information on our technology, how you gain access, how much experiments cost, and our 'hands-on' philosophy."
sidebar: mydoc_sidebar
permalink: mydoc_micro_FAQs.html
folder: mydoc
---

## What are my options for examining the microbiome?
We use either targeted sequencing of 'marker genes', such as the 16S rRNA gene, or 'shotgun' metagenomics.  Several factors, including experimental goals, timeframe, and available $$ will influence which method you choose.  Marker gene sequencing is relatively inexpensive, can accommodate large numbers of samples (in the hundreds), but takes us some time to turn around and ultimately does not give species- or strain-level resolution of the community. In contrast, metagenomics is more expensive, is typically lower throughput, but we can turn this around much faster and this method can provide a higher resolution view of the community, including functional potential (i.e. gene content). 

## Can I look at any sample type?
Sure, but there are some considerations.  Typically, we handle samples with relatively high microbial biomass (e.g. stool or soil).  If you are interested in profiling the skin microbiome, or environmental surfaces, then you have to consider that you'll be dealing with extremely low biomass.  This means your study design should include extra precautions to control for contamination and artifacts.

## What controls should I consider?
All runs should include the following controls:

* water blank - this is just water from the kit used to extract the DNA.  This controls for any potential nucleic acid contaimination present in your kit reagent.  This ['kitome'](http://blog.mothur.org/2014/11/12/TheKitome/) has been well documented in [this paper](https://bmcbiol.biomedcentral.com/articles/10.1186/s12915-014-0087-z) to be an important issue.

* air blank - not essential with high biomass samples. 

* Mock communities - These are simple community mixtures of known bacteria made in our lab.  We currently offer three mock communities (A, B and C), the composition of which is detailed in the table below. Note that Mock A and B have a relatively even distribution of 11-14 organisms, while Mock C is intentially skewed in composition with the majority of the community comprised of *Akkermansia muciniphila*.  Numbers in the table below indicate relative abundance of DNA add to make each mock community.

| Bacterium                                         | ATCC Strain Designation | MockA  | MockB  | MockC  |
|---------------------------------------------------|-------------------------|--------|--------|--------|
| *Nocardia farcinica*                              | 3308                    | 0.1083 | 0.0714 | 0.0004 |
| *Streptococcus equi ssp equi*                     | 33398                   | 0.0551 | 0.0714 | 0.0006 |
| *Streptococcus agalactiae*                        | 12386                   | 0.1081 | 0.0714 | 0.0006 |
| *Klebsiella pneumoniae*                           | 700695                  | 0.1086 | 0.0714 | 0.0026 |
| *Staphylococcus aureus*                           | 29213                   | 0.1079 | 0.0714 | 0.0023 |
| *Enterococcus faecalis*                           | 29212                   | 0.1095 | 0.0714 | 0.0019 |
| *Staphylococcus schleiferi*                       | 49545                   | 0.1084 | 0.0714 | 0.0037 |
| *Campylobacter jejuni*                            | 33560D                  | 0.0239 | 0.0714 | 0.0010 |
| *Escherichia coli*                                | 43895D                  | 0.1083 | 0.0714 | 0.0253 |
| *Leptospira interrogans*                          | 1198D                   | 0.0406 | 0.0714 | 0.0081 |
| *Bartonella henselae*                             | 49882D                  | 0.1103 | 0.0714 | 0.0245 |
| *Akkermansia muciniphila*                         | BAA-835D-5              | 0.0000 | 0.0714 | 0.8927 |
| *Salmonella typhii* strain 1490                   | NA                      | 0.0000 | 0.0714 | 0.0344 |
| *Mycobacterium avium* subspecies paratuberculosis | NA                      | 0.0000 | 0.0714 | 0.0017 |
| *Staphylococcus schleiferi* strain 2317-03        | NA                      | 0.0000 | 0.0000 | 0.0064 |
| *Mycobacterium species*                           | 19105                   | 0.0111 | 0.0000 | 0.0013 |

## What primer sets do you have for targeted sequencing?
We have the V4 16S primers described by Pat Schloss' lab [here](http://aem.asm.org/content/early/2013/06/17/AEM.01043-13) with enough barcodes to multiplex X samples.  

## Do you offer microbial culture as well?
Not really.  We offer basic culture for common aerobic or facultative anaerobic organisms like *Staphylococcus*, *Streptococcus*, and *E. coli*.  For more involved culture-dependent assays, we work closely with the [PennVet Clinical Microbiology Laboratory](http://www.vet.upenn.edu/veterinary-hospitals/ryan-veterinary-hospital/services/diagnostic-laboratories) and Elliot Freedman at the [PennCHOP anaerobic culture core](https://www.med.upenn.edu/penn-chop-microbiome/microbial-culture-and-metabolomics.html)

## Single-end or paired-end sequencing for the microbiome?
For marker gene sequencing it is not only important that you do paired-end sequencing, but the read length must be such that the paired reads overlap completely (usually 250bp paired-end).  This ensures that you have the highest possible consensus sequence across the amplicon.  Single-end or only partially overlapping paired-end could result in higher degrees of uncorrected sequence error that will appear as true sequence diversity (complicating your determination of community composition).  You can read more about this [here](http://blog.mothur.org/2014/09/11/Why-such-a-large-distance-matrix/). 

For shotgun metagenomics, paired-end is ideal if you think you may want to assemble contigs to recover partial genomes for some of the organisms in your community.  If this is not a major goal, and you primarily care about composition and gene content, then single-end will suffice and will be much less expensive.

## How much will it cost?
The exact costs will depend on your particular experiment, however here are some back-of-the-envelope numbers to help you budget:

* DNA extraction is ~$5/sample
* Library prep for shotgun metagenomics is ~$40/sample
* Library prep for marker gene sequencing is ~$150/plate (about 96 samples). 
* Sequencing run on our NextSeq 500 machine for shotgun metagenomics is ~$4200 for paired-end 150bp, and will generate 400 million read pairs, which is sufficient depth of coverage for about 10-20 samples.  Alternatively, the same number of samples on a single-end 150bp run would cost $2700.
* Sequencing run on a MiSeq for marker gene sequencing would cost about $1200/run and is capable of producing enough reads for hundreds of samples.   

## How long will it take?
Our turn-around time varies, but we typically take 1-2 weeks to go from samples to sequences.  Analysis time depends on your question and interests.

## How do you handle data analysis?
We offer many options for analysis and, ultimately, we will choose an analysis method based on your question, timeline and interest in learning some of the analysis methods yourself.  For rapid turnaround and pathogen detection from shotgun metagenomics data, we have partnered with [CosmosID](http://www.cosmosid.com/) and can deliver data to you within minutes of completeing sequencing for $80/sample.  If this commercial service is not essential for you, or you want a more in-depth analysis of your data, we use Curtis Huttenhower's [BioBakery suite](https://bitbucket.org/biobakery/) of tools or [Sunbeam](https://github.com/eclarke/sunbeam) as a pipeline for analysis of metagenomic data.  We use [QIIME2](https://qiime2.org/) and [Mothur](https://www.mothur.org/) for analysis of marker gene sequencing data.  Finally, we also developed [MicrobiomeDB](http://www.microbiomedb.org) for comparing your data to a large publically available studies.

In addition to the SOPs provided on this site, we have also put together a number of detailed posts on the [lab blog](http://hostmicrobe.org/posts/) that walk you through these types of analyses.  Assistance is also available through 1:1 consultations with CHMI staff.

## So I can just give you my samples then?

No.  CHMI does not operate as a fee-for-service core facility, but rather we function as an interdisciplinary genomics lab.  We teach *you* how to carry out every step involved in marker gene sequencing and shotgun metagenomics.  This makes for a fantastic training experience for students and postdocs, and helps build capacity for labs to be independent with these methods.  Finally, this hands-on approach has the added benefit of keeping costs lower, since you are providing the labor.

## Do I get sequencing reagents from CHMI?

No.  With few exceptions, we encourage labs to order their own consumables.  This cuts down dramatically on how much time we have to devote to invoicing and inventory management.  If you have questions about exactly what you need to order, we are happy to help you navigate that process.

{% include links.html %}
