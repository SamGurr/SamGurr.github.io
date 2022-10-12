---
layout: post
title: Phys Assays Pipeline
date: '2019-10-10'
categories: Processing
tags: physiology, geoduck, total protein, antioxidant capacity
---
# Pipeline for geoduck physiology (oxidative stress, total protein, & AFDW/condition index)
NOTE: the following protocol was followed in analysis of juvenile geoduck (~5-8mm shell length)
from an OA experiment completed in summer 2019. **Juvenile geoduck (whole animals) were snap frozen in LN2 at the hatcheryand stored at -80°C until later analysis**

## **1.) Sample preperation**
#### **Homogenize samples / record homogenate volume**

**PREPARATION:**
  - label four 1.5 ml epindorf tubes per sample ID (four aliquots of homogenized tissue; n = 4 phys measurements)
  - chill PBS before use
  - use cold beads (stored at -20°C) to hold a 25ml beaker of cold PBS and samples
  - divide bead bin for four tube destinations
  - label four storage boxes for four assays = total antioxidant capcacity (TAC),
  condition index/AFDW (CI), lipid peroxidation (LP), and total protein (TP)

**HOMOGENIZE FROZEN SAMPLES:**

- add **200 µl cold PBS** to the sample tube
- homogenize samples **thoroughly!**
- pipette **200ul cold PBS to rinse** the homogenizer blade **into** the sample tube

*Important note:* volume of PBS used here **is the minimum needed for downstream assays and is both flexible and sample-dependent** (e.g. 200 µl + 200 µl = 400 µl) for...

1.) the volume needed per sample in downstream assays

2.) volume needed to rinse *all* sample from the homogenizer

- **clean homogenizer** - *before every subsequent sample AND when finished...*
submerge the the homogenizer in centrifuge tubes (15-25mL) of
DI --> bleach --> DI --> >70% ethanol --> DI. Dry with Kimwipe.
Run the homogenizer for 1-2 seconds before the next sample

**TOTAL HOMOGENATE VOLUME (HV):**
- *using a 1000 µl (1ml) pipette* **meausure HV** of
the homogenized sample (e.g. homogenized geoduck + 400ul cold PBS; **~500-800 µl**)
- **RECORD HV and tube/sample ID in datasheet**

- pipette four aliquots in **seperate labeled tubes** for the following:

  *IMPORTANT! **vortex** the HV epindorf tube **between each aliquot** so the sample is homogeneous for each aliquot!*

1.) 50ul - **total protein (TP)** need 20-25 µl per sample in microplate assay (50 µl in duplicate)
    e.g. BCA Rapid Gold used 20µl per well; 40µl in duplicate; BCA (normal) used 25µl per well; 50µl in duplicate
    also! necessary to solubalize insolubale protein before this assay (added ~100-200µl of 1M NaOH and 0.1 M HCl)

2.) 50ul - **total antioxidant capacity (TAC)** need 20 µl per sample in microplate assay (40 µl in duplicate)

3.) 100ul - **lipid peroxidation (LP)** need 300 µl for TBARS acid treatment;
    150ul per sample in microplate assay (300 µl in duplicate)

4.) 270 - 400 µl - **condition index/AFDW (CI)** the remaining sample can be used for CI
    (e.g. 100 µl(TP) + 80 µl(TAC) + 350 µl(LP) = 530 µl; 800 ul - 530 µl = 270 µl)

- **After complete each sample!** place the four aliquoted tubes in labeled storage box (total protein, total antioxidant capacity, AFDW, lipid peroxidation) and store **immediately in...**

| Phys.Box |Location|
---------- | ---------
|  AFDW |  -20°C fridge  |
| Total protein  |  -80°C fridge |
| Lipid peroxidation  |  -80°C fridge   |
| Total antioxidant capacity  |  -80°C fridge  |

## **2.) Physiological Measurements**
##### About
*Q: Why measure oxidative damage and antioxidants?*

 *Review the following:*
- (1) Costantini, D., & Verhulst, S. (2009). Does high antioxidant capacity indicate low oxidative stress?. Functional Ecology, 23(3), 506-509.
-  (2) Monaghan, P., Metcalfe, N. B., & Torres, R. (2009). Oxidative stress as a mediator of life history trade‐offs: mechanisms, measurements and interpretation. Ecology letters, 12(1), 75-92.

## I. Total protein
#### Assay:  Pierce(TM) BCA Rapid Gold Protein Assay Kit (Thermo Scientific)
**ABOUT** Unique aspects of this assay...
- uses 20µl sample or standard per well
- 5 minute incubation at room temp before measure on spec
- absorbance at 480nm

#### Assay:  Pierce(TM) BCA (normal) Protein Assay Kit (Thermo Scientific)
**ABOUT** Unique aspects of this assay...
- uses 25µl sample or standard per well
- 30 minute incubation at 37°C + 15 minute cool to RT before measure on spec
- absorbance at 562nm

#### PREPARE SAMPLES FOR ASSAY -  SOLUBALIZE INSOLUBLE PROTEIN

