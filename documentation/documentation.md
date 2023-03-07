---
documentclass: scrartcl
title: Title
subtitle: Subtitle
author: Author
date: date
geometry: margin=2.5cm
linestretch: 1.2
fontfamily: inter
fontfamilyoptions: sfdefault
---

## Initial Meetings

- decided on a dataset based on the interesting use cases and oportunities for data handling that the sensor data was to provide.
- the data set turned out to be time series data, which made it much more complex to deal with.
    - decisions needed to be made how to handle the time data, or whether to drop it, and what effect this would have. 
- We brainstormed ways to work with the data, which lead us to consider:
    - what relationships between the sensors exist that could describe a persons movement state?
    - do all sensors need to be taken into account, or can we drop some (dimensionality reduction)
    - which are the most important sensors (chest distance from standing, sitting to lying and ankle, movement patterns)

## First Experiments

We graphed the distributions of each sensor (ie, how often does the sensor record a distance between 0 - room max)

![ml-davide-sensordata0](/images/experiments/ml-davide-sensordata-0.png)

It appeared that there were some correlations between labels and individual coordinates, especially for the x-coordinates.
After generating this graph we observed there to be fairly long periods of time where one sensor does not provide any data

![one-param-one-tag](/images/experiments/one-param-one-tag.png)


## Viras Research 

Vira collected a lot of research on many different models and noted down which ones could be good pics given 
our dataset.

## Cleaning The Data 

Manually editing the data file to provide column headings and removing the subsecond unit. 
Makes data handling easier and decreases lines of code and therefore chance of buggy code.

## Feature Generation

Davide's interpolation of the original data set created a new data set that allowed for all x,y,z coords 
of each sensor to be grouped into the same row of the new data set. This created a richer feature set 
and one that more appropriately aligned with the question of interest: which features of what sensors best 
describe an activity?

## Data Init

We wanted to have the same basis for data handling and processing across all our implementations.   
To do this we created a data initialization chunk of code that read the data file and created some preliminary data frames and arrays. 
These data types formed the basis then of further data handling.

This allowed us to be confident that each team member's implementations were using data structures (arrays, data frames, etc) that were 
in the same format and included the same data in the same order. This is important as it meant that we could confidently assert that the models were 
being trained on the same data, which meant that we could more confidently compare the performance, accuracies and other outputs of the models, despite having 
worked in different jupyter notebooks.

## Second Zoom Meeting

After the second project meeting we decided on the following direction: 

- to use SVM, Naive Bayes and KNN
- to focus on quality not quantity
- to look at implementing time series analysis, after Bob's pointers

## Process Progress

Davide worked on merging and interpolating our data set, which contained 4 sensors with 3 coordinates each. 
After the merging we have a data set that considers this data now as a 12 dimensional data set.
