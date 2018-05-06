# GITHUB_1701213097-PHBS_TQFML-Project
This include analysis on one platform of small amount credit in China——RenRen Dai
# Repostiory name：Analysis on P2P success 
### Team members: Winnie Wang (Wang Xinbo)
### Data set: Over 9000 samples on Renren dai website. 
Renren dai is one of the biggest online P2P website in China. It is honored as top 100 internet companies in both 2015 and 2016.

## Brief Description of dataset
The data mainly contains five kinds of information.
1.	Whether the p2p contract is success. This is used as **dependent variable** here.
2.	Basic information about p2p contract including principal, interest rate,
duration
correlation analysis show strong edvidence of their influence on p2p success
3.	Basic information about borrower: Income, education background, age, job, city, marital status.
4.	Index representing borrower’s credit history: credit score, line of credit, all kinds of credit report and authentication. (15 dummy variables here)
5.	Brief introduction of the usage of money. 
2-5 are all potential **independent variables** for the model.
Two dataset are used for total analysis: [dataset of renren dai](dataset of renren dai.csv) and [sentiment analysis](sentiment analysis.csv)
More detailed decription of dataset can be found in:[data description](GITHUB_1701213097-PHBS_TQFML-Project/data description)

## Possible supported theory
Utility function of household, mean-variance investor, behavior finance theory about familiarity and availability, etc.

## Brief plan and result:
#### 1. Preprocessing of data

**Dependent variable** can be put into three categroies to show whether the P2P is successful. 
**Independent variable** should be normalized or standardized and some outliers should be removed. Also,PCA method are used for the credit history data to reduce the curse of dimensionality. I give a brief description of basic information about p2p contract data below.
Randomly divide training set and test set.

| Variable name      |  unit  |  range     | mean  |
| -------------      |-------:|-----------:|------:|
| principal          |RMB yuan| 3000-500000| 64464 |
| interest rate      |        | 10 %-24 %  | 14.01%|
| maturity           |  month |    3-36    |  18.65|

#### 2. Prediction of the model 
Using many kinds of machine learning method (logistic regression, SVM, KNN, decision tree) to form a good model to predict whether it will be a success or failure. Using majority voting to increase the performance of the model. 
I also use bagging and 
For the fifth part of the data, I try to process them with sentiment analysis and I derive two variables from 


#### 3. Measurement of model performance
For the measurement of the performance of the model, I plan to use accuracy as a measure of model performance. And base on this model, give potential borrower advice on whether their condition can get the loan or they should increase interest rate or do something similar to attract more lenders. In this way, this platform can work better to match potential borrowers and lenders.
The predicting power is quiet high using these explaining variables, the detailed data is as followed:
                                      | Method      | Explaining variable | Accuracy | Misclassified samples|
                                      |------------:|--------------------:|---------:|---------------------:|
                                      |  Logisitc  :|         All        :|   0.98  :|         40          :|
                                      |  Perceptron:|         All        :|   0.97  :|         66          :|
                                      |  SVC       :|         All        :|   0.98  :|         37          :|
                                      |  kernel SVC:|         All        :|   0.96  :|         82          :|
                                      |Decisiontree:|         All        :|   0.97  :|         75          :|
                                      |Randomforest:|         All        :|   0.97  :|         66          :|
                                      |  KNN       :|         All        :|   0.97  :|         76          :|
                                      |  Perceptron:|         Core       :|   0.97  :|         76          :|
                                      |  Logisitc  :|         Core       :|   0.96  :|         100         :|
                                      |  SVC       :|         Core       :|   0.96  :|         91          :|
                                      |  kernel SVC:|         Core       :|   0.96  :|         90          :|
                                      |Decisiontree:|         Core       :|   0.96  :|         100         :|
                                      |Randomforest:|         Core       :|   0.96  :|         101         :|
                                      |  KNN       :|         Core       :|   0.96  :|         93          :|
                                      |-----------: |--------------------:|---------:|---------------------:|
For PCA method, 3-5 PCA components have relatively high predicting accuracy about 0.97, adding it to 10 components won't improve accuracy much, while deducting it to 2 will lose accuracy.
We later check that our selection of parameters and division of training/testing sample is rational.
K-fold method also give high accuracy of predicting.
Then we increase the ROC/AUC to 0.96 by using majorty voting combining methods of Logisitic,decision tree and KNN.
Bagging and Adaboosting also help improve the accuracy here.

#### 4. Extension
We meet some difficulties when trying to use sentiment analysis on our dataset. We derive two sentiment variables from the description and find prediction based on these two sentiment variables can have about 0.8 accuracy. However, it is likely that this explaining power is mainly due to their relationship with core variables.

### Implentation 
[Analysis of renrendai](Analysis of renrendai.ipynb)

### Conclusion
