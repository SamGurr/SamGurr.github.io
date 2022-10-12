---
layout: post
title: TagSeq_prep_Pgenerosa_putative_genes
date: '2020-07-09'
categories:
  - Summary
  - Preparation
tags:
  - geoduck
  - proteins
  - tagseq
  - blast
---


## Summary of Experiment in 2019



### Table: Results of the repeat pCO2 stress exposure
##### Stress acclimation improves performance and oxidative status under subsequent stress encounter(s)

 life stage  | age  | Stress acclimation (Y/N) | intensity (uatm)  | Repeat exposure (Y/N) | intensity (uatm) | Respiration rate | Shell growth | Tissue growth (AFDW) |Antioxidant capacity |
 --------: | --------: | --------: | --------: | --------: | --------:| --------: | --------: |  --------: | --------: |
postlarval 'settlement'; pediveliger to juvenile | 30 d to 5 mo post-fertilization  | N  | 900 µatm (ambient) |  N | 900 µatm (ambient)  | - | - | ↓''   | ↑''|
-|  -| N  | 900 µatm (ambient) | Y  | 3000 and 4900 µatm (moderate & severe)  | ↓' |  ↓'' |  ↓'' | ↑''  |
-|  -|  Y | 3000 µatm (moderate)| N  | 900 µatm (ambient)  | ↓'' | -  | ↑'' | ↓''  |
-|  -|  Y | 3000 µatm (moderate)| Y  |3000 µatm (moderate) | ↑' | ↓'' | ↑'' | ↓''  |
-|  -|  Y | 3000 µatm (moderate)| Y  | 3000 and 4900 µatm (moderate and severe) | ↑'' |  ↑'' | ↑'' | ↓''  |

