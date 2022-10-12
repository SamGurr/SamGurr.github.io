---
title: 'Illumina DNA Prep with KAPA and Ampure SOP'
date: '2022-06-03'
categories:
  - Processing
tags:
  - DNA
  - scallop
  - Qubit
  - extractions
  - OA
---
## **Illumina DNA Prep** <span style="color:red">**with KAPA and Ampure SOP**</span>

Outlines below is the step by step SOP for the Illumina DNA Prep protocol <span style="color:red">**with alternative reagents used in amplification and clean up**</span>


#### View <span style="color:red"> red text</span> where there are changes to the raw Illumina protocol [here](https://samgurr.github.io/SamJGurr_Lab_Notebook/Illumina-DNA-Prep-SOP/)


Informative links
* protocol: [here](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/illumina_prep/illumina-dna-prep-reference-guide-1000000025416-10.pdf)
* product(s): [here](https://www.illumina.com/products/by-type/sequencing-kits/library-prep-kits/nextera-dna-flex.html)

NOTE:
* 'tube/well' will be used throughout for clarity - the protocol can be complete in bulk (i.e 96 well plate) or with PCR tubes when testing or completed small batches


### Before getting started...

* calculate your desired nDNA in the target volume per tube/well (C1V1 = C2V2)
* get your samples (i.e. from -80C) and thaw on the PCR cooler rack
* prepare your tubes/wells (pre labeled or a label sheet) wth the DNA diluted, if necessary, with Nuclease free DI (UltraPure DI)


### Tagmentation

*What you will need:*

* Beaded Linked Transposome (BLT)
* Tagmentation Buffer 1 (TB1)
* PCR tubes or 96 well plate (with seal(s) such as Microseal 'B'))
* Thermocycler, vortex
* pipettes, 1-10 ul

1) Thaw reagents Beaded Linked Transposome (BLT) and Tagmentation Buffer 1 (TB1) to room temperature

2) Create Tagmentation Master Mix (TMM) as the following:

n * 1.06 * 10 ul BLT (vortex vigorsouly before pipetting) +

n * 1.06 * 10 ul TB1

where n is the number of samples

3) Pipette your TMM 10x to mix

4) Place samples (PCR tubes or well) on thermocycler for TAG program
* review the link above for the Illumina TAG program, this is set on the thermocycler under folders 'samgurr/Illumina_DNA_Prep'

### Post Tagmentation Clean Up

*What you will need:*

* Tagmentation Stop Buffer (TSB)
* Tagmentation Wash Buffer (TWB)
* PCR tubes or 96 well plate (with seal(s) such as Microseal 'B'))
* Thermocycler, vortex
* pipettes, 1-10 ul, 20 - 200 ul

1) Thaw Tagmentation Stop Buffer (TSB) and Tagmentation Wash Buffer (TWB) to room temperature

2) Remove the PCR tubes/plate from the thermocycler

3) Add 10 ul TSB to each sample. Pipette to mix & resuspend tthe beads (meaning the BLT beads in solution)

4) Seal the plate / close caps on PCR tubes

5) Place samples on the thermocycler and run the PTC program
* review the link above for the Illumina PTC program, this is set on the thermocycler under folders 'samgurr/Illumina_DNA_Prep'

6) Remove from thermocycler

7) Place samples on a magnetic stand (we have one for plates and for PCR tubes/strips to accomodate bulk library prep and small batches). Wait ~ 3 minutes until liquid clears

8) Remove supernatant and discard
* note: use a chemical storage bottle for all liquid waste, properly labeled with % consituents in this library prep protocol

9) Wash 2X as the following:

a. Now with the supernatant discarded, remove sampels from the magnetic stand

b. Add 100 ul TWB **slowly** onto the beads. Pipette mix, **also slowly**, to resuspend the beads

c. place samples back onto the magnetic stand for ~3 minutes until liquid clears

d. Remove and discard the supernatant

9) After two washes completed, remove smaples from the magnetic stand and add 100 ul TWB **slowly**. Pipette mix, **also slowly**, to resuspend the beads

10) Seal the plate/ close tubes and place on the magnetic stand until Step 4 in *Amplifying Tagmented DNA*

