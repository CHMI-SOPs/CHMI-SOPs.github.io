---
title: Depositing RNAseq data to GEO
tags: [bioinformatics, transcriptomics]
keywords:
summary: "This page will walk you through the steps to make your data publicly available so you can meet the requirements for manuscript submission and publication"
sidebar: mydoc_sidebar
permalink: mydoc_RNAseq_depositToGEO.html
folder: mydoc
---

## Intro
So you're ready to submit a manuscript describing your hard work...congratulations!  If you're reading this page, then chances are you have RNAseq data that you want to post to an approved data repository so that you can get an accession number to include in your manuscript submission.  This is the first step in ensuring that the broader research community can access your raw and processed data from any sequencing experiment(s) carried out in your publication.  The [Sequence Read Archive](https://www.ncbi.nlm.nih.gov/sra) (SRA) is the defacto home for all sequencing related studies, but can be confusing to navigate.  Thankfully, the [Gene Expression Omnibus](https://www.ncbi.nlm.nih.gov/geo/), will accept deposits of gene expression profiling data from RNAseq experiments and will pass this data onto to GEO on your behalf.  This is definitely the way to go, since the process of submitting data to GEO is pretty straightforward.  The steps below will walk you through this process.  Be aware that GEO's own instructions are available [here](https://www.ncbi.nlm.nih.gov/geo/info/seq.html), but our instructions are simple.

## What you'll need

* an account on myNCBI.  If you don't already have one, signup [here](https://www.ncbi.nlm.nih.gov/account/)
* the free FTP client, [FileZilla](https://filezilla-project.org/)
* access to your raw .fastq files from your seqeuncing experiment (keep this in the compressed (.gzip) form at all times.
* access to a table of 'processed' gene expression data.  This will need to be either raw counts, or normalized data produced by DESeq2 or EdgeR (or both files).

## Step 1: Complete metadata spreadsheet

This is most time consuming part of whole process, but also the most important.  [Download this example excel file](http://CHMI-sops.github.io/papers/GEOsubmission.xlsx) from one of our own RNAseq studies, and replace with the appropriate information from your own experiment.  This document should describe each sample, how it was handled, and how your samples relate to the raw fastq files.  The more 'metadata' you can include here, the more useful you make this data to outside investigators, so don't skimp on the details.

To complete this form you will need to generate a unique checksum for each file that you intend to transfer to GEO (both fastq files, as well as an process data files).  Checksums confirm that the file is not corrupt.  The are easy to generate, but do require that you open a command line program (e.g. Terminal on a Mac).  Once you have a terminal window open, navigate to the directory on your computer where you have all the files you plan to transfer.  

Use the ```md5``` command followed by the name of your file to generate the 32 character checksum.  You'll want to copy and paste this into your excel submission form.
Here's an example of what this looks like: 

```
md5 GEOsubmission.xlsx 
MD5 (GEOsubmission.xlsx) = 39eae0dbcc54367c588d2815876747f4
```

## Step 2: Preparing to transfer

1. Create a folder anywhere on your computer and give it the same name as your myNCBI username (for me this is 'danielbeiting').
2. Transfer all your raw and processed files, and your metadata spreadsheet completed in step 1, to this folder.
3. If the total size of this folder is >1Tb, you will need to [email GEO](geo@ncbi.nlm.nih.gov) with a list of your file names and their checksums, so that they can manage server space accordingly.


## Step 3: Transfer your data

1. Launch FileZilla and connect to the GEO storage server using the following credentials:

** Host: ftp-private.ncbi.nlm.nih.gov
* username: geo
* password: (this will specific to your myNCBI account)

2. Once connected, simply drag your folder from your local computer to the GEO server

3. Now you must give the crew at GEO a heads-up that you've submitted data to their server.  **Don't skip this step or they will delete your submission.**. [Send an email to GEO](geo@ncbi.nlm.nih.gov), and include the following information in the email:

* Your GEO account username.  If depositing to my account, use 'danielbeiting'
* Names of the directory and files deposited
* Choose a date for public release (this can be immediate, or you can choose up to a maximum of 3yrs.  You can always extend later)

4. Congratulations, you're done!  You will get an email from GEO with your accession number.  Include this number in your manuscript.  If the data is kept private on GEO, but reviewers request a link to access the data (they are entitled to this), you can get a reviewer link through your account on GEO.  If there are any problems with your submission, GEO will contant you and you'll get some instructions on how to resolve the issue before the submission is accepted.

{% include links.html %}
