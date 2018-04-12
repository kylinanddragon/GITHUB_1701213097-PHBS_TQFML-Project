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
3.	Basic information about borrower: Income, education background, age, job, city, marital status.
4.	Index representing borrower’s credit history: credit score, line of credit, all kinds of credit report and authentication. 
5.	Brief introduction of the usage of money. 
2-5 are all potential **independent variables** for the model.

## Possible supported theory
Utility function of household, mean-variance investor, behavior finance theory about familiarity and availability, etc.

## Brief plan:
#### 1. Preprocessing of data

**Dependent variable** can be put into three categroies to show whether the P2P is successful. 
**Independent variable** should be normalized or standardized and some outliers should be removed. Also,PCA or LDA methods may be used for the credit history data to reduce the curse of dimensionality. I give a brief description of basic information about p2p contract data below.
Randomly divide training set and test set.

| Variable name      |  unit  |  range     | median  | mean  |
| -------------      |-------:|-----------:| -------:|------:|
| principal          |RMB yuan| 3000-500000|  43100  | 66027 |
| interest rate      |        | 9.5%-24%   |  15%    | 14.05%|
| maturity           |  month |    3-36    |   18    |  17.52|

You can find the following graph showing the histogram of them.

#### 2. Prediction of the model 
Using many kinds of machine learning method (logistic regression, SVM, KNN, decision tree) to form a good model to predict whether it will be a success or failure. Using majority voting to increase the performance of the model. Try to balance the bias and variance by regularization. 
For the fifth part of the data, I may try to process them with sentiment analysis but there are still many problems here. How to do work stemming and decide gram for Chinese may be hard as this language is really complicated.

#### 3. Measurement of model performance
For the measurement of the performance of the model, I plan to use accuracy as a measure of model performance. And base on this model, give potential borrower advice on whether their condition can get the loan or they should increase interest rate or do something similar to attract more lenders. In this way, this platform can work better to match potential borrowers and lenders.

#### 4. Possible extension
Time permitted, may do comparison with other P2P platform data to show the robustness of the predicting model.

