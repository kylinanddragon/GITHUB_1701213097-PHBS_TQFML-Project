# GITHUB_1701213097-PHBS_TQFML-Project
This include analysis on one platform of small amount credit in China——Renren dai
Repostiory name：Analysis on P2P success 
Team members: Winnie Wang (Wang Xinbo)
Data set: Over 9000 samples on Renren dai website. 
Renren dai is one of the biggest online P2P website in China. It is honored as top 100 internet companies in both 2015 and 2016.
The data mainly contains five kinds of information.
1)	Whether the p2p contract is success. This is used as dependent variable here.
2)	Basic information about p2p contract including principal, interest rate,
duration (Need to be standardized or normalized, may encounter problem with few outliers)
3)	Basic information about borrower: Income, education background, age, job, city, marital status.
4)	Index representing borrower’s credit history: credit score, line of credit, all kinds of credit report and authentication. (Many variables here in 3 and 4, so PCA or LDA can be applied here to reduce the dimensionality.)
5)	Brief introduction of the usage of money. (Sentiment analysis here. May encounter the problem of hard to do word stemming and decide gram. Possibly I can do analysis on some key words)

Possible supported theory includes: Utility function of household, mean-variance investor, behavior finance theory about familiarity and availability, etc.

Brief plan:
Using many kinds of machine learning method (logistic regression, SVM, KNN, decision tree) to form a good model to predict whether it will be a success or failure. Using accuracy as a measure of model performance. And base on this model, give potential borrower advice on whether their condition can get the loan or they should increase interest rate or do something similar to attract more lenders.
Time permitted, may do comparison with other P2P platform data.
