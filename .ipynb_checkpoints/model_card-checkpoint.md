
## Model Description

**Input:** 
The inputs are solely bond specific and using past performance values which reflects a "momentum" approach to the classification problem.
Additional data that is missing is financial statement data by bond which would likely be very important as input variables.

The input of the model are a mix of nominal and quantiative data:
1) Nominal includes:
   Sectors, countries, currencies
2) Quantitative includes:
   Bond yields, spreas, duration and multiple performance metrics

Computed values:
OAS BE: OAS/Spread Duration
Yield BE: Yld to Worst/Mod Dur to Worst

**Output:**
The output variable labels have been shorten in order to make the code easier to handle and read.
Output variable initial lable is 'Rating_Score_Rating - Middle of Three' and re-labelled as 'Rating_Score_Rating'
This is the result of the ordinal re-classification from 'Rating - Middle of Three' to 'Rating'.
The output variable is Rating_Score_Rating - Middle of Three
This reflects a ordinal re-classification of Rating - Middle of Three
such that:

AAA:0
AA1:1
AA2:2
...
BBB1:7
BBB2:8
BBB3:9
BB1:10

**Model Architecture:** 
The Model Architecture reflects a standard approach to apply Random Forest Classification model to a classification problem.
1) Pre-process the data
2) Assess the Category distributions --> decide to keep a stratification approach due to a highly unbalanced rating distribution
3) Use a traditional train-test with a 5-fold cross validation while keeping stratification sampling. This is crucial to reduce the effects of over-fitting.
4) Run a grid search to improve and find the right hyper-parameter tuning to avoid overfitting
5) Present Performance results

In particular:
For the Random Forest Classification model:
1) Train and Test 80/20
2) Cross validation keeping equal distriubtions k=5 fold
3) Limit Tree Depth
4) Increase sample per leaf and for each split (to avoid overfitting)
5) 

## Performance
The performance of the model reflects above average classification of bond ratings and the result is somewhat expected given the limitations of the information of the features. In some sense, the importance of variables such as OAS_BE (OAS Breakeven), OAS, Yld to Maturity and Yld to Worst are unsurprising and have a strong economic rationale. In turn, the model explain more than 50% of the classification which is already an important step and indicator for portfolio managers considering that Credit Rating Agencies do not use the features for their credit rating assessment.

Given the unbalanced nature of the rating distribution and the focus for portfolio managers to be able to assess both False Positives and True Negatives, the model focuses mainly on 'F1 weighted' metric which accounts for both of these type of errors. 

Overall, the Grid Search finds the following model to be best:
Max Depth of :         15
Max Features :        'sqrt'
Min. samples per leaf: 5
Min. samples per split: 5
Nr Estimators:          200

This is a good balance of pruning vs. over-fitting.

In summary, the model performs well on an F1-weighted score:

Classification Report:

              precision    recall  f1-score   support

           0       0.71      0.56      0.62        18
           1       0.75      0.21      0.33        14
           2       0.42      0.24      0.31        33
           3       0.60      0.34      0.44        76
           4       0.53      0.39      0.45       117
           5       0.51      0.41      0.46       176
           6       0.50      0.59      0.54       251
           7       0.50      0.35      0.41       295
           8       0.52      0.79      0.62       378
           9       0.71      0.61      0.66       166
          10       0.00      0.00      0.00         1

    accuracy                           0.53      1525
   macro avg       0.52      0.41      0.44      1525
weighted avg       0.54      0.53      0.52      1525

Confusion Matrix:

[[ 10   1   3   1   3   0   0   0   0   0   0]
 [  1   3   1   2   3   2   2   0   0   0   0]
 [  1   0   8   6   2   7   8   1   0   0   0]
 [  1   0   6  26  12  13  13   2   3   0   0]
 [  1   0   0   5  46  31  19   5  10   0   0]
 [  0   0   0   1  16  73  53  21  11   1   0]
 [  0   0   1   2   5  10 147  27  57   2   0]
 [  0   0   0   0   0   8  43 102 135   7   0]
 [  0   0   0   0   0   0   7  44 297  30   0]
 [  0   0   0   0   0   0   0   3  61 102   0]
 [  0   0   0   0   0   0   0   0   0   1   0]]

The results are supported by stable and similar cross-validation scores
Mean CV accuracy: 0.501

## Limitations
The model and data have several limitations. The first main limitation is that the independent variables are only those related to historical past performance such as yields, spreads and excess return performance over select periods of time (1-day, 1-week, Month to Date, Year to Date...) etc... As a result, it closely mirrors a "momentum" type of application. 

An additional limitation is the distribution of credit ratings which is very skewed towards BBB1/BBB2/BBB3, with AAAs and AAs being the least represented (also BBs). In addition, over time this distribution can change with market conditions which in turn makes a single cross-section limited in its results.

Finally, many of the independent variables are likely correlated with one-another which in turn can reduce the interpretation and feature importance of the model.

## Trade-offs
The trade-off is that this approach is very quick and very reactive to reflect and classify bond's credit risk charateristics (performance, spreads, duration...) with that of the credit rating.
The economic interpretation of the importance of variables is very strong, but it lacks the financial fundamental data which would and should (hopefully) provide more economic importance and performance to the model.
