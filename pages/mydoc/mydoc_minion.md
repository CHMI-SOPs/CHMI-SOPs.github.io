---
title: Oxford Nanopore MinION portable sequencer
tags: [mobile, diagnostics]
keywords:
summary: "The MinION sequencer from Oxford Nanopore Technologies (ONT) is a remarkably small sequencer capable long-reads and substatial sequencing output from either RNA or DNA."
sidebar: mydoc_sidebar
permalink: mydoc_minion.html
folder: mydoc
---

## Device setup
Begin by connecting one minION sequencer to a [MinIT device](https://nanoporetech.com/products/minit) using the supplied cable.  MinIT is a portable, GPU-based computer that is pre-configured with the MinKNOW software that controls the MinION, carries out data acquisition and performs basecalling. Plug the MinIT into a standard 120V outlet.  You should see lights illuminated on both the MinION and MinIT (no need to power on either device).  Take note of the ID number on the bottom of the minIT, directly under the QR code.  You're going to need this ID# to connect the minIT to an iPad.

We use an iPad mini as a monitor to interact with and control control our minION devices.  Open the iPad, navigate to settings and choose Wifi.  Look for the MinIT ID number in the list of available networks, and connect.  You'll be asked for a password.  Enter 'WarmButterflyWings98' (case sensitive).

Open a browser on the iPad and navigate to [MinIT ID#].local (e.g. mt-110472.local).  You should now be looking at the minKNOW control software interface directly in the iPad browser.

There are several different LED lights that can illuminate on the MinIT.  

| Light | Indication |
|----------|----------------|
| White       | device is powered          |
| Blue       | Wi-Fi is enabled         |
| Green   | Wi-Fi is connected      |
| Red   | Wi-Fi connection failed       |

## Flow cell check


{% include links.html %}
