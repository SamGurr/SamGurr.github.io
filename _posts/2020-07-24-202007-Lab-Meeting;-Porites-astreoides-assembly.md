---
layout: post
title: 202007-Lab Meeting; Porites astreoides assembly
date: '2020-07-24'
categories: overview
tags: overview, coral, porites, lab meeting, trininty, trinotate, busco
---

# Porites astreoides transcriptome assembly

## Table of Contents
  - [1. Quality & Trim](#1-Assess-quality-of-reads-using-FastQC-and-trim-using-fastq)
  - [2. *De novo* Transcriptome Assembly](#2-De-novo-transcriptome-assembly-with-Trinity)
    - [2.1 What is Trinity?](#21-What-is-Trinity)
  - [3. Assembly completeness](#3-Assembly-completeness)
    - [3.1 Methods and tools to test](#31-Methods-and-tools-to-test)
      - [BUSCO](#BUSCO)
      - [Orthofinder](#Orthofinder)
      - [Alignment](#Alignment-to-related-species-transcriptomes)
  - [4. Annotate the assembly](#4-Annotate-the-assembly)

-------

# Example pipelines for RNAseq and *de novo* gennome assembly

* [Holzer and Marz, 2019](https://watermark.silverchair.com/giz039.pdf?token=AQECAHi208BE49Ooan9kkhW_Ercy7Dm3ZL_9Cf3qfKAc485ysgAAArowggK2BgkqhkiG9w0BBwagggKnMIICowIBADCCApwGCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQM1XrEyX8vopR0xjmZAgEQgIICbbyfMmevYUVAJ64h-hRStbmfLG5V-NwzIso9KTu4334Vzoebw6jn-4sS6I7Qc65XkIPw3W1IkCdyyuOfMpDf5_o9UBG7eGLv74VZ2arf2TMvUFL34fGF9mDJYApAGOpBKMcrf23ddaJ2VKHYEWuSwMC81OHU2awRWYc02Uo0chb3gsvdZYjfbeQ04sGHjq3JqQafiWoS8_Z7fTRo7F7D1QBfb0wgKP1AOgfPct1HIRZ--YeyFuEqUMBQUll22DfAsOm0qFv0ywczInxqrxADzEyFodCZRA60V_CctPAsNG-1vgBxq61_8ld_bPGCkCSkXFXzT0K53OfoOh9sOly1J-MIZC-GubllQoHFMk2obgTErq-C0QhL-YI-ZlwKE69vrDgDXEze20VUY1sspJLGNtxXIx4tzHOQTlTx7NLB_0e6QoCCEBaBXNI4g3M4mIa4UpqtXaCdgVUgbvNaefJe_os1B2-aoMAbtihQBGgyHARszcDnfOZB52yMWxk1a8dpSIq_EVg_eEWNsESQZQeCQVhuTxl3Ngh0Vp226mEtF7irAdZW3Snnh9oZz8Y7-cNDFWxsjb1sS_pJEEj6ViRDbEf2cOgmVq1n1jdRMDoyoxb5r8F6wL28lNIrISkMv0_hnv1UNSSQb2yEmYHJNw7EXOmDTnKe7dATNuAb_DP3rVdvTDGPgPgh0FQeRp7Ed7zgqJbGMDU8K6_OmJZUwYOiDOSOAf1RVEDUuqb-nw0oI3P1nPvDHedO39m1I3V_D8beFExAptXDAmQQRknfKJLwAUQ9ceEZVJVeUr6i78bdN-wj8mgjeTh7KK4QUwclIQ)

![assembly_pipeline_example](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/assembly_pipeline_example.JPG "assembly_pipeline_example")


* [Carruthers et al. 2018](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5759245/)


![assembly_pipeline_example_2](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/assembly_pipeline_example_2.JPG "assembly_pipeline_example_2")

-------

# 1. Assess quality of reads using FastQC and trim using fastq

-------

# 2. De novo transcriptome assembly with Trinity
Current files:
- Sample2_R1.fastq.gz
- Sample2_R2.fastq.gz
- Sample3_R1.fastq.gz
- Sample3_R2.fastq.gz
- Sample4_R1.fastq.gz
- Sample4_R2.fastq.gz
- Sample5_R1.fastq.gz
- Sample5_R2.fastq.gz
- Past.md5

## 1.1 Checking the files downloaded correctly (cksum)

For small jobs in Bluewave, turn on "interactive mode"

```
interactive
```

Create a seccondary md5 file with uploaded files to compare to original md5

```
md5sum *.fastq.gz > Past_20200729.md5
```

Use 'cksum' to compare md5 files

```
cksum Past.md5 Past_20200729.md5
```

The output should look like this:
```
1158401968 432 Past.md5
282010279 432 Past2.md5
```

The first number is the cksum ID and the second number is the size of the file (in bytes).
Since both files are the same, this suggests the transfer of files did not corrupt any of the files.

```
less Past.md5
```

```
c9251a9b98768edd205724ed12c1c2a8  Sample2_R1.fastq.gz
21139f87ce4d0f4b293059a0020122e1  Sample2_R2.fastq.gz
173692a008fef82c0aecd55890eb985c  Sample3_R1.fastq.gz
962cf69dfcd1384c7f7ce3a792454ab6  Sample3_R2.fastq.gz
adf57023019e4c07fc8e5627db0faad7  Sample4_R1.fastq.gz
680ac6e4b9c4fead8f2f7a195b14dd79  Sample4_R2.fastq.gz
63c622d7c0e7093b537d0f3efd3c48c4  Sample5_R1.fastq.gz
4df8c11d45958e9081aead7d40a9386a  Sample5_R2.fastq.gz
```

```
less Past_20200729.md5
```

```
c9251a9b98768edd205724ed12c1c2a8  Sample2_R1.fastq.gz
21139f87ce4d0f4b293059a0020122e1  Sample2_R2.fastq.gz
173692a008fef82c0aecd55890eb985c  Sample3_R1.fastq.gz
962cf69dfcd1384c7f7ce3a792454ab6  Sample3_R2.fastq.gz
adf57023019e4c07fc8e5627db0faad7  Sample4_R1.fastq.gz
680ac6e4b9c4fead8f2f7a195b14dd79  Sample4_R2.fastq.gz
63c622d7c0e7093b537d0f3efd3c48c4  Sample5_R1.fastq.gz
4df8c11d45958e9081aead7d40a9386a  Sample5_R2.fastq.gz
```

Looks the same.

Don't forget to exit interactive mode!
```
exit
```


* Location of fasta.gz files on bluewaves
* **data/putnamlab/sgurr/P.astreoides_assembly_proj/Past_transcriptome**



## 1.2 Quality control of raw sequencing reads (FastQC and MultiQC)
https://github.com/s-andrews/FastQC
https://github.com/ewels/MultiQC

Make a scripts folder to stay organized.
```
mkdir scripts
cd scripts
```

Making a shell script to assess the quality of the reads using FastQC and summarizing the results using FastQC.

#### Location: **data/putnamlab/sgurr/P.astreoides_assembly_proj/scripts_2**
```
nano multiqc_fastqc_ALL_raw.sh
```

```
#!/bin/bash

#SBATCH --job-name="fast_multi_qc_clean_P.ast"
#SBATCH -t 100:00:00
#SBATCH --nodes=1 --ntasks-per-node=20
#SBATCH --export=NONE
#SBATCH --output="%x_out.%j"
#SBATCH --error="%x_err.%j"
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=samuel_gurr@uri.edu
#SBATCH --account=putnamlab
#SBATCH -D /data/putnamlab/sgurr/P.astreoides_assembly_proj/Past_transcript$

module load FastQC/0.11.8-Java-1.8
module load MultiQC/1.7-foss-2018b-Python-2.7.15

fastqc *fastq.gz .
echo -n "Finished FastQC:"

multiqc .
```

Running the shell script.

```
sbatch multiqc_fastqc_ALL_raw.sh
```

```
scp -r  <EMAIL@BLUEWAVES.URI.EDU>:/<BLUEWAVES.FILEPATH>/multiqc_report.html /<COMPUTER.FILEPATH>/
```


## 1.4 Quality control using fastp

https://github.com/OpenGene/fastp


```nano fastp_ALL.sh```

 loop fastp through left and right sequences; used the tutorial here: https://bash.programmingpedia.net/en/knowledge-base/11215088/bash-shell-script-two-variables-in-for-loop

#### Location: **data/putnamlab/sgurr/P.astreoides_assembly_proj/scripts_2**

```
#!/bin/bash

#SBATCH --job-name="fastp_raw_twosample_P.ast"
#SBATCH -t 100:00:00
#SBATCH --nodes=1 --ntasks-per-node=20
#SBATCH --export=NONE
#SBATCH --output=../../output_2/fastp_out/"%x_out.%j"
#SBATCH --error=../../output_2/fastp_out/"%x_err.%j"
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=samuel_gurr@uri.edu
#SBATCH --account=putnamlab
#SBATCH -D /data/putnamlab/sgurr/P.astreoides_assembly_proj/Past_transcriptome/All_transcriptome_samples

module load fastp/0.19.7-foss-2018b

fwd_array=($(ls *R1.fastq.gz))
rev_array=($(ls *R2.fastq.gz))
for ((i = 0; i < ${#fwd_array[@]} && i < ${#rev_array[@]}; i++)); do
         fastp --in1 ${fwd_array[i]} --in2 ${rev_array[i]} --out1 ../../output_2/fastp_out/clean.${fwd_array[i]} --out2 ../../output_2/fastp_out/clean.${rev_array[i]} -$[i]} --cut_front 20 --cut_tail 20  --cut_window_size 5 --trim_front1 3  cut_mean_quality 30 -q 30 --adapter_sequence=AGATCGGAAGAGCACACGTCTGAACTCCAGTCA -adapter_sequence_r2=AGATCGGAAGAGCGTCGTGTAGGGAAAGAGTGT --json ../../output_2/fastp_out/fastp.json  --html ../../output_2/two_samples/fastp.html
done

echo -n "Finished fastp:"
"
```

Count the reads before and after trimming to compare the reduction in size

### Raw reads:
#### original raw reads from data/putnamlab/sgurr/P.astreoides_assembly_proj/Past_transcriptome/All_transcriptome_samples
```
zgrep -c "@C" Sample*.fastq.gz
```
Sample2_R1.fastq.gz:9869330
Sample2_R2.fastq.gz:9869330
Sample3_R1.fastq.gz:8471009
Sample3_R2.fastq.gz:8471009
Sample4_R1.fastq.gz:8244565
Sample4_R2.fastq.gz:8244565
Sample5_R1.fastq.gz:8920953
Sample5_R2.fastq.gz:8920953

```
zgrep -c "@NB" KW*.fastq.cleaned.gz
```

KW1_S10_LALL_R1.fastq.gz:29961296
KW1_S10_LALL_R2.fastq.gz:29961296
KW2_S2_LALL_R1.fastq.gz:94259322
KW2_S2_LALL_R2.fastq.gz:94259322


### Cleaned reads output from fastp above:
#### output trim 'clean' data in  data/putnamlab/sgurr/P.astreoides_assembly_proj/output_2/fastp_out

```
zgrep -c "@C" clean.Sample*.fastq.gz
```
clean.Sample2_R1.fastq.gz:8726675
clean.Sample2_R2.fastq.gz:8726675
clean.Sample3_R1.fastq.gz:7255348
clean.Sample3_R2.fastq.gz:7255348
clean.Sample4_R1.fastq.gz:7237699
clean.Sample4_R2.fastq.gz:7237699
clean.Sample5_R1.fastq.gz:7673755
clean.Sample5_R2.fastq.gz:7673755

```
zgrep -c "@C" clean.KW*.fastq.gz
```

clean.KW1_S10_LALL_R1.fastq.gz:28711125
clean.KW1_S10_LALL_R2.fastq.gz:28711125
clean.KW2_S2_LALL_R1.fastq.gz:87991607
clean.KW2_S2_LALL_R2.fastq.gz:87991607

## 1.5 Quality control of trimmed sequencing reads (FASTQC)

```

Make a shell script to assess the quality of the trimmed reads

```
nano multiqc_fastqc_ALL_clean.sh
```

```
#!/bin/bash

#SBATCH --job-name="fast_multi_qc_clean_P.ast"
#SBATCH -t 100:00:00
#SBATCH --nodes=1 --ntasks-per-node=20
#SBATCH --export=NONE
#SBATCH --output="%x_out.%j"
#SBATCH --error="%x_err.%j"
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=samuel_gurr@uri.edu
#SBATCH --account=putnamlab
#SBATCH -D /data/putnamlab/sgurr/P.astreoides_assembly_proj/output_2/fastp_out

module load FastQC/0.11.8-Java-1.8
module load MultiQC/1.7-foss-2018b-Python-2.7.15

fastqc *fastq.gz .
echo -n "Finished FastQC:"

multiqc .
echo -n "Finished multiqc:"
```

Export the MultiQC report to view. It should be an HTML file.
```
scp -r  <EMAIL@BLUEWAVES.URI.EDU>:/<BLUEWAVES.FILEPATH>/multiqc_report.html /<COMPUTER.FILEPATH>/

]


-------

##  2.1 What is Trinity?

*Trinity wiki page here* https://github.com/trinityrnaseq/trinityrnaseq/wiki

*Trinity publication* https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3571712/

*Trinity downstream analysis publication* https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3875132/

- Trinity is used fro de novo assembly of RNA-seq data from the illumina platform
- *de novo* in bioinformatics referes to genome assembly based on read data **without** use of a reference
- *The following is a summary of the github wiki above...*
  - assembles the RNA into full-length transcripts or dominant isoforms of genes (contigs) and reports  only the unique portion of the alternativel spliced isoforms (*Inchworm*)
  - takes the output and runs *de Bruijn* graphs to form gene clusters (*Chrysalis*)
  - processes the *de Bruijn* graphs and reports the full-length transcripts for all isoforms of each gene (*Butterfly*)

- What is a *de Bruijn* graph?

*Read about de Bruijn graphs here (image below)* https://homolog.us/Tutorials/book4/p2.1.html

- below is an image of a *de Bruijn* graph
  - this simplified example shows a contructed sequence by splitting into k-mers (k=7 or 7-mers) that connect to form the putative sequence assembly with an overlap of 6 nt or k-1

![debruijn_graph](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/debruijn_graph.JPG "debruijn_graph")

#### Trinity shell script  *(not tested!)*:

cat all clean .gz files and cp from fastp_out to trinity_5

##### Location: **data/putnamlab/sgurr/P.astreoides_assembly_proj/output_2/trinity_5**

##### Files:
* **clean.Sample_ALL_R1.fastq.gz** = all R1 (right) seq files
* **clean.Sample_ALL_R2.fastq.gz** = all R2 (left) seq files

Make a shell script to assess the quality of the trimmed reads (**data/putnamlab/sgurr/P.astreoides_assembly_proj/scripts_2**)

```
nano multiqc_fastqc_ALL_clean.sh
```
```
#!/bin/bash

#SBATCH --job-name="Trinity_clean_P.ast"
#SBATCH -t 200:00:00
#SBATCH --nodes=1 --ntasks-per-node=20
#SBATCH --export=NONE
#SBATCH --output="%x_out.%j"
#SBATCH --error="%x_err.%j"
#SBATCH --mail-type=BEGIN,END,FAIL
#SBATCH --mail-user=samuel_gurr@uri.edu
#SBATCH --account=putnamlab
#SBATCH --mem=500GB
#SBATCH --exclusive
#SBATCH -D /data/putnamlab/sgurr/P.astreoides_assembly_proj/output_2/trinity_5/

module load Trinity/2.9.1-foss-2019b-Python-3.7.4

Trinity --seqType fq --left clean.Sample_ALL_R1.fastq.gz  --right clean.Sample_ALL_R2.fastq.gz --CPU 20 --max_memory 500G --full_cleanup

```

##### Output: **data/putnamlab/sgurr/P.astreoides_assembly_proj/output_2/trinity_5**

# 3. Assembly completeness

##### Why assess assembly 'completeness' in your workflow?

- important to verify the quality of the assembly (i.e. gaps, inconsistancies in contig connection and direction) using ortholog markers before moving forward in downstream annotation and analysis

## 3.1 Methods and tools to test

#### BUSCO ( Benchmarking Universal Single-Copy Orthologs)
- uses highly conserved single-copy orthologs; evolutionary informed expectations of gene content.
- appears that youu can focus a BUSCO analysis to orthologs related to your target taxa.

- image below shows a BUSCO analysis comparing the crayfish targetted for tde novo transcriptome assembly to 44 other arthropod species assemblies and a single vertebrate assembly:

*Theissinger et al. 2016* https://www.sciencedirect.com/science/article/abs/pii/S1874778716300137

Citation: Theissinger, K., Falckenhayn, C., Blande, D., Toljamo, A., Gutekunst, J., Makkonen, J., ... & Kokko, H. (2016). De Novo assembly and annotation of the freshwater crayfish Astacus astacus transcriptome. Marine Genomics, 28, 7-10.

![busco_analysis](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/busco_analysis.JPG "busco_analysis")


#### Orthofinder
- uses all-v-all BLAST to assess completeness of your assembly

*Paper comparing BUSCO and orthofinder* https://genome.cshlp.org/content/early/2019/06/21/gr.243212.118.full.pdf

Altenhoff, A. M., Levy, J., Zarowiecki, M., Tomiczek, B., Vesztrocy, A. W., Dalquen, D. A., ... & Dessimoz, C. (2019). OMA standalone: orthology inference among public and custom genomes and transcriptomes. Genome research, 29(7), 1152-1163.

- authors found Orthofinder detected more othologous groups than other methods...

![assembly_completeness_fig](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/assembly_completeness_fig.JPG "assembly_completeness_fig")

#### Alignment to related species transcriptome(s)
 - Publicly available transcriptomes available on NCBI:
      - *Porites astreoides*
      -  Related taxa



-------

# 4. Annotate the assembly
