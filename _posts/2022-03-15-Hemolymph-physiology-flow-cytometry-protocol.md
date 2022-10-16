---
layout: post
title: Hemolymph physiology flow cytometry protocol
date: '2022-03-15'
categories: protocol
tags: hemolymph C6_plus oyster JC-10 DCFHDA SYBR_green
---

# Hemocyte Physiology and Flow Cytometer Protocol
Samuel Gurr and Meghana Parikh  

## Equipment/Station Prep - Day Prior

* Mass Culture Room (MCR)- Hemolymph sampling and probe prep

  * Clear space for workstations
  * Move field microscope and vortex into room
  * Label hemolymph collection Eppendorf tubes with sample # (1-12) and date there should be 1 tube per individual
  * Label FCM assay tubes with sample # (1-12), probe, and date
  *  Probe = SYBR-PI, DCFH-DA, Beads, JC-10 There should be 4 tubes per individual
  * Assemble equipment - racks/trays, needles and syringes, rongeurs, gloves, slides, mesh screen, pipette tips and pipetters (100 - 1000 ul), sharps container  

*  Flow Cytometer Room (FCR)  - incubation and running samples

  * Ensure enough filtered seawater and DI water
  * Keep some FSW in fridge
  * Put up garbage bags/cardboard against windows to eliminate light
  * Extended flow cell clean and leave machine online
  * Set-up excel spreadsheet and templates

* Rm 29

  * Label RFTM tubes
  * Collect supplies: calipers/ruler, dissecting tools, nitrile and safety gloves, alcohol dip and burner, sterile pipette/syringe (to add abx solution), cover to incubate cultures in the dark
  * Data collection sheet/lab notebook

*  Holding tanks
  * Bring up oysters in flesh colored trays that have individual spaces for the oysters and are numbered.

## Equipment/Station Prep - Day Of

*  MCR - Hemolymph sampling and probe prep

  * Bring in trays of crushed ice - hold sample tubes in ice tray
  * prime syringes with 0.1mL ice cold FSW - hold syringes and FSW on ice tray
  * Add FSW to FCM assay tubes - hold on ice
    * SYBR-PI = 300uL FSW
    * DCFH-DA = 300uL FSW
    * Fluorescent beads = 150uL FSW
    * JC-10 & control = 100uL FSW each
  * Scrub and rinse oysters. transport  in buckets of conditioned SW.
  * Label oysters to keep track through sampling process - labeled trays
*  FCR  - incubation and running samples
  * Start up computer (password = sh*theel) and then the second password is written directly on laptop computer
  * Open up the C6 software and start the program
  * Push the power button for the C6 and wait for the green light to turn on (do not need to hold down for long).
  * Backflush with DI water as sheath fluid and then run clean DI water for 2 minutes on FAST and delete data after run is over.  Switch sheath fluid from DI water to filtered SW (0.22um).  Be sure to empty waste container (after emptying the waster, fill the waster container  to designated line with bleach before attaching)
  * Pull out frozen reagents from food prep room freezer and put in dark drawer to thaw until ready for use (SYBR green, beads, JC-10, and DCFH-DA).  Can also grab the Propidium Iodide and bead solution from the fridge at this time.

## Hemolymph sampling - MCR

  * Notch shell with ronguers 2/3rds of the way down the dorsal (straight) edge, away from the hinge. (see diagram)
  * Collect with sterile, 1.5″ 25 G needle and 3-mL syringe primed ice-cold FSW
  * Examine each syringe of hemolymph under microscope for contamination.
 remove needle, drop from syringe to slide to view under microscope
  * If contaminated (look for ciliates, gill, and digesta) Filter out debris using 75um mesh screen.
small square of screen over the top of the tube, depress the screen in and empty syringe to the tube
note: may see gametes, in which case skip the sample altogether
    * Note: when adding hemolymph sample to collection tube (with or without mesh), remove the needle first!
  * Keep all samples on ice until incubation with probes.
Use within hours of sampling
Send labeled oysters to Rm 29 for further processing

    *The is the perfect time to grab a quick snack, water, hit up the bathroom, whatever you need Break time before we begin the time-sensitive portion of our experiment*

  * Add hemolymph to all FCM assay tubes to minimize waste of pipette tips for hemolymph samples (use separate pipette tip for each oyster) - hold on ice until probes are added

    * SYBR-PI = 100uL hemolymph
    * DCFH-DA = 100uL hemolymph
    * Fluorescent beads = 150uL hemolymph
    * JC-10 & control = 100uL hemolymph each

## Probe incubation - FCR

