---
title: Slides
summary: An introduction to using Academic's Slides feature.
authors: []
tags: []
categories: []
date: "2019-02-05T00:00:00Z"
slides:
  # Choose a theme from https://github.com/hakimel/reveal.js#theming
  theme: solarized
  # Choose a code highlighting style (if highlighting enabled in `params.toml`)
  #   Light style: github. Dark style: dracula (default).
  highlight_style: dracula
---

# Articulatory Analysis With The Corpus MNGU0

[Project Page]({{< ref "/project/articulatory-analysis/index.md" >}})

---

## What We Need

- Python: Pandas and Matplotlib
- articulograph visualization [VisArtico](http://visartico.loria.fr/)
- [articulatory corpus MNGU0](http://www.mngu0.org/) - for each utterance: 
    - `.txt` file: containing numerical data of each articulatory movement recorded at a frequency of every 5 ms
    - `.lab` file: containing phonetic symbols and end time of them

---

## Brief Process Steps

#### Extraction
For each utterance, find pairs of corresponding phonetic segmentation data `.lab` file and articulatory data `.txt` file by their filename in the repository of the corpus.

---

#### Data Cleaning & Wrangling

- Create appropriate table of phonemes and their numerical position data of all the utterances.
    - Find the corresponding **_index_** of each phoneme in one utterance. Since there is only the end time information of each phoneme available, we calculate the median time point of every phoneme as **_index_**.
    - Pull in the numerical position data via **_index_** to the table/dataframe, generated with Pandas library in Python.

---

#### Data Cleaning & Wrangling

- Group the phonemes together and then calculate the mean, min, max, and standard deviation for each phoneme.
- Create another table/dataframe of calcualted articulographic distance and displacement measurements for each phoneme from the previous positional table.
    - Euclidean distance for mouth opening and pair of X-axis and Y-axis of displacement of the tongue tip, back of the tongue.

---

#### Data Visualization
- Organize the distance table by the groups of phonemes according to their place of articulation and plot with a data visualization library in Python or VisArtico.
    - A mapping chart of phonetic symbols between MNGU0 and Internatino phonetic alphabet IPA is needed.

---

#### Linguistic Analysis
- Describe the difference of the manner of the articulation for each place of articulation.
    - The manner of articulation: plosive, nasal, fricative, lateral fricative, approximant, lateral approximant and affricates.

