# GITHUB_1701213097-PHBS_TQFML-Project
This include analysis on one platform of small amount credit in China——RenRen Dai
# Repostiory name：Analysis on P2P success 
### Team members: Winnie Wang (Wang Xinbo)
### Data set: Samples on Renren dai website. 
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
Two dataset are used for total analysis: [dataset of renren dai](https://github.com/kylinanddragon/GITHUB_1701213097-PHBS_TQFML-Project/blob/master/dataset%20of%20renren%20dai.csv) and [sentiment analysis](https://github.com/kylinanddragon/GITHUB_1701213097-PHBS_TQFML-Project/blob/master/sentiment%20analysis.csv)
More detailed decription of dataset can be found in:[data description](https://github.com/kylinanddragon/GITHUB_1701213097-PHBS_TQFML-Project/blob/master/data%20description)

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

![alt text](https://github.com/kylinanddragon/GITHUB_1701213097-PHBS_TQFML-Project/blob/master/relationship.png)

#### 2. Prediction of the model 
Using many kinds of machine learning method (logistic regression, SVM, KNN, decision tree) to form a good model to predict whether it will be a success or failure. Using majority voting to increase the performance of the model. 
I also use bagging and 
For the fifth part of the data, I try to process them with sentiment analysis and I derive two variables from it.

#### 3. Measurement of model performance
For the measurement of the performance of the model, I plan to use accuracy as a measure of model performance. And base on this model, give potential borrower advice on whether their condition can get the loan or they should increase interest rate or do something similar to attract more lenders. In this way, this platform can work better to match potential borrowers and lenders. The selection of parameters are later proved to be proper by GridSearch. 
The predicting power is quiet high using these explaining variables, the detailed data is as followed:

| Method      | Explaining variable | Accuracy | Misclassified samples|
| ----------- |--------------------:|---------:|---------------------:|
|  Logisitc   |         All         |   0.98   |         46           |
|  Perceptron |         All         |   0.97   |         62           |
|  SVC        |         All         |   0.98   |         46           |
|  kernel SVC |         All         |   0.95   |         104          |
|Decisiontree |         All         |   0.97   |         75           |
|Randomforest |         All         |   0.97   |         68           |
|  KNN        |         All         |   0.96   |         86           |
|  Perceptron |         Core        |   0.95   |         104          |
|  Logisitc   |         Core        |   0.96   |         100          |
|  SVC        |         Core        |   0.96   |         91           |
|  kernel SVC |         Core        |   0.96   |         90           |
|Decisiontree |         Core        |   0.96   |         95           |
|Randomforest |         Core        |   0.96   |         101          |
|  KNN        |         Core        |   0.96   |         93           |
                                     
For PCA method, 3-5 PCA components have relatively high predicting accuracy about 0.97, adding it to 10 components won't improve accuracy much, while deducting it to 2 will lose accuracy.
We later check that our selection of parameters and division of training/testing sample is rational.
K-fold method also give high accuracy of predicting.
Then we increase the ROC/AUC to 0.96 by using majorty voting combining methods of Logisitic,decision tree and KNN.
![alt text](https://github.com/kylinanddragon/GITHUB_1701213097-PHBS_TQFML-Project/blob/master/ROC%20AUC%20curve.png)

Bagging and Adaboosting also help improve the accuracy here.

#### 4. Method of sentiment analysis
We meet some difficulties when trying to use sentiment analysis on our dataset. We derive two sentiment variables from the description and find prediction based on these two sentiment variables can have about 0.8 accuracy. However, it is likely that this explaining power is mainly due to their relationship with core variables.

### Implentation 
#[Analysis of renrendai](https://github.com/kylinanddragon/GITHUB_1701213097-PHBS_TQFML/Project/blob/master/Analysis%20of%20renrendai.ipynb)

### Conclusion
We derive a classifier based on public information of p2p contract and applicants with *high accuracy*. This classifier contains information about *payment information of p2p contract*, *demographic information of borrower* and *credit history of borrower*.<br> And among them, though the latter two part contribute to the accuracy of model estimation, payment information itself has relatively high predicting accuracy. 
We can derive some information from borrower's description about the intent of borrowing, "urgent" borrowers are more likely to get loans compared to "stable" borrowers due to they provide higher interest rate and the certificate information are not mattered so much considering the analysis in first part.

## Possible supported theory
1. Limited attention
People's attention is limited so their main attention maybe on the interest rate, principal and maturity at first and search or rank by that. 
2. Information asymmetry
It's somehow like a lemon market that lender can't clearly find the exact quality of borrower, though credit history provide some information, it is not enough. So the influence of most direct thing related with payment dominates here.
3. People's risk preference
People who participate in p2p market and act as a lender are more likely to be risk taking person, these people care less about risk and more about return relatively.

### Further extension
Match interest rate with short-term treasury bond rate/ Extrapolate on other p2p platforms/ Tracking data of one special p2p contract to see how long it takes to gather money(Related with limited attention)
