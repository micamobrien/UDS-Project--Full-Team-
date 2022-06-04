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

We create 5 clusters of the 128 census tracts in Westlake, Downtown, Pico-Union, Echo Park, Silver Lake, and Koreatown to better understand similarities and differences across these neighborhoods in terms of demographic change over time. We find that 2 of the clusters, which make up a majority of the census tracts (90 in total), are fairly stable over the ten year period, meaning they do not have particularly high rates of change in any of the census indicators. The 3 other clusters represent varying degrees of neighborhood change with one cluster exhibiting a dramatic change in racial demographics, education level, and rent, one cluster exihibiting some change in demographics, and another cluster exhibiting dramatic change in nonfamily income. When we map the clusters, we see that cluster 4 (a cluster with some of the more stable census tracts) appear to be grouped on the outskirts of the map in the north, west, and south. Cluster 1, which includes census tracts with some notable deomgraphic change, appears to be concentrated in the southern part of the map. Clusters 0 and 3--which also had high rates of change--appear to be sprinkled throughout.  

The clusters predictably become more visually distinct when we incorporate dummy variables for the neighborhoods into the cluster analysis. We see clear clusters in Koreatown and  Silver Lake/Echo Park in particular. When we map the clusters next to the Urban Displacement Project's Gentrification Typology map, greater patterns emerge. UDP has 8 distinct stages of gentrification, including: advanced gentrification, at-risk of gentrification, becoming exclusive, early/ongoing gentrification, low-income/susceptible to displacement, ongoing displacement, stable moderate/mixed income, and stable/advanced exclusive. We assigned numeric values to each stage to more easily compare it with the 5 clusters of our data. We assigned advanced gentrification as 4 and stable/advanced exclusive as 0. 

We see that cluster 4 (one of the more stable clusters) is concentrated in Koreatown. On the UDP map, this area has medium and rising gentrification/displacement risk (gentrification has intensified on the west side of the neighborhood and appears to be moving eastward). Cluster 3 (which has a high percent change in white population) is clustered in the southwest area, which is Pico-Union/Westlake. On the UDP map, this area has medium to high gentrification/displacement risk. Cluster 2 (one of the more stable clusters) is concentrated in Silver Lake and Echo Park, which correlates with the stable moderate/stable exclusive typology on the UDP map. Cluster 1 (census tracts with extremely high percent change in bachelor's degrees and a notably high percent change in family and nonfamily income and rents) is located in Downtown. The UDP map shows this area as at risk/advanced gentrification. Lastly, Cluster 0 (census tracts with a high percent change in nonfamily income with and without inflation) is distributed across the map and does not translate easily onto the UDP map.

According to the UDP map, many census tracts across the six neighborhoods are at risk of gentrification. However, the cluster analysis indicates which key indicators are correlated with different stages of gentrification. It appears that a large increase in rents and percent of the population with a bachelor's degree and above are correlated with advanced gentrification in the Downtown, Silver Lake, Echo Park areas. This information could be valuable to policymakers, who can tailor displacement interventions accordingly.   

### Predictive Modeling with the Land Value Dataset (Final Notebook 2 - Random Forests)
We created several random forests models for the percent change in land value from 2010 to 2020 with and without price adjusted to inflation. Factors we use for the predicition models include percent change of nonfamily income, percent change of rent, percent change of average number of ppl per household, percent change of numbers of bachelors, percent change of family income and percent change of white population. 

The accuracy score for random forests model 1 and 2 are both 0.6443. In terms of confusion matrix, the true positive number is 9 (6%), the true negative number is 87 (58.4%), the false positive number is 15 (10.1%) and the false negative number is 38 (25.5%).

Our model correctly predict 58.4% in the negative class and 6% in the positive class. In our case, the negative class is considered the less gentrified class with percent change of land value below the mean and the positive class is considered the more gentrified class with percent change of the land value higher than the mean.

Prediction for the less gentrified class is pretty accurate, however, not so much for the more gentrified class. One possible reason could be the distribution of our data where majority of the rows are concentrated in the less gentrified class causing the lack of training and testing samples for the upper end. It could also be caused by a few outliers. Next time, we might try to drop the outlier samples and focus on the range where majority of the samples are located.

In terms of the comparison of with and without inflation, there is no apparent difference between the two predictions. They have the same accuracy score and confusion matrix distribution. We think that the inflation rate (1.19%) is not big enough to create a huge difference in the prediction. In the future, it would be interesting for us to look at the years around 2008 and 2020 where there were higher inflation rates.

The rank of importance of each factor for the prediction is percent change of nonfamily income, percent change of rent, percent change of average number of ppl per household, percent change of numbers of bachelors, percent change of family income and percent change of white population. The percent of nonfamily income plays the greatest role in this prediction model. This result makes a lot of sense because gentrification, a lot of the time, is associated with people who are single with increasing income driving up prices of the neighborhoods.

### Mapping Land Value Percent Change

We created 3 sets of maps to demonstrate the land value percent change from 2010 to 2020. First we mapped out the difference between land value percent change with inflation and land value percent change without inflation. From the two maps, we see there is little difference, so we continue to use land value percent change witth inflation to compare with neighborhood boundary map. The reason was to see where these census tracts are located and see then make a conclusion of which neighborhood has been experiencing the most percent change in land value.

Our main takeaway is that some census tracts have experienced the most change in land value in Koreatown. However, in average, Westlake was shown with the higher percent change, whereas  has the smallest percent change in land value.


## Conclusions and Future Research
Given the high level of change that has taken place since 2010, it's clear that the Westlake area is particularly vulnerable to gentrification. However unlike its neighbors to east in Downtown and North in Silverlake, most of the historic residents have persisted in residing in their communities. There is much that can be done to ensure that historic residents can continue to live in their communities, to not only survive but also thrive amidst the large-scale economic development taking place across the city. 

Future research in the Westlake should focus on the needs of residents and qualitative methods would greatly provide context to the census data change. It would be good to know how residents' experience/views on neighborhood change differs based on their census block. Our group also did not look into the tax or Zillow data which the Urban Displacement Project did look into. Expanding our variables and sample size (i.e. neighborhoods) would also allow us to broaden our scope and bring in more insight to our project. 