-  *↑ ↓ relative rates/analysis between treatments after a single repeat exposure (') and multiple exposures ('')*
-  **Table summary**: acclimated phenotype had greater shell size/tissue biomass/respiration rate and reduced antioxidant protein activity*
----------------------------------------

## Moving forward...
#### Questions:

  - Can moderate oxidative stress or mitchondrial dysfunction improve cellular stress response (i.e. anticipatory frontloading) and physiological performance?
      - What is **frontloading?**
> Figure from Barshis et al. 2012: Genomic basis for coral resilience to climate change

  ![Barshis_etal2012](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Barshis_etal2012.jpg "Barshis_etal2012")

  - Is the **alternative oxidase (AOX) mitchondrial pathway** expressed by acclimatized phenotype to **permit enhanced performance** (continue ATP production) and **decrease mtROS/mitchondrial dysfunction** under acidification?

  -  Does the **early-life and/or paternal envrionment** increase mitchondrial flexibility in  under equal or greater stress intensity?
    - driven by **non-genetic acclimation /inheritance**?
    - is/are there **stress-intensity-dependent effects** of this pheonomenon? (i.e. **magnitude, freqency, duration of stress encounters**)


----------------------------------------
## Objective:

  - investigate mitchondrial mechanism(s) and differnetial expression patterns driving stress-intensity-dependent phenotypic variation (table above)
    - TagSeq  = characterize the expression of target GOIs
    - Metabolomics = analyze the relative importance of reduced cofactors (NAD+ and CoQH) and ATP between treatments
    - DNA sequencing methylation (downstream from prior measurements..) = are there patterns of differential methylation alongside treatments with greater phenotype variation (table above) and differential expressions? Can reveal a stress intensity dependent effect (timing, magnitude, frequency) to elicit epigenotypes on a intragenerational hormetic framework under hatchery timeline

  - Extract RNA/DNA from ~3 samples in ALL treatments at T0, Day 7, Day 14, and Day 21


### Figure and Table: Experiment from 2019 and sampling plan

![Repeat_exposure_TagSeq](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Repeat_exposure_TagSeq.JPG "Repeat_exposure_TagSeq")

 - **Magenta** circles highlight the **target samples for extractions and sequencing**

![DNARNA_extraction_table](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/DNARNA_extraction_table.JPG "DNARNA_extraction_table")

## Mechanism Figures
### Connections between the phenotype and proposed pathway(s) for further investigation

- References in figure...
   - a few GOIs as *numbers*
   - metabolomics targets as *M*

![Mechanism](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/2020_AOX_RET_Crosstalk.JPG "Mechanism")

### How hypercapnia and acidosis may influence Fe-dependent activity (TET Jmj-c), retrograde-ROS signaling, and sirtuin-mediated response

![FE2_OA_methyl](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/FE2_OA_methyl.JPG "FE2_OA_methyl")


#### Current findings
  - *Acclimated phenotype* : = ↑ growth, ↑ metabolic rate, ↓ CSR
  - *Not acclimated* = ↓ growth, ↓ metabolic rate, ↑ CSR


#### Next Analysis
  - *Acclimated phenotype* : proposed pathway =  Alternate oxidase (AOX)
  - *Not acclimated* :  proposed pathway =  Reverese electron transport (RET)
  - **TagSeq & metabolomics** : investigate a stress-acclimation-dependent effect on mitchondrial function(s) [targets: AOX, UCPs, sirtuins, complexes 1 & III, ATP, NAD+:NADH, CoQ:CoQH]

#### Future directions
  - Mitonuclear crosstalk :
    - *What is the role of stress hormesis (via ocean acidification exposure(s)) on DNA/histone methylation (i.e. Jmj-C and TET activity) and anterograde and retrograde signaling (i.e. unfolded protein response)?* *Is there as stress timing- (i.e. paternal & early-life environment) and intensity-dependent (i.e. duration, magnitude, frequency) effect?*

----------------------------------------

### I) TagSeq
#### Identified target genes of interest (GOIs)

### 1. AOX

- *putative P. generosa seqID:* **PGEN_.00g108770**

##### Why alternative oxidase (AOX)?
  - Function:
    - catalyzes the oxidation of ubiquinol and reduction of oxygen to water. Protons taken from uqiquinolnot the mitchondrial matrix (unlike the cytochrome c oxidase reaction; complex IV).
    - allows ATP production and reduces ROS under envrionmental disturbances.
  - AOX is theorized to be prevalent in animals that have frequent transitions from hypoxia to reoxygenation during thier life history - helps taxa survive transitions from anaerobic conditions without substantial damage  to membrrane lipids and proteins by ROS (McDonald and Gospodaryov 2019).
    - Example: In Eastern oyster, Crassostrea virginica, there are two splice forms of AOX mRNA which are expressed in a number of tissues (Liu and Guo, 2017) and assist resitance to hypoxia-reoxygenation

> Table below from: McDonald et al. 2009, Alternative oxidase in animals : unique characteristics and taxonomic distribution

![AOX_McDonald_2009](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/AOX_McDonald_2009.JPG "AOX_McDonald_2009")


##### What is mitchondrial dysfunction?
  - Mitochondrial dysfunction is defined as electron leak or increase of ROS production due to an alteration of normal electron transport.
  - Causes:
    - Reverese electron transport (RET): can occur under (i) high pools of reduced metabolites NADH:NAD+ and CoQH:CoQ; well-chracterized under dietary restriction (ii)  pH gradient ([H+]) and/or protonmotive force of the inner mitchondrial membrane

##### In summary...
  - AOX is an alterantive mitchondrial pathway known as an adaptive response in bivalve taxa under envrionmnental stress. Thus, the lower antioxidant response and greater performance of the stress-acclimated phenotype in 2019 (table above) suggests higher ATP and lower ROS -- this may be driven by enhanced mitchondrial flexibility (i.e. via AOX) due to prior stress priming!

> Fig. below from: Saha et al. 2016, Alternative oxidase and plant stress tolerance

![AOX_Saha2016](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/AOX_Saha2016.JPG "AOX_Saha2016")

### 2. Sirtuins (SIR1, SIR2, SIR3, SIR5)

- *putative P. generosa seqID:* **PGEN_.00g048200** (SRT1)

- *putative P. generosa seqID:* **PGEN_.00g012340** & **PGEN_.00g012350** (SRT2)

- *putative P. generosa seqID:* **PGEN_.00g153700** (SRT5)

- *putative P. generosa seqID:* **PGEN_.00g033970** (SRT7)

##### About:
  - sirtuins are NAD+ dehydrogenases involved in post-traslational modification of histones and proteins in the cytosol (Figure below)
  - Several sirtuins:
    - Mitochondria: SRTs 3, 4, and 5
    - Cytsol: SRT2
    - Nucleus: SRTs 1, 6,7
  - deacetylation of proteins can increase proteostasis and alleviate dysfunction - i.e. sirtuins can increase the antioxidant response (SRT 3 and 5) and promote forward electron transport/beta oxidation in the mitchondria (SRT 1); both suggest a sirtuin-mediated cellular response under mitchondrial dysfunction (Figure below)

![sirtuin_mitonuclear](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/sirtuin_mitonuclear.JPG "sirtuin_mitonuclear")

### 3. Mitchondrial carrier protein

- *putative P. generosa seqID:* **PGEN_.00g063670**

##### About:
  - uncoupling proteins are activated by lipid peroxidation - thus they are a response of oxidative stress and are increased during dysfunction
  - uncoupling proteins reduce the protonmotive force (and pH gradient) of the inner mitchondrial membrane reducing ROS production from mitchondrial dysfunction at the expense of reduced potential for ATP

![UCP_cartoon](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/UCP_cartoon.JPG "UCP_cartoon")


### 4. NADH dehydrogenase

- *putative P. generosa seqID:* **PGEN_.00g299160**

##### About:
  - complex 1 of mitochondrial electron transport chain.
  - major source of mithcondrial ROS production and increases activity under dysfunction - particularly knwon to increase activity under reverse electron transport under increase proton and pH gradient of the inner mitochondrial membrance

   - *Note: This suggests mitchondrial dysfunction under intracellular acidosis and hypercapnia!*

### 5. Cytochrome c reductase

- *putative P. generosa seqID:* **PGEN_00g275780** (Pfam: Ubiquinol-cytochrome C reductase complex 14kD subunit)

##### About:
  - complex III of mitochonrial electron transport chain
  - major source of mithcondrial ROS production; may reduce abundance/activity under mitchondrial dysfunction - Example: high ratio complexI:complexIII is an indicator of reverese electron transport

## DNA and histone Methylation
### 6 & 7. Jumonji C and Ten-eleven translocation (TET)

- *putative P. generosa seqID:* **PGEN_.00g257110** (Jumonji-C)

- *putative P. generosa seqID:* **?** (TET)

### 8. DNMT 3a & DNMT 3b

- *putative P. generosa seqID:* **PGEN_.00g029420** (DNMT 3a; Sam White's Pgenerosa annotation)

- *putative P. generosa seqID:* **PGEN_.00g067800** (Pfam: C-5 cytosine-specific DNA methylase; Cysteine rich ADD domain in DNMT3)

##### About:
  - Jumonji-C and TET function in the demethylation of histones and DNA, respectively - a post-translational (histones) and DNA modification that effects transcriptional regulation
  - Why is this interesting in response to OA stress?
    - Jumonji-C and TET activity is dependent on Fe2+. Chelated Fe2+ is released during intracellular acidosis - further Fe2+ is reduced to Fe3+ from the Fenton reaction also catalyzed by acidosis.
  - Altogether, an iron-acidosis interaction may have downstream effects on non-genetic transcriptional regulation - this is an interesting direction to investigate the role of epigentics in mitonucluear crosstalk and hormetic conditioning under OA conditions!

### II) Metabolomics

#### 1. ADP/ATP

  - Expected ATP: **AOX pathway  ** RET/dysfunction pathway

#### 2. NAD+:NADH

  - Expected NAD+/NADH: AOX pathway **< RET/dysfunction pathway**
  - Note: although dysfunction can be casued by a high pool of NADH, the high activity of complex I oxidizes NADH to NAD+.

#### 3. CoQH

  - Expected CoQH: AOX pathway **< RET/dysfunction pathway**

----------------------------------------

## Resources:
#### Panopea generosa (Pacific geoduck) draft genome
- link: http://dx.doi.org/10.17605/OSF.IO/YEM8N

#### Repository of target genes
   *note*: repo originally in preparation for qPCR - contains blast hits and primer3 outputs for several target GOIs and normalization genes

- link: https://github.com/SamGurr/Pgenerosa_primers
