# Project 2
Student: Yuxuan Qian (A20484572)

## Boosting Trees
* __What does the model you have implemented do and when should it be used?__<br />
The gradient boosting tree I had implemented is one of the machine learning methods that can predict the regression. Since the gradient boosting algorithm trains data by combining several weak learners, I first created the `DcisionTreeRegressor` class which is applied to predict the regression data by decision tree to support a learner that the gradient boosting algorithm can integrate. Thus, the model will be utilized if we want to predict the data for linear regression.
  
* __How did you test your model to determine if it is working reasonably correctly?__<br />
I tested my model with 4 test cases. The first three cases are randomly generated regression data, and the last is the data about US housing prices. All data were first split into 80% training dataset and 20% test dataset. After importing the training data into the model, we can predict the by inputting x-testing data into the trained model. Finally, I measured the performance of the model by r square and the plot of the actual vs the prediction. The r square in all tests is more than 0.85, and the plot is roughly a line through the origin. Those show the model predicted well.
  
* __What parameters have you exposed to users of your implementation in order to tune performance? (Also perhaps provide some basic usage examples.)__<br />
  
GradientBoostingTree(n_estimators=100, rate=0.1, max_depth=3, min_samples_split=2, tol=10)
`<br/>
`n_estimators`: the number of estimators in the gradient boosting algorithm. An estimator is a decision tree that is generated by `DcisionTreeRegressor` <br/>
`rate`: the learning rate <br/>
`max depth`: the maximum depth of the tree. The value is inputted to `DcisionTreeRegressor` to control the maximum depth of an estimator <br/>
`min_samples_split`: the splitting requirement of minimum samples and is imported into `DcisionTreeRegressor`<br/>
`tol`: tolerance. It is an `int` value and controls the early stopping. For each new estimator, the model calculates the loss (mean square error) by the previous residual and predicted residual. If the loss is less than the current best loss, i.e. the model is still improving, the model will update the optimal loss and reset "tol" to the parameter we set. Otherwise, `tol` is decremented by 1 and an early stop occurs when `tol` is 0. <br/><br/>

_Usage Example:_ <br/>
1. Download the file called `Gradient_Dcision_Tree.py` <br/>
2. When using, use the following codes: <br/>
```
from Gradient_Dcision_Tree import GradientBoostingTree

x_train = 'your x training data set'
y_train = 'your y training data set'

x_test = 'your x test data set'
y_test = 'your y test data set'

model = GradientBoostingTree(n_estimators=100, rate=0.1, max_depth=3, min_samples_split=2, tol=10)
model.fit(x_train, y_train)

model.predict(x_test)
```
<br/>
Also, you can use without the parameters:
```
from Gradient_Dcision_Tree import GradientBoostingTree

x_train = 'your x training data set'
y_train = 'your y training data set'

x_test = 'your x test data set'
y_test = 'your y test data set'

model = GradientBoostingTree()
model.fit(x_train, y_train)

model.predict(x_test)
```


* __Are there specific inputs that your implementation has trouble with? Given more time, could you work around these or is it fundamental?__<br />
