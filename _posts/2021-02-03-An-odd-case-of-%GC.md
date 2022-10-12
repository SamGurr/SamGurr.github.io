---
layout: post
title: An odd case of %GC
date: '2021-02-03'
categories: Processing
tags: Tagseq, fastp, mutliqc, trimming, polyA tail, low complexity filtering
---

# TagSeq QC troubleshooting

--------------------------------------------
### The problem...

'clean' TagSeq reads (trimmed of adpters) fail 'Percent GC Content' in the multi QC report (image below)

![GC multiqc report](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/20210203_BEFORE.LowComplexTrim.JPG "failed report")

### Filtering attempts...

I used the following **fastp** calls to remove the low GC reads
- ``` --trim_poly_x ``` = enable polyX trimming in 3' ends

This was my initial gut reaction given that TagSeq targets mRNA polyA tails for short reads. All attempts with this call (i.e. called both 6 and 10 bps) were unsuccessfull!

- ``` --f, --trim_front1```

This was also unsuccessful...

--------------------------------
### What to do next??

Think about the GC plot attached above. This plots does not imply the position of the read, thus ```--f``` and ```--trim_poly_x``` can be irrelevant. A great next step is to (1) identify clean.gz files that did not pass (2) view the sequences using ```zcat```(3) modify fastp accordingly and rerun, check the same clean.gz file for the outcome of this adjustment

##### (1) identify a clean.gz name that did not pass

Screenshot from the multiqc report,
I chose to follow the file 'clean.SG103_S164_L002_R1_001.JPG'

![GC multiqc report](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/20210203_lowGC_files.JPG "failed report")

 ##### (2) Run zcat

```
zcat clean.SG103_S164_L002_R1_001.JPG | head -200
```

Here is the output in nano.
Underlined **in yellow** are instances of polyA within the sequence! Note just localized at the 3' end! Circled **in blue and green** are sequences before and after these off reads.

![screenshot](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Inked20210203_zcat_clean.SG103_S164_L002_R1_001.jpg "screenshot")

Ideas: This may be the result of sequencing error. Also note that the quality scores are mostly 'F' - I included a phred score filter, but this still seems odd

How to ommit these sequences??

It appears that the affected sequences suffer from low complexity. ```fastp``` defaults a complexity of 20% defined as the percentage of base calls that are different from the next base. I think an increase in this threshold should clear our low GC dilemma!

#### (3) Adjust fastp call with ```--low_complexity_filter``` and ```--complexity_threshold``` and rerun

- ``` --y, --low_complexity_filter``` = run to ajdust the complexity filter (default as 20)

- ``` --Y, --complexity_threshold``` call the threshold for the complexity filtering

the new fastp (with adapter trim and phred score trim) included ``` --y --Y 50```
for a threshold of complexity of 50%

Run ```zcat`` of the output 'clean.SG103_S164_L002_R1_001' files

```
zcat clean.SG103_S164_L002_R1_001.JPG | head -200
```


![screenshot2](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Inked20210203_zcat_clean.SG103_S164_L002_R1_001_FILTER.LOW.COMPLEX.50percent.jpg "screenshot2")

We see here that the two sequences previous in yellow (above) are gone!!! Woop! Now take a break from the screen and wait for them multiQC.html report!

--------------------------------
### New multiqc.html report(s)

#### Did not change??

- need to explore further....

![multiQC](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/20210203_AFTER_lowcomplextrim.JPG "screenshot2")

This time I used **the following..**
- ``` --trim_poly_x ``` ==  6
- - ``` --y, --low_complexity_filter```
- - ``` --Y, --complexity_threshold```  == 50

```
#!/bin/bash
#SBATCH -t 120:00:00
#SBATCH --nodes=1 --ntasks-per-node=20
#SBATCH --mem=100GB
#SBATCH --account=putnamlab
#SBATCH --export=NONE
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=samuel_gurr@uri.edu
#SBATCH --output="%x_out.%j"
#SBATCH --error="%x_err.%j"
#SBATCH -D /data/putnamlab/sgurr/Geoduck_TagSeq/output/fastp_multiQC

# load modules needed
module load fastp/0.19.7-foss-2018b
module load FastQC/0.11.8-Java-1.8
module load MultiQC/1.7-foss-2018b-Python-2.7.15

# symbolically link 'clean' reads to hisat2 dir
ln -s ../../../../KITT/hputnam/20201217_Geoduck_TagSeq/*.fastq.gz ./

# Make an array of sequences to trim
array1=($(ls *.fastq.gz))

# fastp loop; trim the Read 1 TruSeq adapter sequence; trim poly x default 10 (to trim polyA)
for i in ${array1[@]}; do
	fastp --in1 ${i} --out1 clean.${i} --adapter_sequence=AGATCGGAAGAGCACACGTCTGAACTCCAGTCA --trim_poly_x 6 -q 30 -y -Y 50
        fastqc clean.${i}
done

echo "Read trimming of adapters complete." $(date)

# Quality Assessment of Trimmed Reads

multiqc ./ #Compile MultiQC report from FastQC files

echo "Cleaned MultiQC report generated." $(date)
```
#### Now lets see the multiQC report...

- looks much better!

![GC looks good](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/20210207_AFTER_polyx_and_lowcomplex.JPG "GC looks good")
