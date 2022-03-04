# Analysis of Media and Semantic Forensics in Scientific Literature

Media manipulation is an increasing concern in scientific and open literature since researchers like [Bik et al.](https://journals.asm.org/doi/full/10.1128/mBio.00809-16) have seen a tremendous uptick in papers with media
manipulations and potential problems over the last decade. 
Bik et al. have captured a dataset that records information about papers including Authors, Paper Title,
Citation, Digital Object Identifier (DOI), Year, Month, Classification Label (0-3)
referring to three major categories: simple duplications, duplications with repositioning,
and duplications with alteration and also two potentially problematic areas that may not
be manipulations but cause issues (Cuts & Beautification). 

The dataset also includes a
text description of what was found (Findings), if the paper was reported to the journal or
not, and whether it was retracted, or a correction issued or not, and finally whether no
action was taken and what date (if any) any action was completed on. The data is
formatted according to the referenced schema which will be provided to you and is in
TSV (TSV) format (MIME type: text/tab-separated-values). Looking at the Bik et al media manipulation data, you may ask yourselves: “what other
data is available that could be joined with this information” to affect its Five V’s (volume, velocity, variety, veracity and value)
intentionally, or unintentionally. 

In this project, we will scrap additional additional information about each
author for each of the provided publications and collecting and joining it to the Bik
dataset. For example, “Lab Size (number of students)”,
“Publication Rate”, “Other Journals Published In” and some information about “First
Author” including “Affiliation University”, “Duration of Career (Years)”, highest degree
obtained (e.g., “PhD”, “MS”) and “Degree Area” (e.g., Computer Science). 

Using this new dataset and Tika Similarity to evaluate data similarity between each author by calculating and 
exploring different distance metrics (Cosine similarity, Levenshtein Distance, Jaro-Wrinkler Distance etc.),
we will aim to find a pattern that will emerge.
For example, you could posit that those with a Masters in
Computer Science, with 50 years of experience and 100 students in the lab, may not be
critically reviewing papers published in biomedical journals. Then, we can figure out how similar papers with problem areas are
within the data and ask questions of your new augmented Bik et al dataset. 

---

## How to use

This project demonstrates the usage of the [Tika-Python](http://github.com/chrismattmann/tika-python) package (Python port of Apache Tika) to compute file similarity based on metadata features. Original project guides to use local terminal to run the files and packages, however, in our project we will use Jupyter notbook to demonstrate our work to make it more interactive.

## Cosine Distance comparison on Metadata Values

- This computes pairwise similarity scores based on Cosine Distance Similarity.
- **Similarity Score of 1 implies an identical pair of documents.**

```
#!/usr/bin/env python3.7
python cosine_similarity.py [-h] --inputDir INPUTDIR --outCSV OUTCSV [--accept [png pdf etc...]]

--inputDir INPUTDIR  path to directory containing files

--outCSV OUTCSV      path to directory for storing the output CSV File, containing pair-wise Similarity Scores based on Cosine distance

--accept [ACCEPT]    Optional: compute similarity only on specified IANA MIME Type(s)

```

## Metalevenshtein string distance

- This calculates Metalevenshtein (Inspired by the paper : Robust Similarity Measures for Named Entities Matching by Erwan et al.) distance between two strings.

```
#!/usr/bin/env python3.7

Usage:

import metalevenshtein as metalev
print metalev.meta_levenshtein('abacus1cat','cat1cus')


To use all the argument options in this function:

def meta_levenshtein(string1,string2,Sim='levenshtein',theta=0.5,strict=-1,idf=dict()):

    Implements ideas from the paper : Robust Similarity Measures for Named Entities Matching by Erwan et al.
    Sim = jaro_winkler, levenshtein : can be chosen as the secondary matching function.
    theta is the secondary similarity threshold: If set higher it will be more difficult for the strings to match.
    strict=-1 for doing all permutations of the substrings
    strict=1 for no permutations
    idf=provide a dictionary for {string(word),float(idf od the word)}: More useful when mathings multi word entities (And word importances are very important)
    like: 'harry potter', 'the wizard harry potter'

```

## Bell Curve fitting and overlap

- Fits two datasets into bel curves and finds the area of overlap between the bell curves.


```
#!/usr/bin/env python3.7
import features as feat
data1=[1,2,3,3,2,1]
data2=[4,5,6,6,5,4]
area,error=feat.gaussian_overlap(data1,data2)
print area

```



## D3 visualization

### Cluster viz 
- Jaccard Similarity
```
* python cluster-scores.py [-t threshold_value] (for generating cluster viz)
* open cluster-d3.html(or dynamic-cluster.html for interactive viz) in your browser
```
- Edit Distance & Cosine Similarity  
```
* python edit-cosine-cluster.py --inputCSV <PATH TO CSV FILE> --cluster <INTEGER OPTION> (for generating cluster viz)

  <PATH TO CSV FILE> - Path to CSV file generated by running edit-value-similarity.py or cosine_similarity.py
  <INTEGER OPTION> - Pass 0 to cluster based on x-coordinate, 1 to cluster based on y-coordinate, 2 to cluster based on similarity score

* open cluster-d3.html(or dynamic-cluster.html for interactive viz) in your browser
```

Default **threshold** value is 0.01.

<img src="https://github.com/dongnizh/tika-img-similarity/blob/refactor/snapshots/cluster.png" width = "200px" height = "200px" style = "float:left">
<img src="https://github.com/dongnizh/tika-img-similarity/blob/refactor/snapshots/interactive-cluster.png" width = "200px" height = "200px" style = "float:right">

### Circlepacking viz
- Jaccard Similarity
```
* python circle-packing.py (for generating circlepacking viz)
* open circlepacking.html(or dynamic-circlepacking.html for interactive viz) in your browser
```
- Edit Distance & Cosine Similarity  
```
* python edit-cosine-circle-packing.py --inputCSV <PATH TO CSV FILE> --cluster <INTEGER OPTION> (for generating circlepacking viz)

  <PATH TO CSV FILE> - Path to CSV file generated by running edit-value-similarity.py or cosine_similarity.py
  <INTEGER OPTION> - Pass 0 to cluster based on x-coordinate, 1 to cluster based on y-coordinate, 2 to cluster based on similarity score


* open circlepacking.html(or dynamic-circlepacking.html for interactive viz) in your browser
```
<img src="https://github.com/dongnizh/tika-img-similarity/blob/refactor/snapshots/circlepacking.png" width = "200px" height = "200px" style = "float:left">
<img src="https://github.com/dongnizh/tika-img-similarity/blob/refactor/snapshots/interactive-circlepacking.png" width = "200px" height = "200px" style = "float:right">

---

## Pre-requisite & Installation

```
- Install [Tika-Python](http://github.com/chrismattmann/tika-python)
- Install [Java Development Kit](https://www.oracle.com/java/technologies/javase-downloads.html)

- git clone https://github.com/chrismattmann/tika-img-similarity
- pip install -r requirements.txt

```

---

## Contributors

* Alex DongHyeon Seo, USC
* Matt Fishman, USC
* Audrey Lin, USC
* Andy Xiang, USC
* Sarah Chu, USC
* Elena Pilch, USC

## License

This project is licensed under the [Apache License, version 2.0](http://www.apache.org/licenses/LICENSE-2.0).







