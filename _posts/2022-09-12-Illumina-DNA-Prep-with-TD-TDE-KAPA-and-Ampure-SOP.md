---
title: 'Illumina DNA Prep with KAPA and Ampure SOP'
date: '2022-09-12'
categories:
  - Processing
tags:
  - DNA
  - scallop
  - Qubit
  - extractions
  - OA
---
## **Illumina DNA Prep** <span style="color:red">**with TD, TDE, KAPA and Ampure SOP**</span>

Outlines below is the step by step SOP for Library preparation <span style="color:red">**as 'modified Baym' protocol with reagents used in tagmentation, amplification, and clean up**</span>


#### Illumina DNA protocol [here](https://samgurr.github.io/SamJGurr_Lab_Notebook/Illumina-DNA-Prep-SOP/); this SOP uses reagenets previously included in their library prep kit but is now sold separately [here](https://www.illumina.com/products/by-type/accessory-products/tagment-dna-tde1-enzyme-buffer.html)


Informative links
* protocol:
[ref to DNA prep (although not used here)](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/illumina_prep/illumina-dna-prep-reference-guide-1000000025416-10.pdf)
* product(s): [TDE and TD buffer](https://www.illumina.com/products/by-type/accessory-products/tagment-dna-tde1-enzyme-buffer.html) [current nextera kit](https://www.illumina.com/products/by-type/sequencing-kits/library-prep-kits/nextera-dna-flex.html)

NOTE:
* 'tube/well' will be used throughout for clarity - the protocol can be complete in bulk (i.e 96 well plate) or with PCR tubes when testing or completed small batches


### Before getting started...

### Normalization


*What you will need:*

* DNA (with known concentrations!)
* Permanent marker for labelling
* PCR tubes or 96 well plate (with seal(s) such as Microseal 'B'))
* PCR grade water
* pipettes & pipettors, 1-10 ul; 20-200 ul

1) Quantify your DNA (if not already known) 

2) Recieve your samples (i.e. from -80C) and thaw on the PCR cooler rack

3) Calculate the volume of sample and water to make stock of 2.5 ng/ul

* note: aim for < 250ul as to avod overflowing the wells while simplifying pipetting samples (i.e. if you sample is > 300 g/ul this will require very small volume to acheive 2.5 ng/ul)

4) Label PCR tubes - if in bulk, label a reference 96 well sheet to track sample locations

5) prepare your tubes/wells (pre labeled or a label sheet) wth the DNA diluted, if necessary, with Nuclease free DI (UltraPure DI)


### Tagmentation

*What you will need:*

* Tagment DNA Enzyme (TDE)
* Tagment DNA buffer (TD) 
* PCR tubes or 96 well plate (with seal(s) such as Microseal 'B'))
* Thermocycler, vortex
* pipettes, 1-10 ul

1) Preheat the thermocycler to 55C (should already be programmed as a 'hold' at 55C) 

2) Thaw reagents TDE and TD 

2) Create Tagmentation Master Mix (TMM) as the following:

n * 1.06 * 1.25 ul TD 

n * 1.06 * 0.25 ul TDE

where n is the number of samples

3) Pipette your TMM 10x to mix

4) Distribute 1.5 ul of the TMM to each tube/well

5) Add 1 ul DNA to each tube/well and pipette mix 10x - breifly centrifuge to collect at the bottom

6) Load samples in the thermocycler and hit 'Enter' to continue to incubation process at 55C for 10 minutes followed by 4C hold

* thermocycler program for incubation: 55C hold, 55C for 10 minutes, 4C hold

7) unload KAPA HiFi hotstart ready mix  (at 4C) and index primers (at -20C) and thaw the room temperature 


### Amplification

*What you will need:*

* Sample tubes/plate from previous step
* KAPA HiFi hotstart ready mix
* index primers
* PCR grade water (ie. Ultrapure distilled water)
* sealing flm (if using a plate) 
* Thermal cycler, vortex
* pipettes, 1-10 ul, 20 - 200 ul

