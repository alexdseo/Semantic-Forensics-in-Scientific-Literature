Code Usage 
1. See Merging_Final.ipynb
2. Chromedriver.exe must be the same verion as chrome and must be pathed correctly in the code 
3. DFs are either joined by university names, county names, or city_names 

Datasets Merged 
1. University Rankings (university_rankings.csv) 
2. University Demographics (univerity_demographics.csv) 
3. countydata.txt (labor data for each county) 
   - launcty20.txt is the raw version (countydata.txt is the cleaned and usable version)

Other datasets that were used to help the merging procee: 

1. Google Search scrape to find mailing address for each university_name 
   - Extract cities from mailing address
2. uscities.csv (used to merge cities to find the county of each city) 
3. Countydata.txt can now be merged by county (cities census features were added from uscities.csv through this processs) 

