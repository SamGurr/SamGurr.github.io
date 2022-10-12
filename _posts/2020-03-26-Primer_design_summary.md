---
layout: post
title: Primer Design
date: '2020-03-26'
categories: Protocol
tags:  primer, design, qPCR prep, blasp, blastn, Augustus, Muscle, Pfam, geoduck, protein
---

# Read.me
The following is a condensed summary of computational work from blast gene identification to primer testing in preparation for qPCR.

---------------------------------

#### About the Panopea generosa genome file
* 34,947 accession IDs / putative genes

*syntax*: grep -c "^>" <genome_fasta_file.fa>

* This genome does not contain gene function info (i.e. accession IDs = Pgen_.008050)

---------------------------------

| Steps | About |
|----|-----|
|  I | Assemble fasta files of target genes |
|  II | Blast against genome |
| III  | Verify putative gene function  |
|   | - Muscle (with Jalview)  |
|   |  -  Augustus |
|   | - Pfam & NCBI blast  |
| IV  | Design primers  |
|   | - primer3  |
|   | - EMBOSS  |
**Note** | - all steps were completed on a local PC laptop with Windows 10; *not all syntax can be completed in git bash!!* (e.g. Ubuntu Linux for Windows was necesasry to download and use primersearch steps in EMBOSS)
| | - simplified syntax and images given when applicable

---------------------------------
## I.) Assemble fasta files of target genes

### **A. Use NCBI to search the protein or nucleotide seqences of related taxa**

*Example*:

My genome = Pacific Geoduck

NCBI fasta tagets = marine bivalves (Crassostra nirginica/gigas, Mytilus sp., Mercenaria, A. islandica, etc.)

### **B. Assemble gene query or queries**
Query = fasta file for a gene to blast against a database. Simply copy and paste the accession ID and nucleootide / protein sequences from NCBI to a text editor (i.e. sublime, notepad++, atom, etc.). Save as "date.created_gene.fasta" to your desired local folder.

*Examples*:

My current qPCR targets have significance for mithchondrial function and oxidative status;
1) Alternate oxidase;
2) NADH dehydrogenase (complex I);
3) Cytochrome c reductase (complex III);
4) Uncoupling protein (Mitchondrial carrier; UPCs)

---------------------------------
## II.) Blast against genome

### **A. Make a blast database for the genome fasta**
 NOTE:  in this case, 34,947 putative genes!

Program(s) needed:

- blast

#### *Sytnax*:

**makeblastdb.exe**

**-in**  <genome_fasta_file.fna> *# you genome - in this case the Panopea generosa genome*

**-dbtype** nucl       *# assuming your genome is nucleotide seq*

**-title**  <myspecies.GENES>  *# database tag to call in blast*

**-out**  <folder_desination_here/myspecies.GENES> *# where are you putting it?*

**-parse_seqids**

### **B. Blast away!!!**


*Note*: are your queries proteins or nucleotides?

When using blast against a nucleotide database (from step II.A.)
- Query as proteins... **use tblastn** (protein query to nucleotide database)
- Query as nucleotides... **use blastn** (nucleotide query to nucleotide database)

#### *Syntax*:

**blastn** *# for nuleotide to nucleotide, change to tblastn for protein to nucleotide*

**-db** <folder.desitnation../Pgenerosa.GENES> *# call the folder where your database is from II.A.*

**-query** <20200325_Alternate_oxidase.fast> *# call your query for one of your gene targets - in this case it is nucleotides seq data of Alternate oxidase assembled with various bivlave taxa from NCBI, this must be nucleotides due to the blastn function*

**-evalue** 0.001 *# threshold criteria to print "hits" of your query to genome*

**-word_size** 11 *# note: word size must be less than 8 to do tblastn*

**-dust** no

**-num_alignments** 1

**-num_descriptions** 1

**-task** blastn *# redundant but good to use*

**-outfmt** 11 *# IMPORTANT!! this number determines what your output will look like and should alse determine what your -out title is based on the format. I typically print THREE versions for each blast: (1) no outformat. leave "-oufmt" out to print reader-firendly format by gene (2) -oufmt 6 prints a summary of ONLY HITS (3) -outfmt 11 prints the raw syntax by blast

