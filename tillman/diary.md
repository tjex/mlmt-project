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


## March 3

- do we want to drop the milisecond division?

Thinking about creating the data init template:
- what groupings will be needed? Make more than is needed.
- is there a consistent naming scheme?

desired data structure = `[unique_seq_name] + [unique_tag_id] + [time_stamp] + [x, y, z] + [unique_activity]`

we want one dataframe structure that is comprised of the groupings:
- sequence name
- tag id
- activity

## Zoom Meeting

chunk the data together as one second
decided on 6 or so experiments
decided to drop time series more or less. will make things too complex.

## Zoom Meeting March 6th

- not looking for a specific number of models, just that we implement and explore them well
- which x, y, z pos for which sensor is best suited for prediction? <- feature selection / engineering
- synchronizing by interpolation and sampling
- NB, support vector, anomaly detection

## Model Review

### KNN

Classifies based on the input data's features. Data with certain features will be clustered together. Data in 
these clusters will have labels (you have to have labels to do KNN). The model will then assign a label to 
the new input data based on the labels on the *nearest neighbours*. Higher K value will take into account more 
neigbours to derive the 'correct' label. 

The nearest neighbours are found by calculating the euclidean distances between the neighbours. 

k=3 means 'find the 3 closest neighbours (based on their euclidean distances)

### SVM (Support Vector Machine)

Classifies by dividing the data points by fitting a plane in the largest divisional space between the data points. 
The 'largest space' is found by calculating a margin, which is the distance from the divisional plane to 
the next closest data points, thereafter called 'support vectors'. 

SVM's are really sensetive to outliers. Outliers can ruin the the placement of the divisional plane and also the 
creation of margins. This is because the SVM does not consider weightings when encountering data points. 

eg one signular data point from class A, which falls incredibly close to class B, will still cause the plane to be placed on the 
in between all instances of A and B, despite the vast majority of data being far away.

To compensate for this, we need to allow for missclassification. Allowing for missclassification enables outliers to 
have less of an effect on the placement of an appropriate divisional line. This is an example of the bias / variance 
tradeoff that's inherit it all ML implementations.

When we allow for misscalssifications, it's called a soft-margin. Only at this point is it called a Support Vector Machine. 
This name comes from the fact that observations on or within the margin are called 'support vectors'. 
When not allowing for missclasification we are using a Maximal Margin Classifier.


### Outlier Detection

Identifying data points that are anomalous to the rest of the data set. This can act as a type of data 
filter or pre-training step. Often used in business environments to detect occurences that do not follow 
expected patterns and can therefore signal that something is wrong and should be looked at.

This could help us to clean the data and create more accurate data sets. 
It can also be used in time series data, as it can take time into account and use it as a identifier to 
base its comparisons on.
