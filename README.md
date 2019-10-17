# Project: University of Washington, DATA 512 Autumn 2019, Assignment 2
# Title: Wikipedia politician pages, and bias in data
### Author: Bianca Zlavog
### Goal: To analyze the number and quality of English Wikipedia politician pages relative to country and region population
### License: This work is available under an MIT license, included in the repository.
### Assignment instructions: https://wiki.communitydata.science/Human_Centered_Data_Science_(Fall_2019)/Assignments#A2:_Bias_in_data


## Inputs:

* [Politicians by Country from the English-language Wikipedia](https://figshare.com/articles/Untitled_Item/5513449), compiled by Os Keyes. Version 6 published on 10/28/2017 10:49, available under a CC-BY-SA 4.0 license
* [2018 World Population Data Sheet](https://canvas.uw.edu/files/58607571/download?download_frd=1), created by the Population Reference Bureau
* Data was gathered from the [Wikimedia ORES REST API](https://github.com/wikimedia/ores), Wikimedia Foundation and authors Aaron Halfaker, Yuvi Panda, Amir Sarabadani, Justin Du, Adam Wight, available under an MIT License
API documentation: https://www.mediawiki.org/wiki/ORES and https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model

Date all data was accessed: 10/13/2019


## Data considerations:

* 
	

## Data processing:

* In the Politicians by Country dataset, we remove any entries starting with the string "Template:", which are not actual Wikipedia pages
* We process the population dataset to map each country to its respective region
* We use the ORES API to obtain article quality data for politician articles, remove entries for which the ORES API query did not return article quality scores
* Merge together all datasets (populations, articles, article quality, region information and population) for analysis


## Outputs:

* `data_raw/page_data.csv`: Raw input data from the Politicians by Country dataset
* `data_clean/wp_wpds_countries-no_match.csv`: Entries for which either no population data or no politician data were available
* `data_clean/wp_wpds_politicians_noscores.csv`: Entries for which the ORES API did not return article quality scores
* `data_clean/wp_wpds_politicians_by_country.csv`: Final cleaned data used for analysis. Variables include:

    `country`: Name of the country that the politician worked in
    
    `article_name`: Wikipedia page title, containing the name of a politician
    
    `revision_id`: edit ID of the last edit to the page
    
    `article_quality`: Quality of the article, as output by the ORES API
    
    `population`: Population of the country
    
* Within the notebook, we create six tables comparing the relative quantity and quality of Wikipedia political pages relative to population across countries and regions
* Within the notebook, we produce a writeup of the findings and potential sources of bias in the data


## Software used:

* MacOS Mojave 10.14.6
* Python 3.7.1
* ipython 7.2.0

