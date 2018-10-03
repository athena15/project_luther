# Project Luther - Predicting King County Home Sale Prices

Brenner Heintz

## Background

Kaggle.com features a dataset of King County home sale data from 2014-2015. The data includes extensive data for each home sale including the sale price, number of bedrooms & bathrooms, square footage of the home, latitude/longitude data, and others. There are 21,613 observations in total. The data can be found at [[https://www.kaggle.com/harlfoxem/housesalesprediction]{.underline}](https://www.kaggle.com/harlfoxem/housesalesprediction).

The goal of my analysis is to use the existing features, along with additional sources of data and feature engineering, to predict the the total cost of homes using linear regression.

This information is important/interesting because of the explosion of housing prices in King County over the last several years. I'm specifically interested in finding out which factors have the greatest impact on price, beyond the obvious - square footage and number of bedrooms, for example. It's a well-known saying that it's all about "Location, Location, Location" in real estate - and I will attempt to see whether this is right by bringing in multiple location-based features.

## Data

Existing data columns include (bolding columns I am likely to use):

-   Id - a notation for a house

-   **Date - Date house was sold**

-   **Price - Price is prediction target**

-   **Bedrooms - Number of Bedrooms/House**

-   **Bathrooms - Number of bathrooms/bedrooms**

-   **Sqft\_living - square footage of the home**

-   **Sqft\_lot - square footage of the lot**

-   **Floors - Total floors (levels) in house**

-   **Waterfront - House which has a view to a waterfront**

-   View - Has been viewed

-   **Condition - How good the condition is ( Overall )**

-   **Grade - overall grade given to the housing unit, based on King County grading system**

-   **Sqft\_above - square footage of house apart from basement**

-   Sqft\_basement - square footage of the basement

-   **Yr\_built - Built Year**

-   **Yr\_renovated - Year when house was renovated**

-   **Zipcode - zip**

-   **Lat - Latitude coordinate**

-   **Long - Longitude coordinate**

-   **Sqft\_living15 - Living room area in 2015(implies\-- some renovations) This might or might not have affected the lotsize area **

-   **Sqft\_lot15 - lotSize area in 2015(implies\-- some renovations)**


Potential additional features to engineer:

-   \$/square foot

-   Living area/Total Area

-   Type of Neighborhood (Urban/Suburban/Rural)

-   School District

-   Density Index \[unsure about how to find\]

-   House is on Arterial Street \[unsure about how to find this info\]

-   How House is Zoned

### Minimum Viable Product:

I am planning to use Google Maps API to get the address of the home nearest to the latitude/longitude coordinates. This won't give me the exact address of a house (for certain), but will be accurate to within a few hundred feet, so I'll be able to use each address to determine information about the neighborhood (if not the *specific* house).

I then plan to input the addresses I received from Google Maps and use Python to create a list of those addresses, then use Selenium to upload batches of lists to the US Census web page, receive that information back from the page, and read that into my dataframe. The data from the Census provides info about which Census Tract each address is in, along with detailed neighborhood demographics and income data. I plan to use data from 2015, since my dataset is from that timeframe.

From that dataset, I plan primarily to use Median household income, but given more time I'd like to use features including median age of residents, size of households, etc.

### Additional Sources of Data

Given additional time, I'd also like to scrape Zillow for neighborhood info (including Walk Score, Transit Score, the grades of local schools, and others).

### Concerns/Known Unknowns

-   The King County housing market has been so hot that even the time difference between the earliest and latest sale dates in the data set may be a significant factor in inflating more recent home prices.

-   My web scraping task may not be that "hard" given that it's not scraping 10,000 pages, but programmatically batching data to upload to the US Census site, getting that data back, and reading it into my dataframe.

-   I'm unable to get addresses for each home that are the correct home *for certain*, as opposed to the neighbor's home given the density of the area. Still, I think that knowing the block will give me more than enough info to work with.
