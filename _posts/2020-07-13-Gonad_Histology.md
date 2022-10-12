---
layout: post
title: Gonad_Histology
date: '2020-07-13'
categories: Analysis
tags: geoduck, histology
---

## Pacific geoduck gonad histology analysis (Image J)

### Objective:
  Outline the process in Image J for investigating the reproductive status of histology samples taken from adult Pacific geoduck broodstock in 2019.

-  Note: broodstock were conditioned during gametogenesis under ambient vs. elevated pCO2 conditions!

#### Histology slide photos can be found here!
-  https://drive.google.com/drive/folders/1AJU6q8X2eejtcLZ90_2LVnjOkcSQJVoy


#### Some important background for geoduck gonad histology
- https://www.dfo-mpo.gc.ca/science/aah-saa/species-especes/shellfish-coquillages/geopath/gonads-eng.html

  -**Important terms from this link..**
    - acini
    - lumen
    - spermatocytes/spermatozoa
    - vesticular connective tissue & glycogen/lipid cells

----------------------------------------
### Image J Analysis

#### Example here: ID #041

##### 1) Open the jpeg in ImageJ and set the scale
  - zoom in to see the scale bar (i.e. 100um in this photo)
  - left click the line tool and trace this scale bar
  - go to... Analyze -> Set Scale
  - type the distance in Known Distance
  - select Global if the next photos are all at the same magnification
  - select OK

![setscale](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/gonad_sample_setscale.JPG "setsccale")

##### 2) Draw oval, measure total area, and clear outside
  - Why? the corners of these histology photos are more blurry and darker than the center of the photos. Drawing this area provides a consistant color threshold for analysis downstream
  - select the oval tool
  - draw an oval/circle focused at the center of the histology photo
  - **A) Total Area**
    - Press Cntrl+m to measure the shape area
  - Select Edit -> Clear Outside to remove the outside of the image and focus our analysis

![gonad_clearoutside](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/gonad_clearoutside.JPG "gonad_clearoutside")

##### 3) Analysis with Color threshold
- Select Image -> Adjust -> Color Threshold
  - this will open the window with saturation, Hue and Brightness
  - *Note*: keep Threshold Method on Default; Threshold color can be changed throughout the following steps w/o interfering with measurements, color space HSB
  - use the table (below) for the color threholds that capture the lumen, sptermatozoa, and spermatozoa & Spermatocytes
  - after **each** setting... press Select to highlight and Cntrl+m to measure
  - once complete, save the measurement window to a desired folder.

### Table for settings
- *Note: this is JUST for this specific exmplae #041*

Target Characteristic | Hue | Saturation | Brightness | Note
-----------: | -----------: | -----------: | -----------: | -----------: |
**(A)**Total Area  | -  | -  |  - | already recorded
**(B)** Lumen | 198:255 | 143:255 | 58:255 |
**(C)** Spermatozoa | 165:195 | 202:255 | 58:255 |
**(D)** Spermatozoa+Spermatocytes | 115:182 | 88:255 | 58:236 |

## Screenshots with these settings...

### B. Lumen

#### Sample #041

![gonad_lumen](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/gonad_lumen.JPG "gonad_lumen")

### C. Spermatozoa

#### Sample #041

![gonad_spermatozoa](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/gonad_spermatozoa.JPG "gonad_spermatozoa")

### D. Spermatozoa+Spermatocytes

#### Sample #041

![gonad_zoa_cytes](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/gonad_zoa_cytes.JPG "gonad_zoa_cytes")

### IMPORTANT! Errors in the process...

#### (1) Lumen + connective tissue and lipid cells overlap in hue/saturation

  - Histology samples showcasing low reproductive status (relative to #041 above) have a higher percent cover of conncetive tissue with lipid cells. Unfortunately, the hue/saturation of the lipid cells overlaps with the lumen.

![gonad_lumen_ERROR](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/gonad_lumen_ERROR.JPG "gonad_lumen_ERROR")

![lipid_cells_connective_tissue](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/lipid_cells_connective_tissue.JPG "lipid_cells_connective_tissue")

#### (2) Spermatocytes + spermatozoa overlap in hue/saturation

  - Spermatozoa and spermatocytes can not be determined - solely the total acini space (minus lumen) is possible in these samples (example below)

![gonad_zoa_cytes_4](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/gonad_zoa_cytes_4.JPG "gonad_zoa_cytes_4")

#### SOLUTION?
  - The purple dye of the cyes and zoa is distinct in all histology slides
  - Focus on the percent cover of reproductive cells per sample (spermatocytes + spermatozoa)
  - **Spermatocytes+spermatozoa / Total area == main metric between samples**

----------------------------------------
## Calculations
- **Use the AREA output by ImageJ measurements for the following...**
- Note: the *letters* used here refer to the the table (above)

### (A) Simple option...
##### ..*in light of inconsistencies between samples!*

 Spermatocytes+Spermatozoa / Total area == main metric between samples

#### RESULTS
- GITHUB REPO: https://github.com/SamGurr/Pgenerosa_histology
- not significant : T-test; t = 0.47357, df = 6.4737, p-value = 0.6514

![male_gonad_hist](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/male_gonad_hist.JPG "male_gonad_hist")



### (B) Most comprehensive option...

Total image area = **A**

Lumen = **B**

Spermatozoa = **C**

Spermatozoa + Spermatocytes = **D**

**E**; Spermatocytes = C - D

**F**; Total acini area = D + B

**G**; Vesticular connective tissue = A - F

### correct for total area

**divide** targets (lumen, total acini area, spermatozoa, spermatocytes, vesticular connective tissue) **by Total image area** to compare the reproductive status between individuals and correct for the oval area selected.
