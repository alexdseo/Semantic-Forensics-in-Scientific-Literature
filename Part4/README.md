# Part 4 feature extraction

`Part4.ipynb` loads `Bik.tsv` into a dataframe, scrapes Research Gate to extract 7 features for 214 papers, adds the features to the dataframe, and exports it as `Bik_pt4.csv`. Because web scraping takes so long, the features have been saved to `Part4features.ipynb` and imported into `Part4.ipynb` for easy access. The variables acessible from `Part4features.ipynb` include:

- `DOI_URLS`: URLs for journal pages
- `first_author_URLS`: URLs for first author Research Gate profile
- `labs`: lab size, all authors
- `rates`: publication rate, all authors
- `journals`: journals published in, all authors
- `affiliation`: affiliated university, first authors
- `duration`: duration of career, first authors
- `degree`: highest degree, first authors
- `department`: degree area, first authors

To run the entire script including web scraping, restart the kernal and run all.

To update the original Bik dataset with the saved features (scraped for you), run:
- Import libraries: all cells
- Load Bik data: all cells
- Clean data: all cells
- Functions (including Get URLs, Classify site structure, First authors): all cells
- All authors: last two cells
- First author only: last two cells
- Last two cells to view updated dataframe and export CSV

## Files

- `Bik.tsv` - original dataset
- `Part4.ipynb` - main script
- `Part4features.ipynb` - extracted features
- `chromedriver.exe` - download the appropriate version as per Requirements
- `Bik_pt4.csv` - output

## Requirements

- Python 3
- Jupyter Notebook
- Google Chrome

### Libraries

```python
import numpy as np
import pandas as pd
import re
import json
import requests
from bs4 import BeautifulSoup
from googlesearch import search
import time

from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.by import By
```

- Numpy: `pip install numpy`
- Pandas: `pip install pandas`
- Requests: `pip install requests`
- Beautiful Soup: `pip install beautifulsoup4`
- Google Search: `pip install google`
- Selenium: `python -m pip install selenium`
	- ChromeDriver: [https://chromedriver.chromium.org](https://chromedriver.chromium.org) - Download the appropriate version for your device. Make sure `chromedriver.exe` is saved to the same directory. Version in this directory is for Mac64 M1, Chrome 98.
	- webdriver-manager: `pip install webdriver-manager`