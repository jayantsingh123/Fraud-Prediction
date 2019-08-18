# Fraud-Prediction

## Introduction
In this project, we are given a dataset related to applications for a new credit card. Each record describes an application for credit card. Every credit application is characterized by following attributes;

* ID: This is the unique identifier for a given credit application,
* dist_latest_transaction_address_km: Distance between the most recent transaction and place of application,
* email: Email address of the applicant,
* application_date: Application Date of the applicant (it is in datetime format),
* site_visits_A: No. of visits to site A,
* site_visits_B: No. of visits to site B,
* site_visits_C: No. of visits to site C,
* credit_limit: Credit limit of previous card,
* number_of_transactions: Number of transactions on most recent card, and 
* is_fraud: flag identifying an applicant as fraud or safe

Here, is_fraud is the response variable taking values 0(safe) or 1(risky). For this project, the goal is to develop a model with satisfactory discriminatory ability.

## Exploratory Data Analysis
To begin with, we have performed basic exploration of the dataset. The goal is to obtain following information regarding the data;
* Data types of different variables,
* Identify missing data, and 
* Multicollinearity Among Predicting variables.

In addition, following new features have been extracted from the variable, application_date;
* Day of the week,
* Time of the day,
* Day of the month, and
* Year.

Above information is helpful in the sense that, do the fraudsters tend to apply for new credit cards on a particular day or time of the week. In addition, EDA also helps us to identify the variables that are more likely to affect the response variable,is_fraud.   

## Model Building

### Baseline Model Using Original Set of Features
Initially, we start with a baseline model using just the basic set of original features, Credit limit, Number of transactions, and Distance between place of transaction and Credit Application. We have used Random Forests as our classification model, the reason being it is quite robust in nature. Moreover, Random Forests are least likely to overfit as well as can handle outliers and different types of variables, such as categorical or numeric. 

In the first attempt, the area under the ROC curve(i.e. AUC) is only 0.57, which is a bit better than random guessing. It should be noted that higher AUC means more discriminatory power of the algorithm. In order to increase the AUC, we designed some new features.

### Feature Engineering
We have designed some new features. These features are related to Email Domains, Credit limit, Number of Transactions, and Distance Between Place of Application and Most Recent Transaction. We performed the Feature Engineering in two steps;

* First, we divide the numeric variables;  Credit limit, Number of Transactions, and Distance Between Place of Application and Most Recent Transaction into buckets large enough not to conceal granular details but still manageable. Too many buckets are difficult to visualize sometimes. 
* Next, we compute the fraud percentage corresponding to each Email Domain, and each bucket for the numeric variables.

### Model Performance Using Engineered Features
Then, we go back to model building using engineered features as the predicting variables. We stay with the same algorithm,  Random Forests. The new features help to boost the AUC to 0.65.   

## Discussion and Conclusion
We have studied the dataset related to applications for new Credit Card. Feature Engineering helped to increase the classification ability of the model. Next step will be to use this model to predict the probabilites of a given record being fraud.  Using business knowledge we can come up with a suitable threshold so as to catch as many fraud cases as possible while keeping satisfactory precision.  
