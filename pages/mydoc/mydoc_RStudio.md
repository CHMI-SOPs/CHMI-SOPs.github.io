---
title: RStudio Server 
tags: [bioinformatics]
keywords:
summary: "How to access RStudio through your web browser"
sidebar: mydoc_sidebar
permalink: mydoc_RStudio.html
folder: mydoc
---

## Accessing the CHMI RStudio Server

Click [**HERE**](http://130.91.255.137:8787) to access our RStudio server directly in your web browser.  

Login with the same credentials you use to access the linux machine.  Feel free to customize your RStudio server by installing any packages needed for your work.

As much as possible, we use R for managing, analyzing and plotting data.  This preference is largely motivated by the excellent community support for R, the exceptional RStudio interface for interacting with R, and the growing number of bioinformatics tools within the [bioconductor](https://www.bioconductor.org/) suite of applications.

Although we frequently use RStudio on our personal computers, it is useful to have access to a server version of RStudio, particularly when your work requires more computing power.  If you have an account on our Linux cluster, then you already have access to RStudio, without having to install any additional software.  

## Installing R packages for RStudio Server

Once you've logged into an RStudio Server session, your browser window will look pretty much indistinguishable from the stand-alone RStudio application you're already familiar with.  One minor but important difference is that your package library can now include R packages in the System Library (available to all users on the server), as well as your User Library (available only to you).  By default, any new packages you install will be located in your User Library.  If you want to install a package in the System Library so that it is available to all users, then you will need to enter R's shell as root.  To do this, navigate to the terminal window in RStudio and type:

```shell
sudo -i R
```

Once in R's shell, you would install the package directly from the command prompt in the terminal window using

```shell
install.packages('packageName')
```


{% include links.html %}

