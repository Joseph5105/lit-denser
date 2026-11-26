# Lit Denser
# Team Members
| Member Name | Role | Branch Name |
| ------------------------ | ------------------------- | ----------- |
| Sivagunalan Thamilarasan | Data Engineer | ST/(task) |
| Nathan Gong | Data Engineer | NG/(task) |
| Joseph Lacap | Cloud Engineer | JL/(task) |
| Jin Ha Park | Data Analytics | JH/(task) |
| Erin Yang | Data Visualizer & Metrics | EY/(task) |

# Problem Statements
Wildfires can create a mix of environmental and health challenges across the U.S. - smoke, poor air quality, evacuations, and damaged homes - they can place multiple burdens on nearby locations. Our goal is to combine four datasets on wildfires, air quality, population, and weather to show how wildfires and air quality vary across places with different population densities. 

To do this, we split the U.S. into 10x10(km) grid cells and add weather data so we can compare places with similar conditions. We investigate whether wildfires happen more often in high density areas, whether fires in low density areas burn more acres, and how long air quality takes to return normally after a fire occurs. The 2020 wildfire season was one of the most severe on record, and California is one of the most impacted states in the U.S. for wildfire, so we expect this data to help us see how wildfire damage relates to the community.  

1. Is a 10x10 km grid cell's population density correlated with its average max CO concentration (join, groupByKey, reduce)
2. Is the occurrence of wildfires correlated to the population density of each grid cell? (join, filter, reduce)
3. How long does it take for the local air quality to return to baseline levels after a recent wildfire across high and low population density grid cells? (join, filter, aggregate)
4. Which grid cells with a high population density experience the highest number of days with unhealthy amounts of CO concentration correlated with wildfires? (join, groupByKey, orderBy)
5. Does the frequency of wildfires happen to be higher or lower across places with different densities?
6. Do fires in low density areas burn more acres compared to high density areas assuming the weather/environmental conditions are similar?
7. Does human vs nature caused wildfires change with population density?

# Data Sources with URL, Description, and Schema
## Dataset # 1 - Population Density
- Title: United States Population Density 2020 UN Adjusted (1km resolution)
- Source URL: https://hub.worldpop.org/geodata/summary?id=44771
- Size on disk (uncompressed): 857.5 MB
- Number of records: 15.8 Million Rows
- Method: File

### Schema
| **Column Name** | **X** | **Y** | **Z** |
|-----------------|-------|-------|-------|
| ***Detail*** | *Longitude: East-West Position*<br>*Data Type: float* | *Latitude: North-South Position*<br>*Data Type: float* | *Population Density: People per km²*<br>*Data Type: float* |

## Dataset # 2 - Wildfire - 2020 
- Title: Spatial wildfire occurrence data for the United States, 1992-2024 [FPA_FOD_20260615] (7th Edition)
- Source URL: https://www.fs.usda.gov/rds/archive/catalog/RDS-2013-0009.7 
- Size on disk (uncompressed): 973 MB
- Number of records: 2.66 Million Records (filtered result by FIRE_YEAR = 2020 is 74,530 rows)
- Method: Bulk download

### Schema
| **Column Name** | **FOD_ID** | **NWCG_CAUSE_CLASSIFICATION** | **State** |
|-----------------|------------|-------------------------------|-----------|
| ***Detail*** | *ID: Unique ID for each fire*<br>*Data Type: int* | *Cause: Human / Natural*<br>*Data Type: str* | *Data Type: str* |

## Dataset # 3 - EPA Air Quality
- Title: EPA Air Quality - Specifically CO Data - Year 2020
- Source URL: https://www.epa.gov/outdoor-air-quality-data/download-daily-data 
- Size on disk (uncompressed): 5.1 MB
- Number of records: 22,127 Rows
- Method: File Download

### Schema
| **Column Name** | **Daily Max 8-hour CO Concentration** | **PM2.5** | **Daily AQI Value** | **State** |
|-----------------|---------------------------------------|--|---------------------|-----------|
| ***Detail*** | *CO Level: 8-hour average concentration of carbon monoxide*<br>*Data Type: float* |*Fine particulate matter*<br>*Data Type: float*| *Air Quality Index*<br>*Data Type: int* | *Data Type: str* |

## Dataset #4 - Climate Climatology Lab
- Title: gridMET - daily high-spatial resolution (~4-km, 1/24th degree) surface meteorological data covering the contiguous US (1979-yesterday)
- Source URL: https://www.climatologylab.org/gridmet.html
- Size on disk (uncompressed): ~1.19GB
- Number of records: ~296.8 Million Rows
- Method: File

### Schema
| **Column Name** | **Date** | **Latitude, Longitude** | **pr** | **tmmx, tmmn** | **sph** |
|-----------------|----------|-------------------------|--------|----------------|---------|
| ***Detail*** | *Observation Date*<br>*Data Type: date* | *Latitude & Longitude of Grid Cell*<br>*Data Type: float* | *Daily Precipitation (mm)*<br>*Data Type: float* | *Daily Maximum & Minimum Temperature (K)*<br>*Data Type: float* | *Specific Humidity (kg/kg)*<br>*Data Type: float* |