1. remove taget samples from the -80C and all them to thaw a bit

2. lyse cells to **solubalize insoluble protein of homogenized whole juvenile geoduck (~4-5 hrs)**
  - *modified from Kevin H. Wong's Lab Notebook (for coral)* - weblink: https://kevinhwong1.github.io/KevinHWong_Notebook/Total-Protein-Extraction-Protocol/:


    This protocol is adapted to solubalize insoluble protein of homogenized whole juvenile geoduck in preparation for  the Pierce BCA **Rapid Gold** Protein Assay Kit from Thermo Scientific.
      1. Thaw homogenized tissues
      2. For 50 μL of homogenized juvenile geoduck, add 10 μL of 1M NaOH  into each vial (**pH should be ~10**)
      - The vial will be too small to fit a pH probe, therefore pipette a very small amount onto **pH paper**
      3. Incubate each vial at **50°C for 4 hours shaking at 300rpm**
      4. Add **70 μL of 0.1M HCl** to each vial to neutralize the sample
      - Add the HCl in small increments and test pH (*could be sample specific*)
      - *NOTE* in this example we are diluting the sample by a factor of 2.6; 50µl sample + 10µl 1 M NaOH
      + 70µl 0.1 M HCl = 110µl total; 110µl total / 50µl sample = 2.6 dilution factor
      pH should be at 7 - use more/less HCl depending on your sample
      Ensure pH is at 7 before moving on to the next steps
      5. Now use this prepared sample for the BCA protocol.

      During the 4 hour incubation, follow the Pierce BCA Protein Assay Kit (Rapid Gold or normal) instructions to prepare the BSA standards and working reagents. Use the micro plate procedure if using the plate spectrophotometer. *DO NOT* prepare the WR for the Rapid Gold assay kit unil used - this reagent will decay after 1.5 hrs.

#### MEAURE TOTAL PROTEIN - RUN BCA PROTEIN ASSAY KIT

Link:

*Notes on BCA Protein Assay Protocol*
- **Bovine Serum Albumin (BSA, for standards)** - careful pipetting, this bubbles easily and can alter spec results. To avoid this, purge pipette above the meniscus. Also... 200 µl pipette tip does not fit in the albumin container and therfore must be pipetted in smaller aliquots
- **Diluent** = DI water
- When adding (1) dilent (2) WR reagent to microplate w/multichannel pipette **pipette mix the sample and DO NOT purge below the meniscus**

- **Q:** What to do with extra standards/when do you make new standards?
  - although a standrd can be used multiple times (stored at -20 C)....  it is good practice to remake the standard **each time the WR** (working reagent) **is made** HOWEVER, the WR for Rapid Gold MUST BE USED WITHIN 1.5 hours

### II. Ash Free Dry Weight OR Condition index (if standardized to size metric)

#### REVIEW TABLE FOR STEP BY STEP INSTRUCTIONS

| Steps |Instrument | Temperature | Data measurements | Units | Notes
---------- | --------- | --------- | --------- | ---------  | ---------
| Thaw 'AFDW' samples | -| room temperature | - |- |-|
|  Label tin dishes with sample IDs | - | - | - |- |-|
| Measure empty dish weight   | Scale  |  - | Empty dish (ED)  |  grams |-|
| Add samples to dishes, use PBS if needed |  -| - | - | - |-|
| Dry samples for 12-24 hrs | HermaTherm Oven  | 75°C |-  | -|-|
|  Measure Dry Weight |  Scale |  - |  Dry weight + empty dish (DW) |  grams | option A: measure directly after removed from oven - do not want samples to aquire moisture/weight; option B load samples into a desicator with dessicant and measure over time |
| Ignite samples for 4 - 4.5 hrs  | Muffle Furnace  |  450°C  |  - |-|-|
| Allow samples to cool  for 2 hrs   |  Muffle Furnace  |  < 450°C  |  - |  - | simply turn off the furnace and allow to sit - keep the furnace door closed  |
| Measure AW of samples |  Scale | - | Ash  weight + dish (AW) | grams| samples will be very hot, use glove and forsnips to remove from the muffle furnace |

#### CALCUATE AFDW
**Ash Free Dry Weight** = (DW - ED) - (AW - ED) = AFDW, Organic weight  of sample

- *Remember* the total homogenized sample (HV) will back-calculate the TOTAL_AFDW of the entire animal.
- Example: if HV = 800µl and the volume aliquot for AFDW = 200µl then Dilution Factor = ((800 + 200) / 200) = 5
- if AFDW = 2 mg; TOTAL_AFDW = 2 × 5 = 10 mg

### III. Total antioxidant capcacity (CSR to oxidative stress)
#### Assay: OxiSelect(TM) Total Antioxidant Capacity (TAC) Assay Kit (Cell Biolabs Inc.)
### IV. Lipid peroxidation (oxidative damage)

#### Assay: Parameter(TM) TBARS Assay (R&D Systems Inc.)
### 3.) Pipeline figure
### 4.) Example Calculation
