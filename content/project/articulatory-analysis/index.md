---
title: Articulatory Analysis With The Corpus MNGU0
subtitle: Descriptive analysis of the results extracted and calculated from electromagnetic articulographs (EMA).
summary: Descriptive analysis of the results extracted and calculated with Python from electromagnetic articulographs (EMA).
tags:
- Sppech Processing
date: "2020-06-17T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: Picture of articulation place from Wikipedia 
  focal_point: Smart

links:
- icon: ""
  icon_pack: ""
  name: ""
  url: ""
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: articulatory-anaylsis
---

_This project is a individual project assigned in the class of Speech Synthesis at IDMC, University of Lorraine._

The [articulatory corpus MNGU0](http://www.mngu0.org) is a public English articulatory data of various forms (EMA, MRI, video, 3D scans of upper/lower jaw, audio etc.), of which the access can be gained from the site after registration. 

The visualization of articulatory corpus can be done via the [VisArtico](http://visartico.loria.fr/), a cross-platform Java-based software designated for the researchers to visualize the articulograph data.

-----------------------------------------------------

### Introduction

The goal of the project to observe and use automatic tools to perform a descriptive analysis of 28 phonemes in English. For each phoneme, the descriptive analysis includes the mean, min, max and standard deviation for the following articulatory movement measurements: the Euclidean distance of mouth opening, the displacement of the tongue tip, the displacement of the back of tongue and the displacement of the jaw.

In this project, 1263 utterances, in average 16 phonemes for each utterance and approximately 20208 phonemes in total, have been analyzed. For each utterance, there are 4 corresponding files: binary file of articulatory data in `.ema` format, readable articulatory data in `.txt` format, phonetic segmentation file in `.lab` format and the audio file in `.wav` format. In order to cal, we need `.txt` and `.lab` files. 

To calculate the articulatory measurements of every phoneme, the phonetic segmentation data `.lab` files, containing phonetic symbols and end time of them, and articulatory data `.txt` files, containing numerical data of each articulatory movement recorded at a frequency of every 5 ms, are needed. In order to extract and perform the calculation, the automatic tool that I chose to work with is **Python**. The built-in functions and libraries help to accomplish these tasks. Easy peasy lemon squeezy.:lemon:

### The brief process steps are described as below:


**Extraction**:

1. For each utterance, find pairs of corresponding phonetic segmentation data `.lab` file and articulatory data `.txt` file by their filename in the repository.

**Data Cleaning & Wrangling**:

2. Create appropriate table of phonemes and their numerical position data of all the utterances.
    1. Find the corresponding _**index**_ of each phoneme in one utterance. Since there is only the _end time_ information of each phoneme available, we calculate the _median time point_ of every phoneme as _**index**_.
    2. Pull in the numerical position data via _**index**_ to the table/dataframe, generated with Pandas library in Python.
3. Group the phonemes together and then calculate the mean, min, max, and standard deviation for each phoneme.
4. Create another table/dataframe of calcualted articulographic distance and displacement measurements for each phoneme from the previous positional table.
    * Euclidean distance for mouth opening (UL upper lip and LL lower lip).
    * Displacement of the tongue tip, back of the tongue and the jaw on both x-axis and y-axis.

**Data Visualization**:　

5. Organize the distance table by the groups of phonemes according to their place of articulation and plot with a data visualization library in Python.
    * A mapping chart of phonetic symbols between MNGU0 and Internatino phonetic alphabet IPA is needed.
    * IPA groups: _bilabial_, _labiodental_, _dental_, _alveolar_, _postalveolar_, _palatal_, _velar_, _glotta_, etc.

**Linguistic Analysis**:

6. Describe the difference of the manner of the articulation for each place of articulation.
    * The manner of articulation: _plosive_, _nasal_, _fricative_, _lateral fricative_, approximant, _lateral approximant_ and _affricates_.