**-out** <folder.destination.../output_title.txt> *# note the output title is largely influenced by the outfmt number!!*

---------------------------------

## III.) Verify putative genes in target genome

### **A. View your blast outputs**

* the most critical information is from the -outfmt 6 output files. This file compiles all hits of your query to the genome database, but ddoes not include every accesion in your query. Important information here is accession ID of your genome database hit and the strength to the query
* Do you see a pattern of repeated strong hits with same accession ID? This is good supporting evidence that this may be your gene of interest.
* Take not of all genes that hit well to your query. Keep in mind that your fasta file compiled from NCBI might have some sequences that are close to, but not exacly your target. Thus, some of your hits may be strong but not related to your exact protein/gene family of interest.

### **B. Seqeunce alignment in Muscle (Optional)**

* **Jalview** is a great alignment program that I highly recommend for this!
* load in your query to Jalview
* Open your genome fasta file and Cntrl-F (find) for the accession ID with high strength or a consistant pattern of hits from your -outfmt 6 file. Copy/paste that the nucleotide seq and accession ID of this putative gene from your genome into Jalview (go to File - add to do this)
* use "Muscle with Defaults" in Jaview to make an alignment.
* Scroll through this output - you will likely see that there are long extensions wihtout alignment and occasional islands of nearly ubiqquitous overlap with your query fastas. This is indicative of the untraslated regions (UTRs) and gene-coding regions. Pretty cool!!!

### **C. Compile gene coding regions with Augustus**

* **online interface works great!** http://augustus.gobics.de/ click "web interface". Change "organism" in the scroll down menu to taxa closest to your genome. In my case I used Pisaster - an intertidal echinoderm in the Pacific Northwest of North America within Pacific geoduck habitat. Although this is not the same phyla, it should work well.
* **What does this program do?** Augustus uses a reference criteria (in this case Pisaster genome) to identify untraslated v. translated regions of an input nucleotide sequence
* **What does the output say?*** The ouput from Augustus will show you the regions of coding and non-coding for putative gene function and compile both the nucleotide and protein sewuence of ALL CODING REGIONS.
* here is an example of an output from Augustus. The nucelotide seq and protein seq of compiled coding sequences are listed at the bottom of the image
![Augustus gff output](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/NADH_Pgen_Augustus.JPG "Augustus output")

### **D. Identify gene family in Pfam and NCBI**

* Copy the protein sequence ouput from Augustus and paste into Pfam https://pfam.xfam.org/ under "Seqeunce Search" - remove all spaces and non-viable characters (you will get #s from the Augustus output, delete these). Press "Go" and wait for Pfam to do its thing.
* You may not get an output from Pfam from your putative protein sequence. There are a few reasons to speculate... Is your orignal fasta targetting the correct gene? Is this gene realtively conserved?
* *If you do not get a Pfam output* not all is lost! Try to blast it in NCBI to see what this sequence is coded for. This may help you with your thought process to repeat or readjust previous steps

* here is an example of an output from Pfam. Displays a single family hit for alternate oxidase from the compiled coding-region sequence copied/pasted from Augustus.
![Pfam result](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Pfam_augustus_followup.JPG "AOX family")

* **important to also run your target sequence in NCBI** try both the full nucelotide sequence AND the compiled gene coding regions from Augustus. The full nuceleotide will likely provide hits close to your target taxa.

### **Synthesize your evidence - enough to move forward *for primers*?**

---------------------------------

## IV.) Design primers

**Step IV follows Sam White's notebook entries (Roberts Lab @ University of Washington)**
- check out his notebook here: https://robertslab.github.io/sams-notebook/about.html Sam White includes every detail on this process and there is also troubleshooting information on the Roberts lab resources page here: https://github.com/RobertsLab/resources/issues

Programs to download..

1. Primer3 - https://sourceforge.net/projects/primer3/
2. EMBOSS - ftp://emboss.open-bio.org/pub/EMBOSS/

### **A. Primer3.**

* **Imporant!** You must create a parameters.txt file for your target gene (e.g. gene_target_PARAMS.txt)
* This will look like the following:

