---
title: CHMI linux cluster
tags: [bioinformatics]
keywords:
summary: "CHMI maintains a custom configured compute server that runs Linux Ubuntu 18.04 LTS.  This machine has two 6-core Intel Xeon E5-2643v4 CPUs (12 cores total), 512 Gb of RAM and 18Tb of RAID1 storage.  If you are a PennVet lab and wish to use this machine, please contact Dan Beiting (beiting@upenn.edu) for more information."
sidebar: mydoc_sidebar
permalink: mydoc_linux.html
folder: mydoc
---

## General rules
Use of the cluster is free-of-charge to approved labs.  However, to protect the cluster from abuse and prevent issues with storage, we have a few rules all users must follow.  Failure to adhere to these rules will result in a warning. Additional rule violations will result in suspension of your account.  Here are the rules:

* We will set-up your account and install any software you may need.  Please do not install software yourself.
* In addition to your home account which is located at ```/home/username``` on the server, you will also be given a data folder that is located on ```/data/username```.  All data must be stored in this directory **not** your ```/home/username``` folder.
* Data storage space is limited (18Tb goes quickly!), so we periodically montior storage space and may request that data not currently in use be moved off the cluster.
* We require a strong password for each account.  We will set this password for you, and ask that you do not change it.

## Creating and managing user accounts (CHMI only)

### Add a new user
First, add a new user to the home directory
```
sudo adduser [username] 
```
Then give the new user sudo priveleges
```
usermod -aG sudo username 
```
### Delete a user
```
sudo deluser --remove-home [username]
```

## Installing software (CHMI only)
* All software *must* be installed only in ```/usr/local/bin/```
* Once installed, you'll need to add the path to the executable to your PATH variable. To do this, open the system profile (a text document, so it can be opened with either the nano or vim text editors, both of which are built into the linux system)
```
sudo nano /etc/profile
```
* scroll to the bottom of the ```/etc/profile``` file and add the path to the new software.  For example, if you had downloaded the program kallisto, you would add ```export PATH=$PATH:/usr/local/bin/kallisto``` to the bottom of the ```/etc/profile``` document.
* now your program will be available to any user, regardless of the directory in which they are working.  Changes to ```/etc/profile``` may not take effect until you start a new session.

## Connecting to the Linux server

```
ssh username@130.91.255.137
#you'll be prompted to enter your password and then you'll be connected
#once connected you'll see a new prompt with username@ubuntu1604
```

## command line tips
If you're new to the command-line in Linux, there are lots of online resoures for learning, but here are a few of the commands that will help you move around and carry out basic tasks.  Note that many of these may only work if run as ```sudo```.

| typing this at the prompt                                   | does this                                                                                   |
|-------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| ```tar -xvzf <fileName.tar.gz>```                           | unzip a .tar file                                                                           |
| ```ls -l```                                                 | list all files and folders in your working diretory with info on permissions                |
| ```du -a -h --max-depth=1 | sort -hr```                     | lists all files and folders in your working directory sorted by size                        |
| ```du -sh *```                                              | simpler version of the command above. lists all files in a folder and shows their file size |
| ```ls -l | wc -l```                                         | counts files in a directory                                                                 |
| ```tree -d```                                               | lists all files and folders in your working directory as a tree structure                   |
| pressing up arrow                                           | recalls previous command                                                                    |
| ```cd /```                                                  | takes you to the root directory                                                             |
| ```cd ~```                                                  | takes you to your home directory                                                            |
| ```cd ..```                                                 | takes you up one level in your file directory                                               |
| ```cd ../..```                                                 | takes you up two levels in your file directory                                               |
| ```chmod u+x <fileName>```                                  | edits permissions on file                                                                   |
| ```chown <yourUserName> <fileName>```                       | makes you the owner of a file                                                               |
| ```chgrp <yourUserName> <fileName>```                       | assigns you as the group for the file                                                       |
| ```rm -rf <directoryName>```                                | removes a folder and all of its contents                                                    |
| ```wget <URLtoFile>```                                      | downloads a file from a website                                                             |
| ```defaults write com.apple.finder AppleShowAllFiles YES``` | show all hidden files in the finder (Mac only)                                              |



{% include links.html %}

