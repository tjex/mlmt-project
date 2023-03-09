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

## Cross Validation 

Allows us to assess many different ml models in one function.

The K-Fold cross-validation is used to evaluate the performance of the model. 
The GridSearchCV is used to find the best hyperparameters for the model.
Cross-validation is a technique that is used to evaluate the performance of the model. 
In cross-validation, the data is split into k-folds, where each fold is used for testing at least once.

Cross validation with kfolds. 
kfolds splits the training data up into nNumber of folds which are further segments (indicies) of testing / training data. 
It then iteratively sequences through these segments using systematic groupings of testing / training data, along with 
different given model parameters to derive the best combination of model+parameters given the original data set. 

Given an estimator, the cross-validation object and the input dataset, the `cross_val_score` splits the data 
repeatedly into a training and a testing set, trains the estimator using the training set and computes the scores 
based on the testing set for each iteration of cross-validation.

The grid search object performs a search over all possible combinations of hyperparameters in the grid using 
the k-fold cross-validation to evaluate the model's performance on each fold.

## Process

- import the data
- check the frequencies of target value (activities)
- plot box plots to check for outliers
- plot histograms to check distributions (if some of the data is skewed or not)
- encode the categorical data
- remove A01 sequence from the data (to not just create a person identifier)
- create test and train data 
- scale the features (see above why)
- find the best model settings with cross validation
- train the model
- evaluate the model


## Remarks / Open Questions


why are some box plots not showing data?
- davide thinks some of the data points have super outliers so they are not even in the plot.
how to implement the a01 sequence as a test?
SVM is very demanding on machine resources.

[x] Remove the sequences before training
look at the different kernals and try argue why some are better than others.
reserach cross validation - look at lab 5
[x] split data by davide's method / find a method?
label columns in score table





