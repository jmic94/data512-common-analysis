# data512-common-analysis
# DATA512 Project Part 1: Common Analysis

# Goal
Estimate the smoke impact of wildfires on the city of Texarkana, TX.

# Data Sources
- [USGS Wildfire data](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81)
- [Air Quality System (AQS) API](https://aqs.epa.gov/aqsweb/documents/data_api.html)

# API Documentation
- [Air Quality System (AQS) API](https://aqs.epa.gov/aqsweb/documents/data_api.html)

# AQS API Key
- Sign up for an API key using the link to the AQS API above.
- Store this token in a .env file stored in your local clone of the repository.
- Format it as: AQS_API = '[INSERT ACCESS TOKEN HERE]'.
- The main notebook will load the .env file to extract the API key by searching for an 'AQS_API' variable in the loaded .env file.
- The repository ignores the .env so that it will not push to any remote Git repository.

# Code
- All of the analysis lives in the notebook [analyze_wildfires.ipynb](https://github.com/jmic94/data512-common-analysis/blob/main/code/analyse_wildfires.ipynb).
- [epa_air_quality_history_example.ipynb](https://github.com/jmic94/data512-common-analysis/blob/main/code/epa_air_quality_history_example.ipynb) contains sample code for using the AQS API along with the code license information.
- [wildfire_geo_proximity_example.ipynb](https://github.com/jmic94/data512-common-analysis/blob/main/code/wildfire_geo_proximity_example.ipynb) contains sample code for working with the USGS wildfire dataset along with the code license information.
- [wildfire](https://github.com/jmic94/data512-common-analysis/tree/main/code/wildfire) contains a Python class that other notebooks import.

# Inputs
- USGS_Wildland_Fire_Combined_Dataset.json.
- Obtain this JSON file from the USGS link above.
- Download the file called 'GeoJSON Files.zip'.
- Unzip this zip file in a folder called 'input' in this repo.
- Any code that utilizes this JSON will access it from this location.
- The rest of the data needed for analysis come from the AQS API.

# Intermediates
- [aqs.csv](https://github.com/jmic94/data512-common-analysis/blob/main/intermediate/aqs_data.csv) contains the AQI data from 1963 to 2023 for air quality monitoring stations in Texerkana TX.
- [distances.csv](https://github.com/jmic94/data512-common-analysis/blob/main/intermediate/distances.csv) contains the wildfire data from USGS along with their calculated distance to Texarkana, TX.
- Both of these intermediate files are outputs from [analyze_wildfires.ipynb](https://github.com/jmic94/data512-common-analysis/blob/main/code/analyse_wildfires.ipynb).

# Outputs
- [acres_burned.png](https://github.com/jmic94/data512-common-analysis/blob/main/output/acres_burned.png) is a chart showing the total number of acres burned annually by wildfires within 1,250 miles of Texarkana, TX that occurred between 1963 to 2020.
- [distance_histogram.png](https://github.com/jmic94/data512-common-analysis/blob/main/output/distance_histogram.png) is a chart showing the distribution of wildfire proximity to Texarkana, TX from 1963 to 2020.
- [est_vs_aqi.png](https://github.com/jmic94/data512-common-analysis/blob/main/output/est_vs_aqi.png) is a chart comparing the annual smoke estimate and the annual fire season AQI from 1999 to 2020.
- [smoke_forecast.png](https://github.com/jmic94/data512-common-analysis/blob/main/output/smoke_forecast.png) is a chart showing the annual smoke estimates from 1963 to 2020 as well as the forecast smoke estimates from 2021 to 2049. It also includes a 95% confidence interval for the forecasts.

# Notes
- There are roughly 130,000 wildfires in the USGS dataset, of which around 63,000 occurred from 1963 onwards AND occurred within 1,250 miles of Texarkana, TX.
- The AQI data can be sparse for older decades. I've found that the monitoring stations in Texerkana, TX begin having reliable data starting in the year 1999.
