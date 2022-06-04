# UDS-Project--Full-Team-

# Final Project: Gentrification in Westlake and Surrounding Communities

### By Jinglan Lin, Pearl Liu, Mica O'Brien, and Omer Sohail

For our final project, our group was interested in exploring neighborhood change and displacement risk in the Westlake neighborhood of Los Angeles. Our group is connected to a community organizing effort around building a strong “ground game” for updating the Westlake Community Plan, which will take place early next year. We hope this data analysis project will help organizers share the significance with funders and leaders of what’s at stake for the Westlake Community, a low-income Brown community that is vulnerable to gentrification.  

Our project attempts to answer the following research questions: 

 - Which census tracts (and which neighborhoods) have experienced the greatest change in terms of gentrification/displacement indicators from 2010-2020? 
     - Are there commonalities across neighborhoods?
     - How are these clusters similar to and/or different from the Urban Displacement Project's gentrification typology determinations? How do they compare? 
 - Which census tracts (and which neighborhoods) have experienced the greatest change in terms of land values from 2010-2020? 
     - Can percent change in land value from 2010-2020 be used to predict percent change for the next 10 years? 

We rely on the following datasets to answer our research questions: 

 - Assessor Parcels Data - 2006 thru 2021 (LA County Open Data)
 - Displacement Typologies Data - thru May 2018 (Urban Displacement Project)
 - City of LA Displacement Index - 2000-2014 (LA GeoHub) 
 - Census Data - 2010 and 2020
    - Racial demographics 
    - Years of education
    - Household size 
    - Median income
    - Median gross rent

We begin by recreating the City of LA's displacement index using updated census data. We clean and join census data on racial demographics, years of education, household size, median income, and median gross rent for 2010 and 2020. We calculate percent change across these years. Seperately, we filter and clean sold land parcels in 2010 and 2020. We calculate percent change across these years as well. We conduct various cluster analyses using the gentrification indicators and map our findings alongside the Urban Displacement Project's gentrification typologies for the 6 neighborhoods. We use a random forest model to predict land value change across the 6 neighborhoods and map the results. 

## Folder Organization

Our project repo includes 4 folders: Data, Data Cleaning Notebooks, Final Outputs, and Resources. We recommend referring to the Final Outputs folder first, which includes 3 notebooks with our final visualizations and reflections. Our data cleaning notebooks are predictably located in the Data Cleaning Notebooks folder. The datasets we used are saved in the Data folder. You can disregard the Resources folder. We have saved several csv and GeoJSON files to the folder as well, which are used throughout our analysis.

## Findings

### Cluster Analysis and Mapping 

We create clusters of the 128 census tracts in Westlake, Downtown, Pico-Union, Echo Park, Silver Lake, and Koreatown to better understand similarities and differences across these neighborhoods in terms of demographic change over time. We find that 2 of the clusters, which make up a majority of the census tracts (90 in total), are fairly stable over the ten year period, meaning they do not have particularly high rates of change in any of the census indicators. The 3 other clusters represent varying degrees of neighborhood change with one cluster exhibiting a dramatic change in racial demographics, education level, and rent, one cluster exihibiting some change in demographics, and another cluster exhibiting dramatic change in nonfamily income. When we map the clusters, we see that cluster 4 (a cluster with some of the more stable census tracts) appear to be grouped on the outskirts of the map in the north, west, and south. Cluster 1, which includes census tracts with some notable deomgraphic change, appears to be concentrated in the southern part of the map. Clusters 0 and 3--which also had high rates of change--appear to be sprinkled throughout.  

The clusters predictably become more visually distinct when we incorporate dummy variables for the neighborhoods into the cluster analysis. We see clear clusters in Koreatown and  Silver Lake/Echo Park in particular. When we map the clusters next to the Urban Displacement Project's Gentrification Typology map, greater patterns emerge. UDP has 8 distinct stages of gentrification, including: advanced gentrification, at-risk of gentrification, becoming exclusive, early/ongoing gentrification, low-income/susceptible to displacement, ongoing displacement, stable moderate/mixed income, and stable/advanced exclusive. We assigned numeric values to each stage to more easily compare it with the 5 clusters of our data. We assigned advanced gentrification as 4 and stable/advanced exclusive as 0. 