1) Thaw KAPA HiFi hotstart ready mix and index primers 

2) Remove the PCR tubes/plate from the thermocycler

3) Start the amplification cycle (details below) so the thermoccler is primed at 72C 'hold' in prep for PCR

4) Add index primers

* indexes as 96 well: these typically contain both indexes combined in each well. Breifly centrifuge the index plate to move sample to the bottom. Add 4.4 ul to each well/tube, note which index plate position (i.e. A4) corresponds with which sample (i.e. sample # 543). Add 4.4 ul of PCR grade water to each tube/well

* indexes as 24 sample (indexes 1 and 2): these smaller kits contain the two indexes to pipette separately. Write in your notes which index combination is planned for which sample ID (i.e. H503 and H710 for sample # 543) . Pipette 4.4ul of each assigned index primer pair (2 indexes per sample, color coded lids for indexes 1 and 2) 

Mixing s not required at this step

5) Prepare a master tube/PCR strip of KAPA HiFi histart readymix as n x 1.06 x 11.25 where n is either the number of samples (small batch tubes) or plate columns (using PCR strip and multichannel pipette). Pipette 11.25 ul of KAPA HiFi histart readymix to each tube/well. Pipette 10x to mix

6) Seal the plate / close caps on PCR tubes

7) Remove the AMPure beads from the 4C fridge to equilibrate to room temperature (in next step)

8) Place samples on the thermocycler and run the modified annealing program by Nina/Harmony for Nextera library prep this is set on the thermocycler under folders 'samgurr/Nextera_SOP'

* 72C hold

* 98C  for 5 minutes

cycle start - repeat for a total of 13 cycles

* 98C for 10 seconds 
* 62C for 30 seconds
* 72C for 30 seconds

cycle end

* 72C for 5 minutes

* 4C hold

9) Prepare 80% ethanol to a volume of n x 1.06 x 300ul 

10) Prepare 10mM pH 8 tris solution to a volume n x 1.06 x 32ul

* note: we have 1M pH 8 tris; 10mM is equivalent to 0.01 M thus your 10mM solution requires 1% 1M tris diluted to the target volume (i.e. target volume = 170ul, you need 1.7 ul of 1M tris)


### PCR cleanup and size selection

*What you will need:*

* AMPure beads, thawed to room temperature
* 80% ethanol 
* 10mM pH 8 tris
* Magnet stand to accomodate your samples (96 well or smaller stand)
* sealing flm (if using a plate) 
* pipettes and pipettors 1-10 ul, 20 - 200 ul
* labelled waste container

1) Remove samples from the thermal cycler 

2) Vortex the thawed AMPure beads and (if using a plate) transfer to a resevoir for the multichannel pipette (skip if not using a plate!) 

3) Pipette 12.94 ul of AMPure beads to each sample, pipette mix 10x to a homogenous color 

4) Incubate samples at room temperature for 5 minutes 

5) Place samples on the magnet stand until the solution clears (~ 1-2 minutes) 

6) Remove and discard the supernatant

9) Wash 2X as the following:

a. Now with the supernatant discarded, remove sampels from the magnetic stand

b. Add 150 ul 80% Ethanol **slowly** onto the beads. Pipette mix, **also slowly**, to resuspend the beads

c. place samples back onto the magnetic stand for minutes until liquid clears

d. Remove and discard the supernatant

9) After two washes completed, remove smaples from the magnetic stand and aadd 32 ul of 10mM tris pH 8 to each sample, beads should be resustpended immediately (at least within 5 minutes to prevent overdrying). 
Pipette mix to resuspend beads.

19) Incubate at room temperature for 5 minutes 

20) Place on magnetic stand for 2 minutes until liquid clears

21) Transfer supernatant to **new** vessles (prelabled PCR tubes or same position on new 96 well plate, or prelabelled tubes for the product and the gel/Qubit check)

### **SAFE STOPPING POINT - store at -20C for up to 30 days!**

* OPTIONAL! Run Qubit dsDNA BR assay and gel electrophoresis to ascertain the quantity and quality of your samples!