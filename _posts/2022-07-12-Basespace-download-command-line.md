---
layout: post
title: Download Illumina seq data to personal computer (using cmd line)
date: '2022-07-12'
categories: Processing
tags: DNA, Illumina, raw data, basespace, command line, RNA
---

## Illumina Basespace --> personal computer (using cmd line):
----------
How to download FASTQ files from basespace through the command line

If you do not already have it, download the cli file from https://developer.basespace.illumina.com/docs/content/documentation/cli/cli-overview
  the file will likely download as the name 'bs'.

Put this file in a folder titled BSCLI (can be in Documents, Desktop, etc.)

Open command line and navigate ('cd') to the BSCLI folder (now with te downloaded bs file inside)

type 'bs auth' in command line to authenticate - this will give you a URL to accept authentification
nav to the URL and authenticate

type 'bs list projects' to receive your project ID (not your job number!) - you will use this ID
for the 'bs download project' command below...

Into the command line type:

bs download project -i <ProjectID> -o <output> --extension=fastq.gz

       *** Project ID can be found in the URL when you have your project open on basespace (NOT the job#) - this is acheived with 'bs list projects'

EXAMPLE:

bs download project -i 351294949 -o C:\Users\samjg\Documents\Raw_seq_data\2022_Airradians_TagSeq --extension=fastq.gz

Execute the command line and it will begin downloading the files to the designated folder (<output>)

Troubleshooting:

Need to be in the C: drive, but sometimes it defaults to teh H: drive

to check use:
	echo %HOMEDRIVE%
If you need to change it to C drive use:
	set HOMEDRIVE=C:

May beed to authenticate. Be sure upi are in the base space folder
	...\Desktop\BSCLI
use the comand
	bs auth
