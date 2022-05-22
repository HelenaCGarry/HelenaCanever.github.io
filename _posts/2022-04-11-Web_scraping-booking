---
title: "Scraping Booking.com and generating an hotels database of France's best destinations"
categories:
  - posts
tags:
  - Scrapy
  - Geopy
  - API
  - Pandas
  - Plotly
  - OpenWeatherMap
  - Nominatim
---

The goal of the project is to obtain data on different french cities and travel destination that can be potentially implemented in a recommendation app. The application should be based on real data about:
- Weather 
- Hotels in the area 

[See on Github](https://github.com/HelenaCanever/Web-scarping-and-database-generation-from-bookings.com){: .btn .btn--primary}

More specifically we are required to: 

* Scrape data from destinations 
* Get weather data from each destination 
* Get hotels' info about each destination
* Store all the information above in a data lake
* Extract, transform and load cleaned data from your datalake to a data warehouse

The destinations were chosen from the list of 35 best destinations in France published by [One Week In](https://one-week-in.com/35-cities-to-visit-in-france/) .

## Get weather data with an API 

*   Coordinates are obtained using https://nominatim.org/ 
*   Weather data is obtained from https://openweathermap.org/appid 
*   The best destinations are based on the weekly average perceived temperature

## Scrape Booking.com 

Scrapy is used to scrape the following info from booking.com:

*   hotel name,
*   Url to its booking.com page,
*   Its coordinates: latitude and longitude
*   Score given by the website users
*   Stars
*   Address
*   Text description of the hotel

The raw scraped data is available in the `scrp` folder.

## Data display
The data is displayed on an interactive map creates with Plotly.

--> add plotly graph

##  ETL

All the information is saved as .csv files (see `data`)and uploaded in an S3 bucket. An SQL Database is created ith AWS RDS.
