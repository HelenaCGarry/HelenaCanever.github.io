---
title: "Scraping Booking.com and generating an hotel database of France's best destinations"
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

header:
  teaser: "/assets/images/hotels/hotel_teaser.png"
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
In the graph below the weather forecast and average perceived temperature for each location  It is also possible to only visualize the top five destinations (as per highest average perceived temperature).


{% include best_locations.html %}


In the floowing graph, one can display the top 20 hotels at each destination. The destinations can be chosen from the selection bar.
The map shows the name, number of stars, and rating for each hotel.


{% include best_hotels_mini.html %}


##  ETL

All the information is saved as .csv files (see `data`) and uploaded in an S3 bucket. An SQL Database is created on AWS RDS.
