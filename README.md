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

In this project, we will scrap additional information about each
author for each of the provided publications and collecting and joining it to the Bik
dataset. For example, “Lab Size (number of students)”,
“Publication Rate”, “Other Journals Published In” and some information about “First
Author” including “Affiliation University”, “Duration of Career (Years)”, highest degree
obtained (e.g., “PhD”, “MS”) and “Degree Area” (e.g., Computer Science). 

Using this new dataset and Tika Similarity to evaluate data similarity between each author by calculating and 
exploring different distance metrics (Cosine similarity, Levenshtein Distance, Jaro-Winkler Distance etc.),
we will aim to find a pattern that will emerge.
For example, you could posit that those with a Masters in
Computer Science, with 50 years of experience and 100 students in the lab, may not be
critically reviewing papers published in biomedical journals. Then, we can figure out how similar papers with problem areas are
within the data and ask questions of your new augmented Bik et al dataset. 

---

## Code & Report

This project demonstrates the usage of the [Tika-Python](http://github.com/chrismattmann/tika-python) package (Python port of Apache Tika) to compute file similarity based on metadata features. [Original project](https://github.com/chrismattmann/tika-img-similarity) guides to use local terminal to run the files and packages, however, in our project we will use Jupyter notebook to demonstrate our work to make it more interactive. Please check our report about this project too!


- [Main Notebook file](https://github.com/alexdseo/tika-similarity/blob/master/DataSimilarity_Tika.ipynb)
- [Report](https://github.com/alexdseo/tika-similarity/blob/master/Report.pdf)


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
* Hsuan Sarah Chu, USC
* Elena Pilch, USC

## License

This project is licensed under the [Apache License, version 2.0](http://www.apache.org/licenses/LICENSE-2.0).







