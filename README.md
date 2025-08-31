Classification of Corporate Bond Ratings with Random Forest Model

## NON-TECHNICAL EXPLANATION OF YOUR PROJECT
The project aims to tackle the issue of classification corporate bond ratings. 
This is particularly important for bond portfolio managers who rely on credit ratings in order to manage their bond portfolios.
Credit Ratings are notoriously flawed, but yet crucial for bond investors; they are largely back-ward looking and slow to react when bond issuers report new financial data. 
Typically, bond ratings are reviewed only once a year.

Bond prices typically anticipate a change or reflect levels that can be higher or lower compared to its current rating.
This consideration is particularly important for portfolio managers both to identify investment opportunities and also manage risks.
From a machine learning classificaiton problem this translates into identifying False Positive and True Negatives, as well as making sure that accuracy is high within the class.

Machine Learning is a great application for this project as the large data set (cross-section counts several thousands observations) allows to process, analyze and help portfolio managers better classify the credit rating of bonds.
For example, bonds that are mis-classified could present opportunities to buy as the rating does not yet reflect the credit risk or sell the bond if the rating is lower than what it is (implying a higher chance of default).

## DATA
The data is a commercially available data-set which takes bonds within a typical investment universe/benchmark of a portfolio manager.
For this project, the names/issuers and identification codes have been removed.

The data-set is incomplete as it does not include financial statement data. As a result, the independet variables used are back-ward looking performance variables. This can also have a strong economic rationale mirroring the concept of momentum in financial academic literature. 


## MODEL 
Random Forest Classification is the best starting point for this type of classification problem, as it can deal with a mix of type of variables both float and categorical. 
In addition, as it is supervised it allows for a good interpretation for portfolio managers which is crucial in order for them to manage a bond portfolio and for auditing/risk/regulatory purposes.
In turn, the Random Forest Classification has some disadvantages; in particular over-fitting which is very easy if the hyper-parameter tuning is too lax. 
As a result, pre-processing, stratification and hyper-parameter tuning are key factors in building a credible and robust Random Forest Classification model.

## HYPERPARAMETER OPTIMSATION
Hyper-parameter optimization is run based on GridSearch with a focus on tree depth, and sample sizes. 
This should allow to reduce the impact of over-fitting while balancing with the need to have a good model performance.

## RESULTS
The results are encouraging considering the fact that the model only uses market based data (rather than financial data). 
A strong and consistent performance of weighted F1 above 50% is good highlighting the fact that market based features such as yield to worst, OAS spreads and duration 
are a good addition to other financial based variables for classifying credit bond ratings.
