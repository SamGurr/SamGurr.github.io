---
layout: post
title: How to set up citation in R markdowns
date: '2023-01-21'
categories: Protocols
tags: citation zenodo Rmarkdown
---

Obj: Link citations within R markdown text for project files and manuscripts

Important hyperlinks:
* Followed the tutorial by Gertjan Verhoeven (his homepage [here](https://gsverhoeven.github.io/]))

* G. Verhoevan's tutorial link [here](https://gsverhoeven.github.io/post/zotero-rmarkdown-csl/) provides a simple step-by-step process

Main steps:

- install Zenodo
  - *set it up with your pdfs and citations!*

- install the Better BibTex for Zotero add-on ([website](https://retorque.re/zotero-better-bibtex/installation/) and down the xpi file [here](https://github.com/retorquere/zotero-better-bibtex/releases/tag/v6.7.52))

- In R markdown file, install the rbbt package from github as
      remotes::install_github("paleolimbot/rbbt")

- Restart R markdown again

- rbbt can be found under 'Addins' in R

* you can make a shortcut to use rbbt (your citation package tool) by navigating to Tools > Modify Keyboard Shortcuts and change the shortcut (likely default as absent!) or 'Insert Zotero citation' - type your desired shortcut, accept , and close

* restart R and open Zenodo (*Note*: **only** functions if Zenodo is also open!)

* in R markdown enter the shortcut you preciously assigned to access 'Insert Zotero citation'

* a window will open from Zotero to search your desired citation **you did it!**
