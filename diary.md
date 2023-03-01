# Diary

## Problems

1. based on the given data, has a person fallen down?
2. based on the given data, create a 3d heatmap of movement. When datapoints enter this spot, they are likely to be the same movement.
3. based on a given movement, which movement is most likely to follow next?
4. can we predit whether someone has fallen, based on their current movement?

## Interpreting the Data

- create snapshots of time series data 
- average out the small movements, defining them as no movement
- we are interested in the *change* in data (between positional data and time)
- rate of change / distance range of movement
- look at the distance relationships of the sensors to one another
- the data / model is very reliant on the size of the person. Sensor data from an adult, will appear very different than sensor data from a chid.
    - therefore the distances between the sensors, and the change in those distances is an important observations.

## Open Questions

- how are the postions of the sensors tracked? Are they relative to a central position, or distances of relay points?
- why are the data samples all in sequenti time? Why were the sensors not pinging at the same time / being processed at the same time?
    - this will make the interpretation of the data difficult
    - it puts importance on creating snapshots / averages of time

## Technical Approaches

- time series analysis
- KNN (as similar averages of movement should reside in similar regions)

Time series data can be classified into two main categories:

    Stock time series data means measuring attributes at a certain point in time, like a static snapshot of the information as it was.
    Flow time series data means measuring the activity of the attributes over a certain period, which is generally part of the total whole and makes up a portion of the results.

Box-Jenkins Multivariate Models: Multivariate models are used to analyze more than one time-dependent variable, such as temperature and humidity, over time.   
https://machinelearningmastery.com/gentle-introduction-box-jenkins-method-time-series-forecasting/  

## Zoom meeting
- very large dimensionality
- probability:
    (sensor|x, t)
    (sensor|y, t)
    ...
- ask 'for each action, how are the positions distributed for x, y, z (for each sensor)'
    - eg make a histogram of this.
- model with qda (quadratic descrim analysis)
- naive bayes will fit (suggests bob)
- find the activity with the highest log likleyhood
- predict per body sensor. What is the liklihood the ankle sensor is sitting.
    - integrate into an 'ensemble model', which integrates all the above into one. 
Break into simpler problems:
    - one sensor, one coordinate, see how well we do
    - one sensor, three coordinates, see how well
- what he would like to see:
    - the above, basically see how far we can go.
- sounds to me that in essence we drop the timestamp column totally

## March 1

Vira:    
- for a model based on distribution of coord data (not time series), z coord is the most descriptive value
- using support vector machine is a good approach
- tries to divide the data points with a plane

We should look at 3d scatter plotting.


