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

## Findings

## Conclusions and Future Research