We see that cluster 4 (one of the more stable clusters) is concentrated in Koreatown. On the UDP map, this area has medium and rising gentrification/displacement risk (gentrification has intensified on the west side of the neighborhood and appears to be moving eastward). Cluster 3 (which has a high percent change in white population) is clustered in the southwest area, which is Pico-Union/Westlake. On the UDP map, this area has medium to high gentrification/displacement risk. Cluster 2 (one of the more stable clusters) is concentrated in Silver Lake and Echo Park, which correlates with the stable moderate/stable exclusive typology on the UDP map. Cluster 1 (census tracts with extremely high percent change in bachelor's degrees and a notably high percent change in family and nonfamily income and rents) is located in Downtown. The UDP map shows this area as at risk/advanced gentrification. Lastly, Cluster 0 (census tracts with a high percent change in nonfamily income with and without inflation) is distributed across the map and does not translate easily onto the UDP map.

According to the UDP map, many census tracts across the six neighborhoods are at risk of gentrification. However, the cluster analysis indicates which key indicators are correlated with different stages of gentrification. It appears that a large increase in rents and percent of the population with a bachelor's degree and above are correlated with advanced gentrification in the Downtown, Silver Lake, Echo Park areas. This information could be valuable to policymakers, who can tailor displacement interventions accordingly.   

### Predictive Modeling with the Land Value Dataset

We create clusters of the 128 census tracts in Westlake, Downtown, Pico-Union, Echo Park, Silver Lake, and Koreatown to better understand similarities and differences across these neighborhoods in terms of demographic change over time. We find that 2 of the clusters, which make up a majority of the census tracts (90 in total), are fairly stable over the ten year period, meaning they do not have particularly high rates of change in any of the census indicators. The 3 other clusters represent varying degrees of neighborhood change with one cluster exhibiting a dramatic change in racial demographics, education level, and rent, one cluster exihibiting some change in demographics, and another cluster exhibiting dramatic change in nonfamily income. When we map the clusters, we see that cluster 4 (a cluster with some of the more stable census tracts) appear to be grouped on the outskirts of the map in the north, west, and south. Cluster 1, which includes census tracts with some notable deomgraphic change, appears to be concentrated in the southern part of the map. Clusters 0 and 3--which also had high rates of change--appear to be sprinkled throughout.

The clusters predictably become more visually distinct when we incorporate dummy variables for the neighborhoods into the cluster analysis. We see clear clusters in Koreatown and Silver Lake/Echo Park in particular. When we map the clusters next to the Urban Displacement Project's Gentrification Typology map, greater patterns emerge. UDP has 8 distinct stages of gentrification, including: advanced gentrification, at-risk of gentrification, becoming exclusive, early/ongoing gentrification, low-income/susceptible to displacement, ongoing displacement, stable moderate/mixed income, and stable/advanced exclusive. We assigned numeric values to each stage to more easily compare it with the 5 clusters of our data. We assigned advanced gentrification as 4 and stable/advanced exclusive as 0.

We see that cluster 4 (one of the more stable clusters) is concentrated in Koreatown. On the UDP map, this area has medium and rising gentrification/displacement risk (gentrification has intensified on the west side of the neighborhood and appears to be moving eastward). Cluster 3 (which has a high percent change in white population) is clustered in the southwest area, which is Pico-Union/Westlake. On the UDP map, this area has medium to high gentrification/displacement risk. Cluster 2 (one of the more stable clusters) is concentrated in Silver Lake and Echo Park, which correlates with the stable moderate/stable exclusive typology on the UDP map. Cluster 1 (census tracts with extremely high percent change in bachelor's degrees and a notably high percent change in family and nonfamily income and rents) is located in Downtown. The UDP map shows this area as at risk/advanced gentrification. Lastly, Cluster 0 (census tracts with a high percent change in nonfamily income with and without inflation) is distributed across the map and does not translate easily onto the UDP map.

According to the UDP map, many census tracts across the six neighborhoods are at risk of gentrification. However, the cluster analysis indicates which key indicators are correlated with different stages of gentrification. It appears that a large increase in rents and percent of the population with a bachelor's degree and above are correlated with advanced gentrification in the Downtown, Silver Lake, Echo Park areas. This information could be valuable to policymakers, who can tailor displacement interventions accordingly.

### Mapping Land Value Percent Change

## Conclusions and Future Research
