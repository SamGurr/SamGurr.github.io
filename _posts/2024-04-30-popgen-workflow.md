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




# Workflow




## Clean reads & QC 

*input* = raw fastq.qz files! 
*output* = clean fastq.gz files

Note: use `scp` to upload from your personnal to the cluster, but remember to run `md5checksum`! 

**modules**: fastp, trimmomatic, etc. 

* cite: 




## Map to reference genome 

*input* = clean fastq.gz files!
*output* = mapped .bam files!

**modules**: hisat2

* cite: 




### Merge bam files 

*input* = mapped bam files, forward (R1) and reverse (R2) for each sample
*output* = one mapped bam file per sample!

**modules**: samtools

* cite: 




## Sort bams and remove duplicates

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




## Genotyping

*input* = mapped bam files (duplicates removed and coordinate sorted!)
*output* = geno.gz, mafs.gz, .bcf, and more!


**Note:** Using ```angsd``` many filteres can be used based such as minmum allele frequency (MAF), p value, min/max depth, min individuals, base quality etc. 

**modules**: angsd

* cite: 




### Normalize, index, convert to VCF, index, and Intersect (optional) and Merge VCF files 

**Objective:** Combine the output of multiple angsd runs. Note that this depends on the question you are asking and whether you may want to 
analysis these datasets together or separately. For example, we have the SNP calls of a single breoodstock parentage (~20 animals) and offspring of those parents
that were given two treatements before sampled as juveniles (40 per treatment). Angsd was run separately on these three groups (parents, offspring A, offspring B) - 
we may want to merge the offspring A and B VCF files for downstream analysis!

```angsd``` outputs a binary .bcf. file, we want a compressed and indexed vcf file for downstream analysis on and off the cluster!

1) Normalize each bcf file 

* recommended to normalize BCFVCF files so that downstream processes function properly (i.e. merging, intersections, etc.) 
normalization entails aplitting multi-allelic calls, left-aligning indels (insertions or deleterions) and ensuring that alleles 
specified in the vcf/bcf files are also present in the reference genome! 

	* left-aligning means shifting the start position of the varant left until it is no longer possible to do so...
	a concepts with indel variants to specifically describe the nature of a genomic position rather than the length of a variant 
	
	* a variant is left aligned if and only if it is no longer possible to shift it position to the left 
	while keeping the length of all its alleles constant - parsimonious, simpliest explanantion that fits the evidence 
	
	* note there is redundancy here as the bam file was generated according to the position and the ID of the reference genome
	so thisis a it of overkill, but important practice incase 


* Use ```norm``` to normalize indels ```-m``` to split multiallelic sites into biallelic records, if only SNPs should be split or merged specific ```-m-snps```, if 
both SNPs and indez should be merged separately specific ```-m-both``` if SNPs and indels should be merged into a single record, specific ```-m-any```. Use 
```--check-ref``` to notify whether to exit ```e``` warn ```w``` exclude ```x``` or set/fix ```s``` when incorrect or missing allele is encountered, and apply filters 
```-f``` for example only to sites which have no filters set use ```-f PASS```

	* reminder - a SNP is a change in a nucleotide base whereas an indel (insertions or deletion) s self-explanatory, incorporation or removal of 1 or more nucleotides 
	
```
bcftools norm -m-any <input .bcf file> | bcftools norm -Ob --check-ref w -f <genome file>.fasta > <outfile>.norm.bcf
```

2.a) Convert the bcf file to vcf, using ```bcftools```

* uncompressed vcf

```
bcftools convert -O v -o outfilename.vcf inputfilename.bcf
```

* compressed vcf in one step 

```
bcftools convert -Oz -o outfilename.vcf.gz inputfilename.bcf
```

2.b) Compress the vcf file to vcf.gz, using ```bcftools```

```
bcftools sort input_file.vcf  -Oz -o input_file.vcf.gz
```

3) Create an index of the compressed vcf.gz file, using ```bcftools```

	- below used ```-c``` to create CSI files, you can also use ```-t``` if you desire YTBI file

```
bcftools index -c <filename>.vcf.gz
```


