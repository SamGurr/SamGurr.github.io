---
layout: post
title: NADH dehydrogenase Pgenerosa Identification
date: '2020-03-17'
categories: Protocol
tags:  qPCR prep, blasp, blastn, Augustus, Muscle, Pfam, geoduck, protein
---

# OBJECTIVE
The following protocol was completed with the geoduck genome in preparation for primer design and qPCR of a target protein **NADH dehydrogenase (complex I)**
This step-by-step process can be used to verify the presence/absence of a particular target gene within an annotated genome without gene family identification.
In this case.. a database of the geoduck genome was used with only ID identifiers for genes (no family-specific accession ID)

# 1.) Create a fasta file query
 ### Objective: create a query of the nucelotide seq data *NADH_dehydrogenase_seq.fasta*
* targetted bivalve taxa and alternative oxidase - complied ~8 sequences from NCBI into a fasta file
NOTE: txt format can be converted into fasta by opening the file in sublime, notepad++ etc. and :savea." .fasta"
# **2.) Make a blast database**
### Objective: download the *P.generosa* reference genome (.fna) and convert to a blast database
#### SYNTAX in terminal *make blast database (nucleotides)*
* **makeblastdb.exe**
* **-in** ~/Documents/genomes/Panopea-generosa-genes.fna
* **-dbtyp** nucl
* **-title** Pgenerosa.GENES
* **-out** ~/Documents/genomes/Pgenerosa_database/Pgenerosa.GENES
* **-parse_seqids**
#### SYNTAX in terminal  *blastn (nucelotide) NADH_dehydrogenase_seq.fasta to the whole annotated database*
* **blastn**
* **-db** ~/Documents/genomes/Pgenerosa_database/Pgenerosa.GENES
* **-query**
* **-out** ~/Documents/blastdb/NADH_dehydrogenase_blastn_GENES.txt
* **-evalue** 0.001
* **-word_size** 11
* **-dust** no
* **-num_alignments** 1
* **-num_descriptions** 5
* **-task** blastn

NOTE: add *-outfmt* 6 == qsequid	ssequid	pident	length	mismatch	gapopen	qstart	qend	sstart	send	evalue	bitscore; *-outfmt* 11 == archive format;
*-num_descriptions* 5 == the five seqeunces with the highest bitscore

# **3.) View output**

### Objective: determine the gene(s) representative of the query/protein target (i.e. *NADH_dehydrogenase_seq.fasta*)
* PGEN_.00g299160 is the best hit!
* Here is the txt blastn file from bash showing a good alignment to the oyster seq
![PGEN_.00g299160 is the best hit!](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/NADH_Pgen_outfmt6_oysterhit.JPG "blastn outformat 6")

# **4.) Use Muscle in Jalview**
### Objective:
view the regions of overlap between the PGEN_.00g299160 gene and the NADH_dehydrogenase_seq fasta

![Putative exon regions!](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/NADH_Pgen_Muscle_jalview.JPG "Muscle screenshot")

# **4.) Augustus**
### Objective:
run sequence against a similar or related reference -- the reference applies a criteria of untraslated v. translated regions to identify and compile the coding region of an uploaded sequence.

* upload the PGEN_.00g299160 nucelotide sequence

* apply Pisaster as the reference (sea star)

NOTE: the output from Augustus give you your full coding sequence (nucleotides) and amino acid seq data for the putative full exon region (i.e. Pisaster as ref criteria)
![Augustus gff output](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/NADH_Pgen_Augustus.JPG "Augustus output")

# **4.) Pfam (Augustus follow-up)**
### Objective:
determine the protein family of the protein sequence output from Augustus.

* copy the protein sequence (nucleotide will give the same result) and paste into Pfam "Sequence Search" - press Go

* high evidence that PGEN_.00g299160 is NADH dehydrogenase! Focus on cover via "to and "end" of the Hidden-Markov-Model in relation to the HMM "length"

![Pfam result](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/NADH_Pgen_Pfam.JPG "NADH_dehydrogenase family")

# **5.) NCBI blastp (Augustus follow-up)**
### Objective:
determine the the sequences within NCBI with the highest %cover and %identity to your putative exon sequence from Augustus
NOTE: remember we used Pisaster as a reference criteria in Augustus to map UTRs and exons!

* copy the protein sequence and run blastp in NCBI

* high evidence that PGEN_.00g299160 is NASDH dehydrogenase and related to the bivalve taxa!!!

![NCBI blastp result](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/NADH_Pgen_blastn_NCBI.JPG "blastp NCBI")
