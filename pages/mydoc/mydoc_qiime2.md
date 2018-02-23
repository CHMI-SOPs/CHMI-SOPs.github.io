---
title: QIIME2 workflow
tags: [bioinformatics, microbiome]
keywords:
summary: "Using the Quantitative Insights Into Microbial Ecology (QIIME2) software pipeline for analysis of marker gene-based microbiome sequencing data"
sidebar: mydoc_sidebar
permalink: mydoc_qiime2.html
folder: mydoc
---

## before starting
This protocol is shorthand 


## Step 1: Connect to a CHMI linux cluster

{% include important.html content="if you do not have an account on our cluster and would like to get one, please contact Dan Beiting" %}

```
ssh username@130.91.255.137
```

## Step 2: prepare your metadata

Before you get started, there are a few basic QIIME commands that you will want to get familiar with

```
#take a look at all the plugins you have available to you through QIIME
qiime tools

#documentation for any QIIME function ca be accessed by appending --help at the end of any command
```

Metadata is information about your samples (e.g. date collected, patient age, sex, pH, etc).  This information should be contained within a single spreadsheet that has samples as rows and variables as columns.

In order to use QIIME, you **must** have your mapping spreadsheet correctly formatted.  Set this file up as a google sheet, using [this example]().  In order to check whether your file is correctly formatted, use the [Keemei plugin](keemei.qiime2.org) for google sheets.  Once Keemei says your spreadsheet is correctly formatted for QIIME2, you're ready to proceed. 

Create a .txt version of your metadata spreadsheet and save in your working directory on a computer with QIIME2 installed.  You can then inspect further if you want using:

```
qiime tools inspect-metadata [filename]
```


Create a visualiation of your metadata on the QIIME2 viewer (.qzv is a qiime zipped visualization)
```
qiime metadata tabulate --m-input-file sample-metadata.tsv --o-visualization tabulated-metadata.qzv
```

