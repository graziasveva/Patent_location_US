
# Patent_location_US

## Improving American assignee geolocalization at county level

In this notebook I propose some code to create a crawler to improve the geolocalization of patents whose assignee address is in United States. The reason for sharing this lies in the fact that currently most of patent addresses are linked to GeoNames ZIPcodes, hence it is not possible to assign coordinates (or county) to all the  patents whose ZIP codes are not present in Geonames' list (https://www.geonames.org/postal-codes/postal-codes-us.html).
To improve this current situation, in my patent geolocalization effort I create a crawler to find geographic information for these unmatched ZIP codes through unitedstateszipcodes.org (https://www.unitedstateszipcodes.org/).

In my research work, I managed to assign to an American county almost 98% of all patents granted at USPTO (100% for green patents, defined as such according to WIPO Green Inventory or OECD Green tech definition), which have at least one assignee residing within the US. To create the complete geolocalized (at county level) dataset, starting from the application dataset of patentsview (https://patentsview.org/download/data-download-tables), I used a number of sources:
1- raw location data from patentsview (https://patentsview.org/download/data-download-tables)
2- USPTO assignee dataset (extracting zipcode from the addresses, where present) (https://assignment.uspto.gov/patent/index.html#/patent/search)
3- location dataset by Gaetan de Rassenfosse (https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3425764)
Then, when even using this sources there wasn't the necessary detail to geolocalize the patent at county level, I used two different strategies:
1-in the first place, for those patents missing zipcodes, I recovered them using a public API (https://geo.fcc.gov/api/census/area) to get them using their latitude and longitude
2- eventually, for those still lacking county information despite having a zip code, I created a crawler to scrape zip codes from unitedstateszipcodes.org and to get in that way the county of the remaining patents (you can find the code for that in the uploaded notebook)

The complete dataset of US assigned patents accounts for 4,067,011 obs, including patents granted between 1980 and 2020 and it is available at the following link: https://drive.google.com/drive/folders/1FsDDmwhfARg83SCSVcxeiHylW8h-Er73?usp=sharing
In the same folder you can also find a dataset about geolocation (US, county level) of green patents (263'630 obs) 