### Amplifying Tagmented DNA

*What you will need:*

* <span style="color:red">KAPA HiFi HotStart ReadyMix 2x </span> (*instead of Enhanced PCR Mix (EPM)!*)
* Illumina Index Adapters (i.e. IDT, Nextera, as tubes or plates depending on kit size)
* Nuclease free DI water (UltraPure DI)
* PCR tubes or 96 well plate (with seal(s) such as Microseal 'B'))
* Thermocycler, vortex
* pipettes, 1-10 ul, 20 - 200 ul

1) Thaw index adapters on 96 well or tube cooler rack depending on kit size

2) Place samples on magnetic stand for ~3 minutes until liquid clears and remove and discard the supernatant

3) Remove samples from the magnetic stand

4) <span style="color:red">*Immediately* Add 11.25 ul of KAPA HiFi HotStart ReadyMix into the beads. </span> Pipette mix to resuspend

6) Seal plate/close tube caps and centrifuge for 3 seconds (benchtop centrifuge)

7) Add index adapters

* if tubes (24 samples kit) add 5ul of i5 and 5 ul of i7
* if a plate (96 well kit) add the contents of a single well (10 ul)

8) Pipette mix with a pipette set to <span style="color:red"> 20 ul </span>  10x to mix

9) Seal plate/close tube caps and centrifuge for 30 seconds (benchtop centrifuge)

10) Place samples on the thermocycler and run the <span style="color:red"> modified annealing program by Nina/Harmony for Nextera library prep </span>
* this is set on the thermocycler under folders 'samgurr/Nextera_SOP'

### Clean up

*What you will need:*

* <span style="color:red"> Ampure XP beads </span> (*instead of Illumina Purification Beads!*)
* <span style="color:red"> 10mM tris pH 8 </span> (*instead of Resuspension Buffer (RSB)!*)
* Freshly made 80% ethanol
* Nuclease free DI water (UltraPure DI)
* 3-4 sets of PCR tubes or 96 well plates (with seal(s) such as Microseal 'B'))
* Thermocycler, vortex
* pipettes, 1-10 ul, 20 - 200 ul

Note: while the thermoccler is running, prepare fresh 80% ethanol to accomodate n * 400 ul +(1*n). You will require 400 ul per sample, an added 1 ul per sample to avoid pipette error.

1) Thaw <span style="color:red"> Ampure XP beads </span> to room temperature. Bring <span style="color:red"> 10mM tris pH 8 </span> to your bench (already stored at room temp).

2) Remove samples from the thermocycler

3) Centrifuge at 280 x g for 1 minute to collect beads at the bottom (I simgply used the benchtop centrifuge when working with PCR tubes and this worked fine)

4) Transfer  <span style="color:red"> 20 ul </span> of the supernatant to **new** vessels (prelabled PCR tubes or same position on new 96 well plate). Discard previous tubes/plate

5) Add <span style="color:red">12.49 ul of Ampure XP beads to each sample. </span> Pipette mix 10x

8) Seal plate/close tube caps and incubate on the benchtop at room temperature for 5 minutes

9) Place samples on magnetic stand for 5 minutes until liquid clears. D

10) Remove and discard the supernatant careful to not discturb the beads

11) Wash 2X as the following:

 a. With the samples **on** the magnetic stand, add 150 ul 80% ethanol **without mixing**

 b. incubate for 30 seconds at room temperature

 c. remove the supenatant without disturbing the beads

15) Use a 10-20 ul pipette to remove excess ethanol

17) Remove samples from the magnetic stand

18) Add <span style="color:red"> 32 ul of 10mM tris pH 8 </span> to each sample, beads should be resustpendided immediately (at least within 5 minutes to prevent overdrying). Pipette mix to resuspend beads.

19) Incubate at room temperature for <span style="color:red"> 5 minutes </span>

20) Place on magnetic stand for 2 minutes until liquid clears

21) Transfer 20 ul of supernatant to **new** vessles (prelabled PCR tubes or same position on new 96 well plate)

### **SAFE STOPPING POINT - store at -20C for up to 30 days!**
