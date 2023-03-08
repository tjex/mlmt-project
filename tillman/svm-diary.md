# svm diary

sklearn offers three models: SVC, NuSVC and LinearSVC.   
As there is a lot of overlap in our observations between classes (activities), 
a linearSVC is not a good approach as a linearSVC attempts to fit a line between data in a singular dimension. 

The models take two inputs: 
- an array X of shape `(n_samples, n_features)` of training data
- and an array y of class labels `(n_samples)` 

The data needs to be scaled. If it isn't, the features with the largest range will completely 
dominate in the computation of the kernel matrix, which is the underlying algorithm used to calculate the 
classifiers.

## Process

- import the data
- check the frequencies of target value (activities)
- plot box plots to check for outliers
- plot histograms to check distributions (if some of the data is skewed or not)
- encode the categorical data
- remove A01 sequence from the data (to not just create a person identifier)
- create test and train data 
- scale the features (see above why)
- train the model
- evaluate the model

## Remarks / Open Questions


why are some box plots not showing data?
- davide thinks some of the data points have super outliers so they are not even in the plot.
how to implement the a01 sequence as a test?
SVM is very demanding on machine resources.

Remove the sequences before training
put classes back in f1 table
look at the different kernals and try argue why some are better than others.
reserach cross validation - look at lab 5
split data by davide's method / find a method?





