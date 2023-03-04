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

![ml-davide-sensordata0](documentation/images/experiments/ml-davide-sensordata-0.png)

It appeared that there were some correlations between labels and individual coordinates, especially for the x-coordinates.
After generating this graph we observed there to be fairly long periods of time where one sensor does not provide any data

![one-param-one-tag](documentation/images/experiments/one-param-one-tag.png)

After the second project meeting we decided on the following direction:


## Cleaning The Data 

Manually editing the data file to provide column headings and removing the subsecond unit. 
Makes data handling easier and decreases lines of code and therefore chance of buggy code.
