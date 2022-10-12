---
layout: post
title: AOX Pgenerosa identification
date: '2020-02-26'
categories: Protocol
tags: qPCR, protein, genome, augustus, blastp, jalview
---
# OBJECTIVE
The following protocol was completed with the geoduck genome in preparation for primer design and qPCR of a target protein Alternative oxidase
This step-by-step process can be used to verify the presence/absence of a particular target gene within an annotated genome without gene family identification.
In this case.. a database of the geoduck genome was used with only ID identifiers for genes (no family-specific accession ID)

# 1.) Create a fasta file query
 ### Objective: create a query of the nucelotide seq data *AOX_seq.fasta*
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
#### SYNTAX in terminal  *blastn (nucelotide) AOX_seq.fasta to the whole annotated database*
* **blastn**
* **-db** ~/Documents/genomes/Pgenerosa_database/Pgenerosa.GENES
* **-query**
* **-out** ~/Documents/blastdb/AOX_blastn_GENES.txt
* **-evalue** 0.001
* **-word_size** 11
* **-dust** no
* **-num_alignments** 1
* **-num_descriptions** 5
* **-out** haktan.txt
* **-dust** no
* **-task** blastn

NOTE: add *-outfmt* 6 == qsequid	ssequid	pident	length	mismatch	gapopen	qstart	qend	sstart	send	evalue	bitscore; *-outfmt* 11 == archive format;
*-num_descriptions* 5 == the five seqeunces with the highest bitscore

# **3.) View output**

### Objective: determine the gene(s) representative of the query/protein target (i.e. *AOX_seq.fasta*)
![PGEN_.00g108770 is the best hit!](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/AOX_blastn_outfmt6.JPG "blastn outformat 6")

# **4.) Use Muscle in Jalview**
### Objective:
view the regions of overlap between the PGEN_.00g108770 gene and the AOX_seq fasta

![Putative exon regions!](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Muscle_Jalview_AOX.JPG "Muscle screenshot")

* many regions without overlap -- likley untraslated regions (UTRs)

![UTRs](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Muscle_Jalview_AOX_introns.JPG "Muscle screenshot 2")

# **4.) Augustus**
### Objective:
run sequence against a similar or related reference -- the reference applies a criteria of untraslated v. translated regions to identify and compile the coding region of an uploaded sequence.

* upload the PGEN_.00g108770 nucelotide sequence

* apply Pisaster as the reference (sea star)

NOTE: the output from Augustus give you your full coding sequence (nucleotides) and amino acid seq data for the putative full exon region (i.e. Pisaster as ref criteria)
![Augustus gff output](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Augustus_Pgen_Pisaster.JPG "Augustus output")

# **4.) Pfam (Augustus follow-up)**
### Objective:
determine the protein family of the protein sequence output from Augustus.

* copy the protein sequence (nucleotide will give the same result) and paste into Pfam "Sequence Search" - press Go

* high evidence that PGEN_.00g108770 is AOX! Focus on cover via "to and "end" of the Hidden-Markov-Model in relation to the HMM "length"

![Pfam result](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Pfam_augustus_followup.JPG "AOX family")

# **5.) NCBI blastp (Augustus follow-up)**
### Objective:
determine the the sequences within NCBI with the highest %cover and %identity to your putative exon sequence from Augustus
NOTE: remember we used Pisaster as a reference criteria in Augustus to map UTRs and exons!

* copy the protein sequence and run blastp in NCBI

* high evidence that PGEN_.00g108770 is AOX and related to the bivalve taxa!!!

![NCBI blastp result](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/NCBI_blastp_Augustus_followup.JPG "blastp NCBI")
