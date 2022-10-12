---
layout: post
title: Multivariate Analysis DESeq2
date: '2021-02-20'
categories: analysis
tags: DESeq2, TagSeq, mRNA, differential expression, stats, model design, multivariate
---

## Tips on multivariate analysis in DESeq2

### Links:

* TagSeq repo: [github](https://github.com/SamGurr/Pgenerosa_TagSeq_Metabolomics) & [OSF](https://osf.io/ydmt5/)
* Bioconductor DESeq2 online tutorial: [here](http://bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html)

------------------
## Experimental deign and rationale for multivariate analysis of DE data


![Exp_design](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/TagSeq_Exp_design.JPG "Exp_design")

**Figure. Experimental design** in our repeated reciprocal OA experiment in 2019. Details on the resulting phenotypic response can be found in our preprint here: [Gurr et al.](https://www.biorxiv.org/content/10.1101/2020.08.03.234955v1.full)


![SizeAFDW_summary_res](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/SizeAFDW_summary_res.JPG "SizeAFDW_summary_res")

![TAOC](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/TAOC_summary_res.JPG "TAOC")

**Phenotypic response** We conclude that early moderate stress acclimation (primary treatment) elicited a larger phenotype associated with lower CSR suggesting plasticity of bioenergetic and subcellular responses to OA in pediveliger-juvenile geoduck.

-------------------------
## Multivariate analysis in DESeq2

![Exp_design_cartoon](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/TagSeq_Exp_design_cartoon.JPG "Exp_design_cartoon")

**Figure.** Another way of looking at the experimental design stated above - with levels to reference the DESeq2 models presented below

![TagSeq_Exp_design_ques](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/TagSeq_Exp_design_ques.JPG "TagSeq_Exp_design_ques")

**QUESTION!** How do we properly address the *main effect* such as the response to primary treatment after second and third exposures? (**displayed above**)

#### DESeq2 model design (after a subsequent 'Second' exposure)

* **Full** model (with interaction term) ==

```design = ~ Second_Treament+Primary_Treatment+Second_Treament:Primary_Treatment```

* **Additive/Main Effects** model (w/o interaction term) ==

```design = ~ Second_Treament+Primary_Treatment```

* **Group as 'All_Treatment'** model (all contrasts of treatment groups)==

```All_Treatment = paste(Primary_Treatment, Second_Treament, sep ='')```

  ```design = ~ Group - 1```

*NOTE*: it may appear the the 'Full' model is to correct model to address treatment effects - this is what you would with a stat such as ANOVA. However, DESeq2 investigates pairwise differences. Further, keep in mind that interaction terms output by models such as the 'Full' design stated above will have pairwise results in response to the **reference level of your treatments!!!**

**What does this mean??**

Consider the following result names output by these models...

### Results of DESeq2 models

Remember the *levels* of primary treatment and second treatment from the figure above...

* **Full** model (with interaction term) ==

```> resultsNames(dds.full) "Intercept"  "Second_Treament_M_vs_A"     "Second_Treament_S_vs_A"    "Primary_Treatment_M_vs_A" "Second_TreamentM.Primary_TreatmentM" "Second_TreamentS.Primary_TreatmentM" ```

* **Additive/Main Effects** model (w/o interaction term) ==

```> resultsNames(dds.main) "Intercept"                "Second_Treament_M_vs_A"   "Second_Treament_S_vs_A"  "Primary_Treatment_M_vs_A"```

* **Group** model (all contrasts of treatment groups)==

```> resultsNames(dds.group) "All_TreatmentAA" "All_TreatmentAM" "All_TreatmentAS" "All_TreatmentMA" "All_TreatmentMM" "All_TreatmentMS"```

### **now lets explore the results of the PRIMARY treatment effect ONLY...**

* **Full model** ==

```results(dds.d7, contrast = c("Primary_Treatment", "A", "M"),  alpha= 0.05)```

*result - 10 DEGs*

* **Main effect model** (mo interaction term) ==

```results(dds.main, contrast = c("Primary_Treatment", "A", "M"),  alpha= 0.05)```

*result - 150 DEGs*

* **Group model** - address by contrasts ==

```results(dds.group, contrast = list(c("All_TreatmentAA", "All_TreatmentAM", "All_TreatmentAS"),c("All_TreatmentMA", "All_TreatmentMM", "All_TreatmentMS")),  alpha= 0.05)```

*result - 150 DEGs*

**IMPORTANT** Why is there this drastic difference in the full model? The reason here is becasue although we are calling the primary treatment ans the effect betwee Ambient and Moderate treatment as our target constrasts, the *interaction in the design* ONLY referes this effect in light of the *reference level of the 'Second_Treatment'!*. Thus the DEGs in the full model results written above are actually A**A** versus M**A** with the second **A** as the reference level (alphabetical unless called otherwise) in the second treatment interaction

**to test this - run the group calling AA vs MA below...**

* **Group contrast** - this tests the full model effect above ==

```results(dds.group, contrast = list(("All_TreatmentAA"),("All_TreatmentMA")),  alpha= 0.05)```

*result - 10 DEGs* **same as full  model above!!**

-----------------------------------
## Venn Diagrams

### Link
* Github repo script here [venn_diagrams.R](https://github.com/SamGurr/Pgenerosa_TagSeq_Metabolomics/blob/main/TagSeq/Analysis/Scripts/venn_diagrams.R)

Below I create Venn diagrams to display the overlapping DEG calls between the full model and the diagnostic constrasts run with the group model (white and yellow fill). I also include the main effect model and the group constrasts model DEG calls (green and blue fill).

![Venn diagram 1](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Venn_Day7_TagSeq.JPG "Venn diagram 1")

![Venn diagram 2](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/Venn_Day14_TagSeq.JPG "Venn diagram 2")

**What do we see?**
The full model only calls DEGs under the reference level of the subseqent treatment. The main effect and greoup model call the same DEGs but the main effect models have lower LFC values. Note: these Venn diagrams display DEGs with a cut-off of 1 LFC and 0.05 p adjusted value.
