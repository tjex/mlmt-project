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

The GridSearchCV is used to find the best hyperparameters for the model.
Cross-validation is a technique that is used to evaluate the performance of the model. 

kfolds splits the training data into nNumber of folds which are further segments (indicies) of testing / training data. 
It then iteratively sequences through these segments using systematic groupings of testing / training data, along with 
different given model parameters to derive the best combination of model+parameters given the original data set. 

The grid search object performs a search over all possible combinations of hyperparameters in the grid using 
the k-fold cross-validation to evaluate the model's performance on each fold.

It then returns the combination of hyperparameters which achieve the best accuracy.

gamma controls the smoothness of the decision boundary for polynomial and sigmoid kernals. For the rbf kernal 
the gamma controls the complexity of the boundaries. The linear kernal does not use gamma as it's based on 
a straight line. 

Linear Kernel: A linear kernel is used when the decision boundary between classes is expected to be a straight line. 
It is the simplest kernel function, and it works well when there is a clear linear separation between the classes. 
However, it may not work well when the data is not linearly separable.

Polynomial Kernel: A polynomial kernel is used when the decision boundary between classes is expected to be a polynomial function. 
This kernel function has two parameters, degree and gamma. 
The degree parameter controls the order of the polynomial function, and the gamma parameter controls the smoothness of the decision boundary. 
A higher degree can model more complex decision boundaries, but it can also lead to overfitting.

Radial Basis Function (RBF) Kernel: An RBF kernel is the most commonly used kernel in SVC. 
It is used when the decision boundary between classes is expected to be nonlinear and smooth. 
It has one parameter, gamma, which controls the width of the Gaussian kernel. 
A larger gamma leads to a more complex decision boundary, and a smaller gamma leads to a simpler decision boundary.

Sigmoid Kernel: A sigmoid kernel is used when the decision boundary between classes is expected to be a sigmoid function. 
It has two parameters, gamma and coef0. 
The gamma parameter controls the smoothness of the decision boundary, and the coef0 parameter controls the bias of the sigmoid function. 
This kernel function can work well when the data is non-linearly separable, but it is less commonly used than the other kernel functions.

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
[x] look at the different kernals and try argue why some are better than others.
[x] reserach cross validation - look at lab 5
[x] split data by davide's method / find a method?
label columns in score table





