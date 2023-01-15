---
title: "Classifying celestial objects with ML"
categories:
  - posts
tags:
  - machine_learning
  - classification
  - XGBoost
  - Sci-kit Learn

header:
  #teaser: "/assets/images/space/space_teaser.png"
  #overlay_image: "/assets/images/space/space_header.png"
---

The aim of this notebook is the classification of observations of astronomical objects in three different categories: stars, galaxies, quasars.
To do so I use data from the [Sloan Digital Sky Survey Classification](https://www.sdss.org/).

[See on Github](https://github.com/HelenaCanever/Classifying-celestial-objects-with-ML){: .btn .btn--primary}

## The data
The Sloan Digital Sky Survey is a project that periodically provides data from space imaging free to the public. This project specifically uses data from the [RD14](https://www.sdss.org/dr14/) data release. 

For this purpose a special 2.5 m diameter telescope was built at the Apache Point Observatory in New Mexico, USA. The telescope uses a camera of 30 CCD-Chips with 2048x2048 image points each. The chips are ordered in 5 rows with 6 chips in each row. Each row observes the space through different optical filters (u, g, r, i, z) at wavelengths of approximately 354, 476, 628, 769, 925 nm.

![Uploading image.png…](https://www.sdss.org/wp-content/uploads/2016/07/sdss_gaulme1.jpg)

The dataset contains the following features:
### Object identity and position
- objid = Object Identifier 
- ra = J2000 Right Ascension (r-band)
- dec = J2000 Declination (r-band)

### Filters
- u = better of DeV/Exp magnitude fit
- g = better of DeV/Exp magnitude fit
- r = better of DeV/Exp magnitude fit
- i = better of DeV/Exp magnitude fit
- z = better of DeV/Exp magnitude fit

### Acquisition metadata
- run = Run Number 
- rereun = Rerun Number 
- camcol = Camera column 
- field = Field number

### Object info
- specobjid = Object Identifier 
- class = object class (galaxy, star or quasar object)
- redshift = Final Redshift 
- plate = plate number 
- mjd = MJD of observation 
- fiberid = fiber ID 

Some features are removed as they consist of unique identifiers or are irrelevant to the identification of astronomical objects:
`objid`, `specobjid`,`fiberid`,`mjd`,`plate`, `rerun`, `run`

The following color channels are also removed, as they are highly correlated with each other and another channel:
`r`, `i`, `z`

## Training and optimizing the model

The algorithm chosen for the classification task is XGBoost Classifier.
Algorythm optimization is achieved with a gridsearch and the parameters of the best performing model are:
`{'gamma': 1,
 'learning_rate': 0.05,
 'max_depth': 6,
 'min_child_weight': 1,
 'n_estimators': 100}`

After optimization the scores for the train and test set are, respectively 0.998 and 0.99.