* Add reagents for Viability
  * 4uL SYBR Green + 4uL Propidium Iodide
  * Vortex then store in DARK at room temperature
  * Note start time and set timer. Incubate for 1 hour.
  * Notes: SYBR green adheres to all cells (green) and propidium iodide to the dead cells (red) - gives a look at the nature of your hemolymph (live vs. dead cells). Use FSC and SSC for analysis
* Add reagents for ROS
  * 4uL DCFH-DA
  * Vortex then store in DARK at room temperature
  * Note start time and set timer. Incubate for 2 hours.
* Add reagents for Phagocytosis
  * 30uL bead solution
  * Vortex then store in DARK at room temperature
  * Note start time and set timer. Incubate for 2 hours.
* Add reagents for mitochondrial membrane potential
  * 5uM JC-10
    * JC-10 stock solution = 2 mg/ml (2g/L); molecular wt = 583.34 g; thus stock in molarity is (2/583.34) 0.003428 M or 3428 uM.
    * Dilute stock 10x to achieve Molarity 342.8 uM. Why? Allows you to accurately pipette a volume of stock to achieve such small molarity in sample
    * Now in 200 ul sample (100ul FSW + 100ul hemolymph) you need 2.91 ul of 342.8 uM JC-10 stock
  * Vortex then store in DARK at room temperature
  * Note start time and set timer. Incubate for 15 minutes.
  * Notes: Detect using FL1 and FL2
* Add reagent for JC-10 control (CCCP or FCCP)
  * 5uM JC-10 + 50-100uM CCCP
  * Vortex then store in DARK at room temperature
  * Note start time and set timer. Incubate for 15 minutes.
  * Notes: Detect using FL1 and FL2    

## Running Samples on Flow Cytometer - FCR

* Before running samples - make sure sheath fluid is on DI * water and run SIP clean
* Switch sheath fluid to FSW
* Parameters for all samples:
  * Run time =  30sec
  * Fast flow rate = 66 ul/min
  * Threshold of 100,000 on FSC-H (forward scatter)
  this threshold us used to set the sizes of desired cells / particules for detection
    * Note: need to do backflush every 20 samples, and a SIP clean anytime the machine is not used for 10 minutes.

* At 15 min - JC10 & control
  * Open MMP template, save as workbook.
  * Run samples on FAST for 30 sec.
  * Save workbook
  * Backflush & SIP clean
* At 1 hour - Viability (SYBR-PI)
  * Open viability template, save as workbook
  * Run samples on FAST for 30sec.
  * Save workbook
  * Backflush and SIP clean using DI water
* At 2 hours - ROS (DCFH-DA) & Phagocytosis (beads)
  * ROS
    * Open ROS template, save as workbook
    * Run samples on FAST for 30sec.
    * Save workbook
    * Backflush and SIP clean using DI water
  * Phagocytosis
    * Open Phagocytosis template, save as workbook
    * Run samples on FAST for 30sec.
    * Save workbook
    * Backflush and SIP clean using DI water

## Example timeline (using military time for clarity)

Estimated run time per probe (10 samples + backflush and SIP clean) =  ~25 minutes

**Person A** - pipetting reagents to samples - write timestamp on sheet and tube rack - kep in dark and transport to the flow cytometer

**Person B** - running the flow cytometer

- Person A: 0:00-0:20 add DCFH-DA reagents (with ~2 minute lag)
- Person A: 0:25-0:45 add ROS reagents (with ~2 minute lag)
- Person A: 0:50-1:10 add JC-10 reagents (with ~2 minute lag)
- Person B: 1:15-1:35 run JC-10 samples on flow cytometer
- Person B: 1:35-1:40 swap sheath - backflush+SIP clean - swap sheath
- Person A: 2:00-2:20 add viability (SYBR-PI) reagents (with ~2 minute lag)
- Person B: 2:00-2:20 run DCFH-DA samples on flow cytometer
- Person B: 2:20-2:25 swap sheath - backflush+SIP clean - swap sheath
- Person B: 2:25-2:45 run DCFH-DA samples on flow cytometer
- Person B: 2:45-2:50 swap sheath - backflush+SIP clean - swap sheath
- Person B: 3:00 - 3:20 run viability (SYBR-PI) samples on flow cytometer


## Clean-up for FCR

**You have now completed running the samples!!**
* Discard all test tube solutions into a beaker to go into the labeled waste container in the fume hood.  
* Put all frozen reagents and refrigerated reagents back in storage now if not done already.  
* Can also empty waste from side container on C6 if getting to about halfway full.
* To finish up, switch the input tubes on the side of the C6 instrument from FSW to filtered DI water.  
* Backflush and run with bleach for 2 min and then DI water for 2 min on FAST.  
* Leave this DI water in place on the C6 and turn the computer off.  Then turn off the C6.
