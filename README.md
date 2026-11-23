# Lit Denser
# Team Members
| Member Name | Role | Branch Name |
| ------------------------ | ------------------------- | ----------- |
| Sivagunalan Thamilarasan | Data Engineer | ST/<task> |
| Nathan Gong | Data Engineer | NG/<task> |
| Joseph Lacap | Cloud Engineer | JL/<task> |
| Jin Ha Park | Data Analytics | JH/<task> |
| Erin Yang | Data Visualizer & Metrics | EY/<task> |

# Problem Statements
Wildfires can create a mix of environmental and health challenges across the U.S. - smoke, poor air quality, evacuations, and damaged homes - they can place multiple burdens on nearby locations. Our goal is to combine four datasets on wildfires, air quality, population, and weather to show how wildfires and air quality vary across places with different population densities. 
To do this, we split the U.S. into 10x10(km) grid cells and add weather data so we can compare places with similar conditions. We investigate whether wildfires happen more often in high density areas, whether fires in low density areas burn more acres, and how long air quality takes to return normally after a fire occurs. The 2020 wildfire season was one of the most severe on record, and California is one of the most impacted states in the U.S. for wildfire, so we expect this data to help us see how wildfire damage relates to the community.  

Is a 10x10 km grid cell's population density correlated with its average max CO concentration (join, groupByKey, reduce)
Is the occurrence of wildfires correlated to the population density of each grid cell? (join, filter, reduce)
How long does it take for the local air quality to return to baseline levels after a recent wildfire across high and low population density grid cells? (join, filter, aggregate)
Which grid cells with a high population density experience the highest number of days with unhealthy amounts of CO concentration correlated with wildfires? (join, groupByKey, orderBy)
Does the frequency of wildfires happen to be higher or lower across places with different densities?
Do fires in low density areas burn more acres compared to high density areas assuming the weather/environmental conditions are similar?
Does human vs nature caused wildfires change with population density?