**Optional** based on exploratory analysis or specific to the experimental design/hypothesis at hand..

4.a) Intersect vcf files using ```bcftools``` and the command ```isec``` and ```-n```

* What if you want *only* the loci **shared** between all your input vcf files? For example, I have parents and thier offspring 
exposed to two conditions, therefore 3 vcf.gz files deriving from three separate ```angsd``` outputs for parents, offspringA and offspringB

	* here we would use ```isec``` with the command ```-n=3``` note that the equal sign says that you desire the output to have each occurance 
	shared between all input files

```
bcftools isec -n=3 parent.vcf.gz offspringA.vcf.gz offspringB.vcf.gz -p <dir>
```

* What do the outputs by ```-p``` mean? IMPORTANT! The internet severely lacks detail about how to cater 
a specific outcome from inputs in *isec*, I had to run a LOT of trial and error 

	- to get all shared SNPs between input files, use  ```-n=``` as -n=<number of total files> 
	
	- to get all shared SNPs of each input vcf with the first input vcf, use  ```-n=``` as -n=<total linked files -1>; 
	the first input vcf in your list is output as 0000.vcf and serves as the 'source' file of which each subsewent is subsetted for shared SNPs with it
	you can check with bcftools view -H of the pre and post data to see which are the same and which files are shortened by this ```isec``` command

*Output content: 
	
	(1) README.txt: open this file with ```cat``` or ```nano```, this is a great feature in referene to the written command and the reference of the output vcfs
	(2) .vcf files: for each input, in the order written. note that these are names 0000 0001 0002 and so on..  **refer to the README.txt** to know which sample/population
	each .vcf refers to! 
	(3) sites.txt: a simple text list of all the sites called in the isec command. In the example above, this includes the same chromosome + position (or contig) for all 
	shared between all input vcfs. IF we were to use different ```-n``` command, this would have those that are shared and/or unique to input files 
	

4.b) Merge the vcf.gz files together, using ```bcftools``` and the command ```merge``` 

	- assumes that you completed steps 1-3 for each of the vcf files you are merging

	- you can write our each vcf file you are merging, below we use ```*``` because these all live in the current directory
	
```
bcftools merge *vcf.gz -Oz -o Merged.vcf.gz
```


### Viewing the VCF file

* see how big the vcf file is 

```
ls -lh *.vcf.gz
```

* check how many variants there are 

	- this prints each line of the vcf 
	
	- note: compare this to the number of lines in the geno.gz file output by ```angsd```, should be exactly the same!

```
bcftools view -H <filename>vcf.gz | wc -l
```

* take a look at the first five lines of data! 

	- ```-H``` views the vcf file afterthe angsd commands and other vcf metadata to the start of the output alleles, differs from ```-h``` as the true start of the vcf file
	
```
bcftools view -H <filename>.vcf | head -5 | cut -f 1-10
```
	- you can also do this with the ```-m``` and ```-A``` commands using ```grep`` and followed by ```cut```
	
	- note that the cut calls the first 7 columns and A prints the number of  matches with "n" lines after the match

```
bcftools view <filename>.vcf | grep -m 5 -A 5 "#CHROM" | cut -f 1-7
```

* view the header with the delimietr '#INFO' that defines possible output acronyms of the vcf file  

	- to do this, you need to use  ```-h``` and grep for the common string in the header

```
bcftools view -h <filename>.vcf | grep "#INFO"
```

* want to view the genotpes in *character format*? You can do this! 

```
bcftools query -f '%CHROM\t%POS\t%REF\t%ALT[\t%TGT]\n' <filename>.vcf | head
```

* want to view the genotpes in *numeric format*? You can do this! (just remove the **T** in '..t%**T**GT' below!)

```
bcftools query -f '%CHROM\t%POS\t%REF\t%ALT[\t%GT]\n' <filename>.vcf | head
```

### Subsampling the vcf files

**Objective**: understand what filters you should set by subsetting your file (if very large!) to run basic statistics 
One way of ding this (without bias from chronomose position that may have mapped poorly/well) is to truncate your vcf file randomly 
from start to   end. 

**modules**: bcftools, vcflib

The following is an ecample of  a command using ```-r``` as the rate of sampling or the fraction of the total vcf that we wish to retain. 
For example, if we have a file with 1 million variants, ```-r 0.10``` would output a subset with 100 K variants

```
bcftools view <file name input>.vcf.gz | vcfrandomsample -r 0.012 > <file name output>.vcf
```

You can then zip it, this will output <subset output file>.vcf.gz

```
bgzip <subset output file>.vcf
```

And index it for downstream analysis

```
bcftools index <subset output file>.vcf.gz
``` 


### Analysis and diagnostics of vcf files (Pre-filtering!)

**NOTE:** the folloiwng is largely from the link https://speciationgenomics.github.io/

**What statistics?**

* missingness

* depth

* minor allele frequency 

* inbreeding 

**modules:** ```bcftools``` and ```plink```

* ```bcftools`` has the command ```--gzvcf``` used throughout the following to pipe in your compressed vcf file 

