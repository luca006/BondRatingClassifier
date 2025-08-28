# Model Card

See the [example Google model cards](https://modelcards.withgoogle.com/model-reports) for inspiration. 

## Model Description

**Input:** Describe the inputs of your model 

**Output:** Describe the output(s) of your model

**Model Architecture:** Describe the model architecture you’ve used

## Performance

Give a summary graph or metrics of how the model performs. Remember to include how you are measuring the performance and what data you analysed it on. 

## Limitations

The model and data have several limitations. The first main limitation is that the independent variables are only those related to historical past performance such as yields, spreads and excess return performance over select periods of time (1-day, 1-week, Month to Date, Year to Date...) etc... As a result, it closely mirrors a "momentum" type of application. 

An additional limitation is the distribution of credit ratings which is very skewed towards BBB1/BBB2/BBB3, with AAAs and AAs being the least represented (also BBs). In addition, over time this distribution can change with market conditions which in turn makes a single cross-section limited in its results.

Finally, many of the independent variables are likely correlated with one-another which in turn can reduce the interpretation and feature importance of the model.

## Trade-offs

The trade-off is that this approach is very quick and very reactive to reflect and classify bond's credit risk charateristics with that of the credit rating.

