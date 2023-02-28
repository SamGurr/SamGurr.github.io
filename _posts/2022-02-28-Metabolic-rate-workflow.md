---
layout: post
title: Metabolic rate workflow
date: '2022-02-28'
categories: Protocols
tags: metabolism respiration Presens Loligo R scallops NOAA  
---

# Metabolic rate workflow

## objective:
walkthrough all steps from data upload to analysis of respiration rate data using both the presens and loligo datasets. Note, this documet does not 
describe the process for data collected - review SOPs for this information 

----

## Table of  contents:

| Task | About |
| ---- | ---- | 
| [Raw data upload](#Raw-data-upload) | the format and location of stored and working data | 
| [Metadata](#Metadata) | all reference data pertaining to the sample | 
| [Plot raw timeseries](#Plot-raw-timeseries) | an initial sanity check, visualize the raw timeseries O2 consumption data | 
| [Compute raw rates](#Compute-raw-rates) | compute rates and plot diagnostics using the R package LoLinR (Olito et al. 2017)   | 

----

## Raw data upload

**about**: where the data will live both on remote and local drives for the team, the format and data management 


#### Format of the **raw data**..

The raw respiration data exists in two forms *dependent on whether the presens or loligo system* was used for data collection. 

* csv files = Presens system 

	- contains calibration, timestamp, etc data prior to rows with raw timeseries data 
	
* txt files = Loligo system 

	- <title>_raw.txt == contains the calibration, experiment, and the logged timeseries raw data 
	
	- <title>.txt = respiration file that contains sample metadata (if manually input before the start of the trial!)



#### Where is the raw data? 

All data is saved in directories with the time stamp as YYYYMMDD 

	* **google drive** location: BayScallops 2021-2023 > 1.All DATA FILES > ( F0, F1, or F2 here1) >Respiration > file_uploads > YYYMMDD

	* **remote repository (github)** location: RAnalysis > Data > Physiology > Respiration > YYYMMDD 
	
	
#### Nuances between stored (google drive) and working (repository) 

The upload on the google drive and the repository **are the exact same data!** 
with ONE exception

File title. 

Google drive (storage) = the title of the file on the respirometry laptop. This title varies dramatically depending on who
recorded respiration for that day. I decided to keep consistancy with the raw local stored data (government laptop) and the 
project google drive 

Repository (working data) = the title was changes to accomodate looped upload and analysis in R such as 'run_1_raw.txt' 


----

## Metadata

**about**: downstream analysis is dependent on merging raw data with master metadata sheets, else the 
rates we will aquire for particular channels will have no relevance to sample ID, treatment, size, etc. Here I 
decribe how our metadata is structured in order to call by a unique sample identifier. 


*We have two datasheets for the metadata* where the data is **input manually** for each sample! 

* Why important? 

- the raw data contains only  the following information: the directory, filename, channel IDs

	- directory: functions as the date YYYYMMDD
	
	- fileaname: we rename the file to function as run number 'run_X_raw.txt'
	
	- channel IDs: the raw data has numerical identifiers for column names signifying the probe channel
	
	- summary - the timestamp, run number, and channel are integral to assigning more metadata needed for calling sample-specific attributes such as the 
whether a blank or live sample, the treatment, tank ID, size of the indivdual(s), and number of individuals 

* (1) **Reference_resp_ID.csv**

- main objective of file is to *assign treatment and replicate ID to the respiration data* 

- contains the timestamp as MM/DD/YYYY and all metadata to describe the sample treatment, replicate, and respiration system 
(i.e. pH, tank ID, sample number, number of individuals, respiration channel, plate, run, etc.). Importantly, there is a 'Filename' column where the 
exact filename of the respiration data is input (i.e. 'Run_1_.txt)

- a few important columns to expand upon 
	- (a) 'Number' is a unique identifier if multiple samples were measured from the same treatment and tank replicate and on the same run, else these will be viewed as the 
same individual downstream (i.e. CH2 and CH3 in Run 1 are pH 8 replicate A, Number calls them 1 and 2) 	
	- 'Filename'  column contains the renamed file name *NOT* the google drive raw title
	- Chamber_tank calls 'blanks' - further reinforced by NA in other columns (i.e. Replicate, Num_individuals, etc.)

- each column is important to merge the data correctly, as each row is unique to a respiration data point - thinking of a tree and branches, the 
filename and date are the broad identifiers whereas the ph treatment, replicate, and sample number are the fine-scale identifiers on the individual level 

	
	
* (2) **Reference_resp_size.csv**

- main objective of file is to *assign size data to the sample* 

- contains the same unique identifiers as the reference file in #1, these must mimic one another to merge correctly! 
HOWEVER the main difference is this sheet contains the sample length, dry weights, etc. for individuals measured

- Why not have this data in #1? If all respiration data was collected per individual then it is best to have this data merged 
as one file with #1, however on larvae we have multiple individuals per respiration record, such that datasheet #2 contains 
redundand columns with separate individual sizes

	- user can take the mean, length for example, to merge downstream to a single O2 consumption datapoint that was recorded on multiple individuals

	- Note: this size metadata does not call 'blanks' 

----

## Plot raw timeseries

**about**: obtain a visual of the raw data - though we take detailed notes, there are nuanced characterics of each 
respiration run and channel. Observation of these data can assist truncating and diagnostics before computing rates 


SCRIPT: **Respiration_raw_plots.R**

* about the script

- data formatting and loop calls

	- loops through all YYYMMDD directories
	
	- calls raw data for .csv or .txt formats (either presens or loligo data). 
	
	- converts the timestamp to minutes and seconds
	
	- converts units to mg/L if needed (loligo raw output in % air sat)

- plot

    - for each respiration run... output a simple ggplot titled as date_run_number and facet-wrapped by channel ID

* output
	
	- timeseries plots of all data by date X run 
	
	- located in RAnalysis > Output  > Respiration  > plots_raw
	
**with a raw visual..** 

we can make important decisions during the next step - the following script being computationally intensive 
for large datasets. thus truncation of the data by intervals and/or before a cut-off is important to reduce run time. 
	
	- example 1: larval respiration rate data run overnight due to slow rates, high temporal reslution every 5 seconds. In addition to 
	O2-based truncation (only >0 a.s. to avoid confounding effects ofhypoxia on metabolism) we can view the dataset to truncate 
	in intervals or before a specific timepoint (< 3 hours for example) 
	
	- example 2: we have fast rates with adults in which we stopped and reoxygenated containers at 30 minutes of record, however 
	the system was run through lunch before taken down. In this case the majority of the record contains non-critical data and we can 
	truncate < 30 minutes to reduce run time

----

## Compute raw rates

**about**: calculate raw rates of oxygen conumption by time using the LoLinR package (Olito et al. 2017)

SCRIPT: **Respiration_LoLin.R**

* about the script

- data formatting and loop calls (*same as 'Respiration_raw_plots.R'*)

	- loops through all YYYMMDD directories
	
	- calls raw data for .csv or .txt formats (either presens or loligo data). 
	
	- converts the timestamp to minutes and seconds
	
	- converts units to mg/L if needed (loligo raw output in % air sat)

	- **truncates data** based on (1) visual diagnostics of from the raw plots (2) by 15 second intervals for to narrow
	the resolution and resolve slow run time 
	
- compute raw rates 

	- loop the respiration file by channel (looped priors for by date and by run) to compute a raw respiration rate in **mg O2 per minute** 
		
		- note: a good data point is a negative value for O2 cosumed per unit time! 
				
	- **about** LoLinR runs a multitutde of regressions to estimate monotonic rates from time-series data in a statistically robust and reproducible fashion. 
	In relation to historical respiration data, use of this tool is a non-bias and reproducible alterantive avoiding the putative biases 
	in estimate rates by eye (in excel for example) 
		
	- the output rate is the slope of the regression with te highest freqency of occurnace

- plot diagnotics for each data point

	- LoLinR outputs a regression and density plot with vertical designations for the reported slope (i.e. rate) 
