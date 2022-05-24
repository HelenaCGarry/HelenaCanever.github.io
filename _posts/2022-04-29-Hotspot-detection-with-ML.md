---
title: "Detecting Uber pickups hotspots in NY"
categories:
  - posts
tags:
  - K-Means
  - DBScan
  - Pandas
  - Plotly
  - Geopy
---

The task at hand is to use Uber data from the month of May 2014 to detect hotspots for Uber pickup in NY to better help drivers be where they are needed.

[See on Github](https://github.com/HelenaCanever/Hotspot-detection-with-ML){: .btn .btn--primary}

## The data

The dataset is obtained from the [Uber Pickups in New York City dataset](https://www.kaggle.com/datasets/fivethirtyeight/uber-pickups-in-new-york-city) on Kaggle, and focuses on the month of May 2014.


## Clustering
Ouliers are initially removed using DBScan. Hotspots are then determined using KMeans on 9 centroids.
The ideal number of centroids is based on the evaluation of the silhoutte score and inertia score of KMeans models train on different number of clusters.
The clusters are determined on an hour-by-hour and day-by-day basis.

## Data display
Clusters are displayed on an interactive Plotly graph

The map below shows the pickups hotspots hour by hour. The size of the dots is indicative of the size of the hotspot and hovering over the dots will reveal the concerned neighborhood.

{% include Hour_map_mini.html %}

This second map displays the information on a day by day basis, as the hotspots may differ, for example between the weekend and Monday.

{% include Day_map_mini.html %}