navigate to [QIIME2 viewer](https://view.qiime2.org/) in browser to view this visualization


## Step 3: prepare your raw data

There are a number of ways you may have your raw data structured, depending on sequencing platform (e.g., Illumina vs Ion Torrent) and sequencing approach (e.g., single-end vs paired-end), and any pre-processing steps that have been performed by sequenencing facilities (e.g., joined paired ends, barcodes in fastq header, etc).  Check out the [QIIME info page](https://docs.qiime2.org/2018.2/tutorials/importing/)

Move your fastq files and your barcode file (if data is not already demultiplexed) to your working directory

create an artifact of your data
```
qiime tools import \
  --type EMPSingleEndSequences \
  --input-path emp-single-end-sequences \
  --output-path emp-single-end-sequences.qza
```
 
Check this artifact to make sure that QIIME now recognizes your data (.qza is a qiime zipped artifact)

```
qiime tools peek emp-single-end-sequences.qza
```

{% include important.html content="the .qza and .qzv files can be unpacked using the unix command  ```unzip``` or the qiime commands ```qiime tools extract``` or ```qiime tools export```.  These unpacked files can then be used in other settings (R, perl, etc).  In other words, the QIIME concept of an 'artifact' does not permanently alter the structure of your data." %}

## Step 4: demultiplexing

{% include note.html content="If you data is already demultiplexed, you can skip this step. For paired data you would use qiime demux emp-paired in the code snipet below to produce a demux.qza file" %}

```
qiime demux emp-single \
  --i-seqs emp-single-end-sequences.qza \
  --m-barcodes-file sample-metadata.tsv \
  --m-barcodes-column BarcodeSequence \
  --o-per-sample-sequences demux.qza
```


{% include note.html content="If you ran qiime tools extract on the demux.qza, you would have all your demultiplexed per-sample fastq files, if you wanted these for other fun stuff" %}

Now produce a visualization of the demux'ing.  This will produce a file called *demux.qza*, which can be viewed on the [QIIME2 viewer](https://view.qiime2.org/) as you did earlier for your metadata.qzv file

```
qiime demux summarize \
  --i-data demux.qza \
  --o-visualization demux.qzv
```

## Step 5: Denoising and QC filtering

BLURB ABOUT OTU AND denoising.  One method for denoising is to use DADA2.  You can learn more about this method by checking out the Nature Methods paper, and the online methods section for more indepth (but still very readable) description of the statistical methods [here]()

{% include important.html content="DADA2 denoising will join paired reads for you.  Do not join your reads prior to running DADA2, since the program has a model for the basewise error of illumina reads, and joining reads would violate the expectations of that model.  If you're working with single-end data, you would use 'denoise-single' in the code below." %}

{% include important.html content="If you have multiple runs, it is recommended that you run DADA2 separately on data from each run individually, then combine data from the runs after denoising.  See the [QIIME2 fecal transplant tutorial](https://docs.qiime2.org/2018.2/tutorials/fmt/) for an example of how this works" %}

{% include note.html content="we will trim our sequences to 120bp.  This number is a bit arbritrary but should be guided on quality scores that you observed in demux.qzv in step 4 above.  If you want to avoid trimming for any reason (for example, if you are profiling fungi by ITS sequencing), simply set this value to 0." %}

```
qiime dada2 denoise-paired \
  --i-demultiplexed-seqs demux.qza \
  --p-trim-left 0 \
  --p-trunc-len 120 \
  --o-representative-sequences rep-seqs-dada2.qza \
  --o-table table-dada2.qza
```


Now you'll summarize your filtered/denoised data using the ```qiime feature table``` function.  

```
qiime feature-table summarize \
  --i-table table.qza \
  --o-visualization table.qzv \
  --m-sample-metadata-file sample-metadata.tsv
qiime feature-table tabulate-seqs \
  --i-data rep-seqs.qza \
  --o-visualization rep-seqs.qzv
```


The code above produced two .qzv files that can be explored on the qiime2 viewer.  The "interactive Sample Detail" tab of the viewer gives you a great way to explore how rarefaction depths (subsampling) will impact your data (i.e. which samples will be dropped).

Once you're confortable with the individual steps of this workflow, you could use [this shell script](), to run the entire workflow 


## Step 6: build a phylogenetic tree

{% include important.html content="tree construction is optional, and is useful downstream if you want to compute alpha diversity metrics that are phylogenetically based.  The resulting tree is unrooted and is created using Fasttree.  Some downstream actions will require a rooted tree, in which longest branch is used to root the tree ('midrooting')" %}

{% include warning.html content="You are cautioned against drawing strong conclusions about relationships between taxa from this tree alone, since it was only constructed using a single marker gene." %}

```
#carry out a multiple seqeunce alignment using Mafft
 qiime alignment mafft \
  --i-sequences rep-seqs.qza \
  --o-alignment aligned-rep-seqs.qza

#mask (or filter) the alignment to remove positions that are highly variable. These positions are generally considered to add noise to a resulting phylogenetic tree.
qiime alignment mask \
  --i-alignment aligned-rep-seqs.qza \
  --o-masked-alignment masked-aligned-rep-seqs.qza

#create the tree using the Fasttree program
qiime phylogeny fasttree \
  --i-alignment masked-aligned-rep-seqs.qza \
  --o-tree unrooted-tree.qza

#root the tree using the longest root
qiime phylogeny midpoint-root \
  --i-tree unrooted-tree.qza \
  --o-rooted-tree rooted-tree.qza

```

## Step 6: alpha rarefaction

Produce a graphic that shows the impact of rarefaction (sampling at different depths) on alpha diversity of each sample.  These are also called 'collectors curves'.

```
qiime diversity alpha-rarefaction \
  --i-table table.qza \
  --i-phylogeny rooted-tree.qza \
  --p-max-depth 4000 \
  --m-metadata-file sample-metadata.tsv \
  --o-visualization alpha-rarefaction.qzv
```

{% include note.html content="A few comments on interpreting alpha diversity metrics: it is important to understand that certain metrics are stricly qualitative (presence/absence), that is they only take diversity into account, often referred to as *richness* of the community (e.g. observed otus).  In contrast, other methods are quantitative in that they consider both *richness* and abundance across samples, commonly referred to as *evenness* (e.g. Shannon).  Yet other methods take phylogenetic distance into account by asking how diverse the phylogenetic tree is for each sample.  These phylogenetic tree-based methods include the popular Faith's PD, which calculates the sum of the branch length covered by a sample" %}


## Step 7: calculate and explore diversity metrics

Use QIIME2's ```diversity core-metrics-phylogenetic``` function to calculate a whole bunch of diversity metrics all at once.  Note that you should input a sample-depth value (set at 1109 reads in the example below) based on the alpha-rarefaction analysis that you ran in step 6.

```
qiime diversity core-metrics-phylogenetic \
  --i-phylogeny rooted-tree.qza \
  --i-table table.qza \
  --p-sampling-depth 1109 \
  --m-metadata-file sample-metadata.tsv \
  --output-dir core-metrics-results
```

Now test for relationships between **alpha diversity** and study metadata and create .qzv files to view these relationships on QIIME2 viewer
```
qiime diversity alpha-group-significance \
  --i-alpha-diversity core-metrics-results/faith_pd_vector.qza \
  --m-metadata-file sample-metadata.tsv \
  --o-visualization core-metrics-results/faith-pd-group-significance.qzv

qiime diversity alpha-group-significance \
  --i-alpha-diversity core-metrics-results/evenness_vector.qza \
  --m-metadata-file sample-metadata.tsv \
  --o-visualization core-metrics-results/evenness-group-significance.qzv
```

Now test for relationships between **beta diversity** and study metadata and create .qzv files to view these relationships on QIIME2 viewer

{% include note.html content="Like alpha diversity discussed above, beta diversity metrics can also be either qualitative or quantitative.  Qualitative measure only consider whether a given taxon is present (yes/no) in both samples from any given airwise comparison (e.g. Jaccard distance).  Quantitative measures are *weighted* by taxon abundance (e.g. Bray-Curtis).  Phylogenetic beta diversity metrics can also be qualitiative (unweighted) or quantitative (weighted).  Weighted Unifrac and unweighted Unifrac are examples of quantitative and qualitiative phylogenetic-based metrics, respectively." %}

```
qiime diversity beta-group-significance \
  --i-distance-matrix core-metrics-results/unweighted_unifrac_distance_matrix.qza \
  --m-metadata-file sample-metadata.tsv \
  --m-metadata-column BodySite \
  --o-visualization core-metrics-results/unweighted-unifrac-body-site-significance.qzv \
  --p-pairwise

qiime diversity beta-group-significance \
  --i-distance-matrix core-metrics-results/unweighted_unifrac_distance_matrix.qza \
  --m-metadata-file sample-metadata.tsv \
  --m-metadata-column Subject \
  --o-visualization core-metrics-results/unweighted-unifrac-subject-group-significance.qzv \
  --p-pairwise
```

Create a PCoA plot to explore beta diversity metric.  To do this you can use [Emperor](https://biocore.github.io/emperor/build/html/index.html), a powerful tool for interactively exploring scatter plots.  You do not need to install Emperor.

{% include note.html content="notice that the custom-axes parameter in the code below can be used to specific any column from your metadata file that you'd like to stratify you PCoA plot by." %}

```
#first, use the unweighted unifrac data as input
qiime emperor plot \
  --i-pcoa core-metrics-results/unweighted_unifrac_pcoa_results.qza \
  --m-metadata-file sample-metadata.tsv \
  --p-custom-axes DaysSinceExperimentStart \
  --o-visualization core-metrics-results/unweighted-unifrac-emperor-DaysSinceExperimentStart.qzv

#now repeat with bray curtis
qiime emperor plot \
  --i-pcoa core-metrics-results/bray_curtis_pcoa_results.qza \
  --m-metadata-file sample-metadata.tsv \
  --p-custom-axes DaysSinceExperimentStart \
  --o-visualization core-metrics-results/bray-curtis-emperor-DaysSinceExperimentStart.qzv
```


## Step 8: assign taxonomy

In this step, you will take the denoised sequences from step 5 (rep-seqs.qza) and assign taxonomy to each sequence (phylum -> class -> ...genus -> ).  This step requires that you either [train your own classifier](https://docs.qiime2.org/2018.2/tutorials/feature-classifier/) using the [q2-feature-classifier](https://peerj.com/preprints/3208/)  

We'll use a classifier that has been pretrained on [GreenGenes](http://greengenes.secondgenome.com/) database with 99% OTUs.  Download this classifier from the qiime site and place in your working directory.

```
wget -O "gg-13-8-99-515-806-nb-classifier.qza" "https://data.qiime2.org/2018.2/common/gg-13-8-99-515-806-nb-classifier.qza"
```


Now you're ready to assign taxonomy to your sequences

```
qiime feature-classifier classify-sklearn \
  --i-classifier gg-13-8-99-515-806-nb-classifier.qza \
  --i-reads rep-seqs.qza \
  --o-classification taxonomy.qza

qiime metadata tabulate \
  --m-input-file taxonomy.qza \
  --o-visualization taxonomy.qzv
```

Now create a visualization of the classified sequences.  Again, the resulting .qzv file produced below can be explored in the [QIIME2 viewer](https://view.qiime2.org/)

```
qiime taxa barplot \
  --i-table table.qza \
  --i-taxonomy taxonomy.qza \
  --m-metadata-file sample-metadata.tsv \
  --o-visualization taxa-bar-plots.qzv
```



{% include links.html %}