* Allele Frequency 

```
VCF_IN=<filename>.vcf.gz
OUT=vcf_statistics/ # not this assumes that where you are running this code is in the direcotry containing vcf_statistics folder
vcftools --gzvcf $VCF_IN --freq2 --out $OUT/AlleleFreq --max-alleles 2
```

* Site Depth 

```
VCF_IN=<filename>.vcf.gz
OUT=vcf_statistics/ # not this assumes that where you are running this code is in the direcotry containing vcf_statistics folder
vcftools --gzvcf $VCF_IN --depth --out $OUT/SiteDepth
```

* Site Mean Depth 

```
VCF_IN=<filename>.vcf.gz
OUT=vcf_statistics/ # not this assumes that where you are running this code is in the direcotry containing vcf_statistics folder
vcftools --gzvcf $VCF_IN --site-mean-depth --out $OUT/SiteMeanDepth
```

* Site Quality 

```
VCF_IN=<filename>.vcf.gz
OUT=vcf_statistics/ # not this assumes that where you are running this code is in the direcotry containing vcf_statistics folder
vcftools --gzvcf $VCF_IN --site-quality --out $OUT/SiteQuality
```

* Missingness

```
VCF_IN=<filename>.vcf.gz
OUT=vcf_statistics/ # not this assumes that where you are running this code is in the direcotry containing vcf_statistics folder
vcftools --gzvcf $VCF_IN --missing-indv --out $OUT/MissingData
```

* Inbreeding

```
VCF_IN=<filename>.vcf.gz
vcftools --gzvcf $VCF_IN --het --out $OUT/InbredCoeff
```

* load ```pink```

```
module load bio/plink/1.90b6.23
```

* output in new folder plink

```
plink --vcf <filename>.vcf.gz --double-id --allow-extra-chr --set-missing-var-ids @:# --extract plink/<filename>.prune.in --make-bed --pca --out plink/<filename>
```






```vcftools --gzvcf $SUBSET_VCF --freq2 --out $OUT --max-alleles 2```


### Calculating Fst from vcf file 

**Options:**

- PGDSider 

- adegenet (in R) 

	- Check out this tutorial - https://adegenet.r-forge.r-project.org/files/tutorial-basics.pdf


* Remove **an individual** from a vcf file

	- note that a set of individuals can also be removed, calling a text file with those listed

```
vcftools --remove-indv adapter_trim.F1-J256-pH75_querydupscoord.bam --vcf F1Juveniles_Merged_filtered.vcf.gz --out F1Juveniles_Merged_filtered.vcf.gz
```


```
VCF_OUT=vcftools_Merged_vcf/F1Juveniles_MErged_filtered.vcf.gz
MIN_DEPTH=10
MAX_DEPTH=50
vcftools --gzvcf $VCF_IN --remove-indels --maf $MAF --max-missing $MISS --minQ $QUAL --min-meanDP $MIN_DEPTH --max-meanDP $MAX_DEPTH --minDP $MIN_DEPTH --maxDP $MAX_DEPTH --recode --stdout | gzip -c > \
```

