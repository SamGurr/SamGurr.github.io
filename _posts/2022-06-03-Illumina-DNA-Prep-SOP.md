---
layout: post
title: Illumina DNA Prep SOP
date: '2022-06-03'
categories: Processing
tags: DNA, scallop, Qubit, extractions, OA
---
## **Illumina DNA Prep SOP**

Outlines below is the step by step SOP for the Illumina DNA Prep protocol 

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

* Enhanced PCR Mix (EPM)
* Illumina Index Adapters (i.e. IDT, Nextera, as tubes or plates depending on kit size)
* Nuclease free DI water (UltraPure DI)
* PCR tubes or 96 well plate (with seal(s) such as Microseal 'B')) 
* Thermocycler, vortex
* pipettes, 1-10 ul, 20 - 200 ul

1) Thaw Enhanced PCR Mix (EPM) on cooler rack. Thaw index adapters on 96 well or tube cooler rack depending on kit size

2) Create PCR Master Mix (PMM) as the following: 

n * 1.06 * 20 ul EPM (birefly cnetrifuge before using) + 
n * 1.06 * 20 ul Nuclease free DI water 

 vortex and centrifuge birefly (with mini bechtop centrifuge)
 

3) Place samples on magnetic stand for ~3 minutes until liquid clears and remove and discard the supernatant 

4) Remove samples from the magnetic stand

5) *Immediately* add 40 ul of PMM into the beads. Pipette mix to resuspend 

6) Seal plate/close tube caps and centrifuge for 3 seconds (benchtop centrifuge) 

7) Add index adapters 

* if tubes (24 samples kit) add 5ul of i5 and 5 ul of i7
* if a plate (96 well kit) add the contents of a single well (10 ul) 

8) Pipette mix with a pipette set to 40 ul 10x to mix 

9) Seal plate/close tube caps and centrifuge for 30 seconds (benchtop centrifuge) 

10) Place samples on the thermocycler and run the BLT program for the corresponding input nDNA
* all ranges from 1-<500 are set 
* review the link above for the Illumina BLT program, this is set on the thermocycler under folders 'samgurr/Illumina_DNA_Prep'

### Clean up 

*What you will need:* 

* Illumina Purification Beads (IPB)
* Resuspension Buffer (RSB)
* Freshly made 80% ethanol 
* Nuclease free DI water (UltraPure DI)
* 3-4 sets of PCR tubes or 96 well plates (with seal(s) such as Microseal 'B')) 
* Thermocycler, vortex
* pipettes, 1-10 ul, 20 - 200 ul

Note: while the thermoccler is running, prepare fresh 80% ethanol to accomodate n * 400 ul +(1*n). You will require 400 ul per sample, an added 1 ul per sample to avoid pipette error. 

1) Thaw the Illumina Purification Beads (IPB) and Resuspension Buffer (RSB) to room temperature. 

2) Remove samples from the thermocycler

3) Centrifuge at 280 x g for 1 minute to collect beads at the bottom (I simgply used the benchtop centrifuge when working with PCR tubes and this worked fine) 

4) Place the plate/tubes on the magnetic stand until liquid clears (~ 5 mintues) 

5) Transfer 45 ul of the supernatant from each well/tube to **new** vessels (prelabled PCR tubes or same position on new 96 well plate). Discard previous tubes/plate

6) Vortex/invert the stock IPB to resuspend  

7) Add 40 ul of UltraPure DI (Nuclease free) to each sample (referring to the supernatant in the new tubes/wells)

8) Add 45 ul of IPB (inverted and vortexed the stock prior) to each sample 

7) Pipette mix 10x 

8) Seal plate/close tube caps and incubate on the benchtop at room temperature for 5 minutes 

9) Place samples on magnetic stand for 5 minutes until liquid clears. During this 5 minutes, vortex the IPB stock and add 15 ul to **new** vessles (prelabled PCR tubes or same position on new 96 well plate)

10) After 5 minutes on the magnetic stand, transfer 125 ul of the supernatant to your new vessels (each now with 15 ul of IPB). Remove tubes/plate from magnetic stand and discard them.

11) Pipette mix and incubate at room temperature for 5 mintues 

12) Place samples on the magnetic stand for ~5 minutes until the liquid clears

13) Remove and discard the supernatant

14) Wash 2X as the following: 
 
 a. With the samples **on** the magnetic stand, add 200 ul 80% ethanol **without mixing** 
 b. incubate for 30 seconds at room temperature 
 c. remove the supenatant without disturbing the beads
 
15) Use a 10-20 ul pipette to remove excess ethanol

16) Air dry samples (still **on** the magnetic stand) for 5 minutes 

17) Remove samples from the magnetic stand

18) Add 32 ul RSB to each sample. Pipette mix to resuspend beads.

19) Incubate at room temperature for 2 minutes 

20) Place on magnetic stand for 2 minutes 

21) Transfer 30 ul of supernatant to **new** vessles (prelabled PCR tubes or same position on new 96 well plate)

### **SAFE STOPPING POINT - store at -20C for up to 30 days!**