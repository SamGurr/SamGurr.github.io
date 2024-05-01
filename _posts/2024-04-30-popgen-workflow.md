---
layout: post
title: popgen workflow
date: '2024-04-30'
categories: analysis processing computing
tags: popgen genomics angsd snp_calling clusters bash bioinformatics
---

## Pogen workflow

* *as of 4/30/2024*

**Objective**: walk through the current process completed and in progress on the OAP Bay scallop project
inlude the stepwise overview, scripts, troubleshooting/tips, obstacles, etc. 



**About**: We raised three generations of bay scallops from F0 - F3 under laboratory stress, in which larvae 
were exposed to the same confition with respect to their parents. The objective of this work is to determine the 
capcity for rapid adaptation in this species by identifying putatively adaptive genomic regions. We used low-coverage
whole genome seq data to maximize replication and quantify allele freqs across the entire expereiment as follows 

| About | # treatments | notes | 
| --- | --- | --- |
| F0 Broodstock | 0 | our starting population (F1's parentage!), seqenced all individuals that constributed eggs or sperm in batch fertilizations |
| F1 Juveniles | 2 | whole juvneiles ~100 days in age, low and moderately-elevated pCO2, ~40 each | 
| F1 Broodstock | 2 | our first generation spawners (F2's parentage), seqenced all individuals that constributed eggs or sperm in batch fertilizations | 
| F2 Juveniles | 3 | whole juveniles ~100 days in age; low, moderate and severely-elevated pCO2, ~40 each* | 
| F2 Broodstock | 3  | our first generation spawners (F3's parentage), seqenced all individuals that constributed eggs or sperm in batch fertilizations |
| F3 Juveniles | 3 | whole juveniles ~80(?) days in age; low, moderate and severely-elevated pCO2 | 


*The severely-elevated pCO2 animals were split from the low pCO2 during F2 post-metamorphosis - therfore the first generation of severely-elevated pCO2 exposure has the same parentage as the low pCO2 animals. Exposure to this high OA conditoin occured shortly 
before they were samples, expect minimal change between these cohorts 


## Workflow

### Clean reads & QC 

*input* = raw fastq.qz files! 
*output* = clean fastq.gz files

Note: use `scp` to upload from your personnal to the cluster, but remember to run `md5checksum`! 

**modules**: fastp, trimmomatic, etc. 

* cite: 

### Map to reference genome 

*input* = clean fastq.gz files!
*output* = mapped .bam files!

**modules**: hisat2

* cite: 


### Merge bam files 

*input* = mapped bam files, forward (R1) and reverse (R2) for each sample
*output* = one mapped bam file per sample!

**modules**: samtools

* cite: 

### Sort bams and remove duplicates

*input* = mapped bam files
*output* = mapped bam files with duplicates removed and sorted by coordinate

Important: you can sort by queryname and coordinate to remove duplicates. Check the stats 
output from duplicate removal. Which method removes the most data? Is there rationale with one over the other? 
Conduct a sanity check here to decide on the best foot forward - this will reduce the memory load on the cluster 
becasue all these mapped bams add up!

**modules**: picard

* cite: 

Note: I found quername sorted bams maximized duplicate removal in all cases. 
I therefore sort by queryname, then remove duplicates and follow with coordinate sorting the output. 
becasue the output *must be coodinate sorted* to run angsd! 

### Genotyping

*input* = mapped bam files (duplicates removed and coordinate sorted!)
*output* = geno.gz, mafs.gz, .vcf, and more!

**modules**: angsd

* cite: 
