# IIT_ke_gobhi-IITR-
created a heart rate prediction model with the help of the ensemble model
Loading Of Datasets

We has 3 files - train, test, sample. I am going to extract the HR column of the sample file which will be used as y_true for out test data. 

# Explotary Data Analysis

-Checking of Datatype and Missing values
-There are 2 object type columns and the target column is continous , therefore it is a linear regression problem.   Also there is not missing values in the dataset.
 we will drop the uuid column , there is no use of it.
-From the value_counts of each columns you can understand that datasetId column is a constant column wich is equal  to 2. So  we will drop it.
-I also dropped the "uuid" column which is just a ID column.
-We have also a object column called condition , I am going to convert that column to numerical column by using a   %allocation method. I am going to use the formula like = (Count of that value)/(total values in that column)


# Choosing the Model.
-The target column here is continous, so this is a regression problem , there are many ML  algorithms to solve it ,  like Linear Regression, DecisionTree Regression, RandomForest Regression , Support Vector  Regression. Lets  analyze each of them.
-First we are removing highly correlated data columns.
-The most of the values of the heart-rates are gathered within the 55-85.
-In linear regression the features will be linearly related to the target column , but in this case most of the   features are not linear , so it linear regression will not able to capture all complexiciteis of the data. So  we  will first apply the non-linear models.
-You can see there are outliers in the target column but, we dont remove them , as humans can have heart rate  greater than usual( >100) , so we dont remove them. I can say that very much people whose heart rate is determined  are patients. Useful Infomation.

# Results of all Models:
Decision Tree:
 Accuracy: 0.9965361458905129
 R squared: 0.9965361458905129
Random Forest:
 Accuracy: 0.9988773982616372
 R squared: 0.9988773982616372
Support Vector Machine:
 Accuracy: 0.963901328198551
 R squared: 0.963901328198551
Gradient Boosting
 Accuracy: 0.9980654442704989
XGBoost Regressor:
 Accuracy: 0.9988792799835
Linear Regressor:
 R squared: 0.9763005772194225
Voting Regressor:
 score:0.9975959738698421


After seeing the performance of the each regressor , I am decided to use the ensemble of the model.The reason which would be like some base models, like Random Forest, Support Vector ,XGBoost, and Decision Tree, are effective at capturing nonlinear relationships as well as linear relationships and they all are also non-sensitive to outliers, while others, like Linear Regression, may perform better in capturing linear relationships but sensitive to outliers.As We all know ,in this case outliers are important. The ensemble can adapt to different types of relationships in the data as well as in the outliers.


# Comparison of the predictions of the different models on the test data.
	predictions	actuals
0	75.296309	75.206050
1	80.744938	80.870132
2	62.242087	62.313063
3	66.366923	66.336924
4	64.315921	64.422596
5	57.028245	56.061095
6	75.045416	75.543673
7	62.453680	62.458281
8	56.819444	56.271876
9	71.237896	71.201501

Though the model is good , As we have some outliers , it can be possible that we have some chances that our model will not work on the outliers, lets see the predictions vs actuals plot for X_test

# Final Model
 I am going to store the final model as voting regresssor , the reference columns,the conditioning function used  for transforming the *Condition* column to numerical column  the scaler parameters.


