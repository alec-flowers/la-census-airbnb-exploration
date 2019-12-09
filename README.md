# Census & Airbnb Data Exploration
Medium Article - https://medium.com/@alec.flowers00/psychology-crime-and-togas-fb58c21af328
## Overview
The purpose of this analysis was to write a Medium article that was insightful while building my expertise manipulating and analyzing data. I decided to work with Airbnb data and chose Los Angeles as my city of choice. I wanted to also explore correlations between Airbnb price per day data and data from the Los Angeles census. Because I was writing an article I wanted to have be able to include items that were visually striking and played around with wordmaps, scatterplots, and geo-visualizations using leaflet. 

## Airbnb Text Analysis
You get such a small window to make an impression on Airbnb. I figured looking into Airbnb titles would turn up some interesting trends. I used nltk to strip, lemmatize, and remove stopwords from the titles. I wanted a very visual way to display the data I was working with for the medium article and played around with wordmaps to make that happen. 

I wanted to look into title word choice by review rating, however when I was downloading LA review data I was getting a corrupted file and for the sake of time moved on to the next section. 


## Airbnb Price and LA Census Correlations
Because the census data and the airbnb data are at different levels of granularity you have to aggregate the census data from the tract level up to the neighborhood level. However, it isn't as simple as summing all the categories toghether. For crime data the statistic we are measuring is rate of crime per 1000 people. Therefore a sum would wildly overstate the crime rates. To overcome this issue I weighted the rates by the population percentage that each tract contributed to the overall neighborhood. 

When looking into the correlations between the crime data and price it was clear that all the distributions for crime are heavily skewed towards 0. To overcome this I log tranformed the skewed data to get something closer to a normal distribution. Because some of the crime numbers were decimals, this log transformation turned them negative and when I tried to use Seaborne pairplot it wasn't happy. I then went and added 1 to each value and then applied the log transformation. This really helped display the linear correlations in the pairplot and we saw the pearsons coefficient change (in a more meanigful direction). 

## Instructions to Run:
Disclaimer: You will need to download data from the below source to fully run the jupyter notebook. This file was too large to upload to GitHub!

https://ladata.myneighborhooddata.org/#!/view-data
Go to this link and download the Citizen Variables Connect data. It should download a csv with the following title -  Citizen_Connect_Variables__LA_.csv

### Files
LA Exploration.ipynb - Jupyter notebook where all the above work was completed. Read data in, manipulated data, and vizualized data.\
listings_la.csv - Consolidate Airbnb data \
neighbourhoods.geojson - LA Neighborhood geojson coordinates to visualize boundaries of the neighborhoods/
map3.html - Geo-Vizualization of Los Angeles overlaid by Leaflet Cloropleth graphs/

### Libraries
Pandas - data manipulation\
Numpy - number functions\
GeoPandas - geographical visualizations\
wordcloud - generate wordclouds\
nltk - text processing\
sodapy - API connection to import data\
seaborne - data visualization\