SEQUENCE_ID=ACCESSION ID
SEQUENCE_TEMPLATE=**YOUR_RAW_SEQUENCE**
PRIMER_TASK=generic
PRIMER_PICK_LEFT_PRIMER=3
PRIMER_PICK_RIGHT_PRIMER=3
PRIMER_OPT_SIZE=18
PRIMER_MIN_SIZE=15
PRIMER_MAX_SIZE=21
PRIMER_MAX_NS_ACCEPTED=1
PRIMER_PRODUCT_SIZE_RANGE=75-150
P3_FILE_FLAG=1
PRIMER_EXPLAIN_FLAG=1
PRIMER_THERMODYNAMIC_PARAMETERS_PATH=**full path to /primer3_config/**

=

NOTE:

**YOUR_RAW_SEQUENCE** - must be a single line WITHOUT any spaces. For example, this can be done on a text wditor such as notepad++ (cntrl+j for a single line and cntl+f to open window and find/replace spaces)

**full path to /primer3_config/** - this is a common source of error when running primer3, make sure with navigates to primer3_config!

* **Run primer3_core.exe  to get primers!**

#### *Syntax*:

**primer3/src/primer3_core.exe** *# call the program primer3_core.exe*

**>** *# (1) with ">" outputs a defaults file will all info, (2) without ">" outputs a reader-friendly view of the primer selection with descriptive information also included in defaults*

**--format_output**

**--output=<folder.destination/gene_primers_OUTPUT.txt>  <folder.location/gene_target_PARAMS.txt>**

* for more information check out my MARDOWN FILE on Github! https://github.com/SamGurr/Intragenerational_thresholds_OA/blob/master/qPCR/Primer3_EMBOSS/20200324_primer_design.md


### **B. EMBOSS.**

#### **Why run EMBOSS on my primers from primer3?**

The function I run (following Sam White's process) is **primersearch** in EMBOSS. This basically acts as a **high powered "Find" function** (Cnrt+F) of your primer sequnece to a fasta file. In your case the fasta file contains ~35k accession IDs likely millions of basepairs! In addition, the primersearch will **prints the accession ID where your primer was found!** This is very useful to **verify your primers are diagnostic to the target gene** before purchasing to run qPCR.

NOTE: To download EMBOSS and use primersearh **git bash will NOT work** Linux for Windows (Ubuntu) works well

#### *Syntax*:
* the following uses grep to get the seqeunce ID and left and right primer outputs from your defaults file to create a file readable by EMBOSS.

**seq_id**=$(grep "SEQUENCE_ID=" <path_to_defaults_file/primer3_defaults.txt>  | sed 's/SEQUENCE_ID=//')

**left_primer**=$(grep "PRIMER_LEFT_0_SEQUENCE="  <path_to_defaults_file/primer3_defaults.txt>  | sed 's/PRIMER_LEFT_0_SEQUENCE=//')

**right_primer**=$(grep "PRIMER_RIGHT_0_SEQUENCE="  <path_to_defaults_file/primer3_defaults.txt>  | sed 's/PRIMER_RIGHT_0_SEQUENCE=//')

**printf** "%s\t" "${seq_id}" "${left_primer}" "${right_primer}" > path_destination/_emboss_file.txt

* Add newline to end of file to read it with EMBOSS

**printf** "\n" >> <path_to_emboss_file/_emboss_file.txt>

#### **Time to run primersearch EMBOSS on your emboss_file.txt!**

#### *Syntax*:

**path_to_EMBOSS/EMBOSS-6.6.0/emboss/primersearch**

**-auto**

**<path_to_ref_fasta/ref.fna>**

**<path_to_emboss_file/_emboss_file.txt>**

* What does your output say?
The ouput will print the seq ID of your emboss.txt file and the ID(s) of the matches it found in your reference fasta. In the image below we see that the emboss.txt ID and the genome ID match and there are zero other matches in the genome. This is great evidence that qPCR will solely target this one sequence with the primer output from primer3!
![EMBOSS](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/EMBOSS_AOX_output.JPG "EMBOSS output")
