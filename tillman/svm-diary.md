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



