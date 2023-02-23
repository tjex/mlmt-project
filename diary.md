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

## Open Questions

- how are the postions of the sensors tracked? Are they relative to a central position, or distances of relay points?
- why are the data samples all in sequential time? Why were the sensors not pinging at the same time / being processed at the same time?
    - this will make the interpretation of the data difficult
    - it puts importance on creating snapshots / averages of time


