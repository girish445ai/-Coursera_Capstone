# IBM DATA SCIENCE CAPSTONE PROJECT
## New Restaurants Location Recommendation in Vishakpatnam
![beach](https://user-images.githubusercontent.com/63008519/142022517-5e42d08e-1291-407f-ab1a-3ce457b2fdd0.jpg)
## Introduction:
To start with let me give you the context of my project.So basically vizag is also called as the "city of destiny".This City is home for many restaurants ,tourists spend a lot of time in restaurants .So, there is a lot of demand for more of them to be built. So the property builders could take advantage of this and can construct more of them and money could be made out of it. But the main problem is to select a location with less competition and more chance of growth .We are going to address this topic and try to find a answer through this project.
## Problem:
The main objective of this project is to gather data and run data analysis algorithm to find the best possible location where if the property builders construct building he could make franchices to open new restaurants at his sites.So this project aims to use the datascience and machine learning algorithms like K-mean clustering and provide an answer to the question:In Vizag(the city of destiny)-A.P-India,if a land developer want to construct a restaurants , what would be the best location to do so?
## Target Audience of this project:
The target audience of this project are the land builders/developers,and investors looking to open/invest in new restaurants in Vizag-India.Visakhapatnam is one of the fastest growing cities in the state and is slowly getting a cosmopolitan look. The city is witnessing a huge demand for restaurants, thanks to the boom in industrial and business sectors, which has ensured a change in lifestyle and fashion preferences.So this project will help them take better decision of the choice of location on opening new restaurants.
## Data:
### The following data must be acquired to solve this problem:
1. List of neighborhoods in Vizag.
2. Latitude and Longitude coordinates of the neighborhoods.This data is required in order to plot the map and also to acquire the venue details.
3. Venues of the neighborhoods specially that of restaurants,on which we will perform clustering algorithms. 

### Source's of data and methods to acquire them:
First to acquire the vizag neighbourhoods data,  we will use web scraping techniques to extract the data from this wikipedia page: https://en.wikipedia.org/wiki/Category:Neighbourhoods_in_Visakhapatnam, there are total 121 names in this page which are the neighbourhoods of vizag, which we will extract.Then we will acquire the coordinates of these neighbourhoods using Python Geocoder package as a result we will get the latitude and longitude coordinates of these neighborhoods.

Next step is to use the Foursquare API to get the venues data of these neighborhoods.Foursquare has one of the largest database collection with about 105+ million places and is used by over 150,000 developers.Foursquare API will provide us many venues we are interested in the shopping mall venue.This project will test many of the data science skills, from web scraping, working with Foursquare API, data cleaning, data wrangling,data manipulation, to data visualization(generating map using folium) and machine learning techniques(clustering) implementation.
### Methodology:
The first step is to get the neighbourhoods names of visakhapatnam by scraping the data from this wikipedia page (https://en.wikipedia.org/wiki/Category:Neighbourhoods_in_Visakhapatnam,) using BeautifulSoup library and next we need to get the coordinates ie; latitude & longitude values of each neighbours .we could do this in many ways , we can use geocoder library to get coordinates but it didnt work for me so i decided to generate the coordinates using the excelsheet extension so i saved the output data frame after scraping as a excelsheet and downloaded that excelsheet and using Geocode extension i generated the coordinates for cooresponding neighbourhoods .Then i have uploaded this new excel sheet as dataframe onto my jupiter notebook and next i visualized the neighbourhooda on the map by using Folium package.This visualization step gives us a sanity check to make sure that the geographical coordinates generated are correct and are correctly plotted.

Next, we will use the Foursquare API to get the top 100 venues of each neighbourhoods withina a radius of 3300 meters.We need to register a Foursquare API developer account in order to obtain the Foursquare ID and Foursquare secret key. We then made API calls to Foursquare API by passing the geographical coordinates of the neighbourhoods in a python loop. Foursquare will return the venue data in JSON format and we will exteact the venue name, venue category, venue lat, venue long. With this we can check how mand venues are returned for each neighbourhood usin panda code. The we will analyze each neighbourhood by grouping the rows by neighbourhood and taking the mean of the frequency of occurrence of each venue category. By doing so, we are also preparing the data for use in clustering. Since we are analysing the "Restaurants" data, we will filter the "Restaurants" as venue category for the neighbourhoods.

Lastly, we will perform clustering on the data by using k-means clustering. K-means clustering algorithm identifies k number of centroids, and then allocates every data point to the nearest cluster, while keeping the centroids as small as possible. It is one of the simplest and popular unsupervised machine learning algorithms and is particularly suited to solve the problem for this project. We will cluster the neighbourhoods into 3 clusters based on their frequency of occurrence for "Restaurants". The results will allow us to identify which neighbourhoods have higher concentration of Restaurants while which neighbourhoods have fewer number of Restaurants. Based on the occurrence of Restaurants in different neighbourhoods, it will help us to answer the question as to which neighbourhoods are most suitable to open new Restaurants.

## Results:
The results from the k-means clustering show that we can categorize the neighbourhoods into 3

clusters based on the frequency of occurrence for "Restaurants":

Cluster 0: Neighbourhoods with low number to no existence of Restaurants

Cluster 1: Neighbourhoods with moderate number of Restaurants

Cluster 2: Neighbourhoods with high concentration of Restaurants

The results of the clustering are visualized in the map below with cluster O in red colour, cluster 1 in purple colour, and cluster 2 in mint green colour.

### Discussion:
As observations noted from the map in the Results section, most of the Restaurants are concentrated in the central area of Visakhapatnam city, with the highest number in cluster 2 and moderate number in cluster 1. On the other hand, cluster 0 has very low number or no restaurants in the neighbourhoods. This represents a great opportunity and high potential areas to open new Restaurants as there is very little to no competition from existing Restaurants. Meanwhile, Restaurants in cluster 2 are likely suffering from intense competition due to oversupply and high concentration of Restaurants. From another perspective, the results also show that the oversupply of Restaurants mostly happened in the central area of the city, with the suburb area still have very few Restaurants. Therefore, this project recommends property developers to capitalize on these findings to open new Restaurants in neighbourhoods in cluster 0 with little to no competition. Property developers with unique selling propositions to stand out from the competition can also open new Restaurants in neighbourhoods in cluster 0 with moderate competition. Lastly, property developers are advised to avoid neighbourhoods in cluster 2 which already have high concentration of Restaurants and suffering from intense competition.

### Limitations and Suggestions for Future Research:
In this project, we only consider one factor i.e. frequency of occurrence of Restaurants, there are other factors such as population and income of residents that could influence the location decision of a new Restaurants. However, to the best knowledge of this researcher such data are not available to the neighbourhood level required by this project. Future research could devise a methodology to estimate such data to be used in the clustering algorithm to determine the preferred locations to open a new Restaurants. In addition, this project made use of the free Sandbox Tier Account of Foursquare API that came with limitations as to the number of API calls and results returned. Future research could make use of paid account to bypass these limitations and obtain more results.

## Conclusion:
In this project, we have gone through the process of identifying the business problem, specifying the data required, extracting and preparing the data, performing machine learning by clustering the data into 3 clusters based on their similarities, and lastly providing recommendations to the relevant stakeholders ie. property developers and investors regarding the best locations to open a new Restaurants. To answer the business question that was raised in the introduction section, the answer proposed by this project is: The neighbourhoods in cluster 0 are the most preferred locations to open a new Restaurants. The findings of this project will help the relevant stakeholders to capitalize on the opportunities on high potential locations while avoiding overcrowded areas in their decisions to open a new Restaurants.




                                                       
