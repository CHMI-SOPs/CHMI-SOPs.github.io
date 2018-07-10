---
title: Single Cell RNAseq library prep
tags: [library_prep, transcriptomics]
keywords: transcriptomics, library preparation
summary: "Using droplet-based technology to barcode individual cells for RNAseq"
sidebar: mydoc_sidebar
permalink: mydoc_scRNAseq.html
folder: mydoc
---
# Day 1

## Documentation

We use the [InDrop platform from 1CellBio](https://1cell-bio.com/indrop/) to isolate and barcode single cells.  This technology was initialy described in [this Cell paper]().  The steps on this page are derived from 1CellBio's [protocol for encapsulating single cells](https://1cell-bio.com/wp-content/uploads/2018/05/inDrop-Single-Cell-Encapsulation-and-Rever-se-Transcription-Protocol-Version-2.2-.pdf)

## What you'll need

{% include important.html content="The following items are included in the InDrop kit" %}

* Barcoded Hydrogel Microspheres - 500,000 beads provided in 500ul (4C)
* 1.3x RT Premix (-20C)
* 2x Gel Concentration buffer (-20C)
* Wash buffer (RT)
* OptiPrep - density matching agent (RT)
* Demulsifying agent - for breaking droplets (RT)
* Separate assemblies for loading beads, oil, cells and RT mix

{% include important.html content="The following items are __not included__ and may need to be purchased by the individual user" %}

* SuperScript III enzyme
* 1CellBio UV box (we provide this)
* RNAase ZAP spray (recommended by the company...not essential)
* 1.5ml LoBind EpTubes
* Chilling block (stored at 4deg; used for keeping samples and beads chilled while on the InDrop machine).
* Gel loading pipette tips

## A few important comments before you start

## Instrument set-up

* Log into the laptop provided by 1CellBio – the login password is “inDrop” – and Click desktop icon labeled “Thor”. This opens the software that controls the instrument and implements the inDrop process. 

* Remove the syringe and loading assembly from the 'beads' package. This syringe is shipped pre-filled with hydraulic fluid specific to the loading the hydrogel beads.  Remove cap on syringe, attach tubing and manually expel syringe volume until it is near the end of the tubing.  Secure assembly into the appropriately labeleld automatic pump on the InDrop.

* Repeat the above step for each syringe assembly

* Syringes can remain on the machine for 2 weeks and can be used for multiple experiments

* On the first tab of Thor software, click “Set Up”.  Input the total number of cells you want encapsulate, the concentration of the cell solution, and the desired Bead-to-cell ratio.  Pressing "calculate" will populate the boxes below with the amount, in microliters, of reagents needed to be prepped. Clicking on the “?” gives the recipe of the RT/Lysis Mixture to be made.

* Prepare microchip devices by following the [Chip Silanizing protocol](https://1cell-bio.com/wp-content/uploads/2017/10/Silanization-Protocol-v4.pdf).  Silanization is only good for a few hours, so if you use 1 device on the chip, you will need to repeat the silanization protocol when you use the other devices on the chip.

* Click "next" on the Thor software to move forward to bead preparation

## Prepare beads

{% include warning.html content="The polyT oligos on each bead have a UV-cleavable linker.  Avoid direct exposure of beads to UV light by wrapping in foil." %}

{% include important.html content="The beads are very porous, particularly when they are resuspended in wash buffer, which makes them hard to see even when pelleted.  If you're worried about losing beads during washing, be sure to save your supernatants." %}

* Concentrate beads in the stock, 1.5 mL tube by spinning at 5000 g for 2 min in a 1.5ml LoBind Ependorf tube.

* If you want to prep all the beads in the kit (enough for encapsulating about 30,000 cells).  Reach down into the pelleted beads with your pipet tip and draw up 250 ul of the pellet (should be almost all of it), leaving behind the supe (storage buffer).  

* Transfer this bead volume to a 1.5ml LoBind Tube, and add 1ml Wash Buffer.  This buffer will cause the beads to swell, making them more porous and even harder to see.  Spin at 1000g for 1min, remove supe. 

* Repeat this washing, at least 2-3 more times.

* After the last wash, draw off a volume of Wash Buffer to leave about 500ul of beads/buffer left in the tube.  To this volume, add 500ul of the 2x Concentration Buffer.  

* Spin at 5000xg for 1min.  The concentraiton buffer added in the previous step will cause the beads to shrink back down a bit, resulting in a smaller pellet. 

* Draw off as much supe as possible (using a gel loading tip is helpful here), spin again at 5000xg if necessary to draw off more supe.

{% include important.html content="It's essential that you remove all the supe at this step.  Residual supe will make the packed bead suspension more soupy and prevent the beads from forming a dense pack on the device." %}

* Prime the bead pump to make sure the line is cleared of air.  You should see small droplets of fluid coming out of the tubing (just dab on a kimwipe).  If the line contains lots of air, you can use the Thor software to crank up the priming flow rate to speed the process.

* After priming, immerse the end of the tubing into your packed bead pellet and parafilm the top to hold the tubing in place.  

* Use Thor to begin loading your desired bead volume.  

{% include important.html content="It's important that you not introduce air into the line during the bead loading.  To prevent this, check at about 1/2 way through the loading to be sure the tip is still immersed in the packed beads.  Then continue to check every minute for the remainder of the bead loading process." %}

* Once loading is complete, resuspend residual beads in new storage buffer and return to storage.  These can be used for future experiments.  In addition, supe saved from the bead prep process can be spun down at 5000xg to pellet residual beads for resuspension and storage.

## Cell encapsulation

* With beads loaded onto the InDrop, you are now ready to prepare your cells.

* Resuspend cells at 80-100K/ml in cold PBS supplemented with 18% OptiPrep (this is a density matching gradient; included in the kit from 1CellBio).  You will only need < 1ml final volume of cells at this concentration.

* Prepare the calculated amount of RT/Lysis mixture. Click on the “?” in the Thor software to see the breakdown of the RT/Lysis mixture will be given.  Prepare 10% extra volume for RT mix, and add excess cell volume as well.  This will prevent air from being drawn up into the lines during loading.

* Collect droplets into a 1.5ml LoBind tube containing 200ul mineral oil.

## In-droplet 1st strand cDNA reaction

* Immediately following droplet collection, place the 1.5ml LoBind tube containing droplets into a the 1CellBio UV box for 10 sec.  This cleaves the oligos off the bead, allowing you to carry out a cDNA reaction in solution.

* Immediately incubate tube in a heatblock at 50degC for 2hr.  This is your 1st strand cDNA reaction.

* Incubate at 70degC for 15min to heat kill the reaction

* Use a gel loading pipette tip to remove as much of the mineral oil (clear) on  top of the bead emulsion layer (white).  Avoid removing any of the bead emulsion, since each droplet contains a cell.  Under the bead emulsion is residual droplet oil, which you can ignore.  

{% include important.html content="At this point, if you had collected > 3000 cells, you can divide your emulsion into equal parts for downstream steps.  For example, if you collected 9000 cells, divide into 3 equal parts.  35ul of emulsion typically contains about 1000 barcoded cells." %}

* Break up droplets by adding an equal volume of demulsifier (1CellBio kit) to your tubes (just eyeball the volume of bead emulsion in the tube and add equal vol of demulsifier).

* Vortex for 5 seconds and spin at 1000xg for 1min.  Your sample should now appear clear.  If not, repeat the demulsifer step.

* Your sample can now be stored at -80C for up to 3 months.  

## Instrument clean-up
 
* For the cells and RT mix pumps, dispense until remaining fluid is ejected and red hydrolic fluid is at the end of the tip again.

* Once cells and RT are cleared from the tips, use the 'withdraw colored oil' function in the Thor software to pull the hydrolic fluid back into tubing and clear the tips.  Remove tips and discard.

* Dispense beads into a LoBind tube.  Resuspend 1:1 with storage buffer and store protected from light at 4C.

* Close software and turn off microscope.

* Store microfluidic chip at RT, with the unused devices covered with the protective tape.  Be sure to use a pen to mark which device(s) has been used. 

# Day 2

## Library prep


{% include links.html %}
