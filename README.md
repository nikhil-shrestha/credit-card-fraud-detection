# Credit Card Fraud Detection
### Group Project

### Table of Content
- Dataset Overview
- Data Preprocessing and EDA
- Model Fitting 
- Results


### Dataset Overview
The dataset contains transactions made by credit cards in September 2013 by European cardholders. This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions.

It contains only numerical input variables which are the result of a PCA transformation. Unfortunately, due to confidentiality issues, we cannot provide the original features and more background information about the data. Features V1, V2, … V28 are the principal components obtained with PCA, the only features which have not been transformed with PCA are 'Time' and 'Amount'. Feature 'Time' contains the seconds elapsed between each transaction and the first transaction in the dataset. The feature 'Amount' is the transaction Amount, this feature can be used for example-dependant cost-sensitive learning. Feature 'Class' is the response variable and it takes value 1 in case of fraud and 0 otherwise.

### EDA

- Look at the distribution of the Time, Amount and Class column
- Experience the horrible imbalancy

![alt text](https://github.com/nikhil-shrestha/credit-card-fraud-detection/blob/master/images/distribution_time.png?raw=true) 

![alt text](https://github.com/nikhil-shrestha/credit-card-fraud-detection/blob/master/images/distribution_amt.png?raw=true) 

![alt text](https://github.com/nikhil-shrestha/credit-card-fraud-detection/blob/master/images/distribution.png?raw=true) 

So as you can see, there is only 0.2% fraud (570 Samples from 284,807 entries), which is a severe imbalance. If we train our model just like this, there is no chance we'll ever predict a FRAUD case. So we'll have to deal with this and this project is mainly about this topic - Dealing with Imbalanced Classification!

![alt text](https://github.com/nikhil-shrestha/credit-card-fraud-detection/blob/master/images/relation.png?raw=true) 

As you can see, the number of transactions for genuine users take a hit during late night and early morning hours. It also makes sense since most people sleep during this. On the contrary, for fraudulent transactions, the number sees sharp spikes during late hours, and during the daytime, the count is significantly less.

### Data Cleaning

- Missing Data?
- Duplicating Data?
- Outliers?

### Data Preprocessing

- PCA Transforming the Time & Amount columns
- Using the RobustScaler() to scale the Time & Amount columns
- Using SMOTE technique to solve the imbalancy

- To learn more about PCA transformations, you can read this: https://builtin.com/data-science/step-step-explanation-principal-component-analysis

- To learn about Scaling, read this: https://machinelearningmastery.com/standardscaler-and-minmaxscaler-transforms-in-python/

- To read on RobustScaler, have a look here: https://www.geeksforgeeks.org/standardscaler-minmaxscaler-and-robustscaler-techniques-ml/

### Model Fitting

- Split the Data into Training & Testing sets
- Try out different models like
  - Naive Bayes (GaussianNB)
  - Random Forest Classifier
  - K-Neighbors Classifier
  

#### Evaluation Metrics Selection
During the modeling process, we choose multiple different evaluation metrics to evaluate the performance of models based on the nature of our data:

- Accuracy
- F-1 Score
- Precision Score
- Recall Score

#### Basic Model Comparison
Using Naive Bayes as our baseline model, we first used cross validation and compared the performance of the following three models: DecisionTree, RandomForest and KNeighbors. KNN seems to perform better for this kind of problem.

![alt text](https://github.com/nikhil-shrestha/credit-card-fraud-detection/blob/master/images/score_compare.png?raw=true) 


![alt text](https://github.com/nikhil-shrestha/credit-card-fraud-detection/blob/master/images/cross_validation.png?raw=true) 
