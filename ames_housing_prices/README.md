# Predicting the Sale Price of Houses in Ames
#### by Si Hao Tan

<br/>

# Executive Summary

This project delivers a model that can a) derive house sale price **predictions**, and b) **infer** the strongest features that affect sale price. A regression approach was selected for this business problem. Five regression models were shortlisted and then evaluated for predictive accuracy, interpretability of the model coefficients (inference), and parsimony (number of features required by the model). The final model delivered is a Huber Regressor that achieves strong predictive accuracy, with a cross-validated r2 score of 0.870. The features that most strongly affect sale price can also be inferred from the model parameters. 

# Problem Statement 

We are employees of a real estate agency in Ames, Iowa who have been tasked with doing market research for the company to find out the features of a house that are the strongest predictors of the sale price of the house and the magnitude to which these features affect the sale price of the house. 

The problem covers both prediction and inference - a) derive sale price **predictions** and b) **infer** the strongest features that affect sale price.

This information can help our company’s agents determine a fair price range for each house and identify the strongest features of each house they sell in order to maximize selling price for our customers. 

## Business context

Without time/resources/expertise to understand everything about a house, the buyer is unable to ascertain his own valuation perfectly.

Because a buyer’s resources are limited, our agents assist the price discovery process such that the buyer is able to arrive at a satisfactory valuation. 

If we are able to highlight features that increase the perceived value and “downplay” features that decrease perceived value - then the price discovered by the buyer will be higher than if he had total information about the house (which is impossible in reality).

This means that we are able to extract additional value from the buyer by tilting the price discovery process in our favor. 

## Data Dictionary

Readers may refer to the [data dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt) for data context. 

## Model Results 

The final tuned model is a Huber Regressor. It achieves respectable predictive accuracy, with a cross-validated r2 score of 0.870 and performs well against unseen data with no overfitting.

## Business Recommendations 

- Agents should pay close attention to highlight features that have a strong positive coefficient because these features have a positive impact on sale price. Likewise, features with negative coefficients should be downplayed. Agents may take reference from the [`model_coefficients.csv`](output/model_coefficients.csv) for the full list of features and coefficients. 

- If houses are to be refurbished by the Ames agency prior to market listing, overall quality (material and finish) should be prioritized over overall condition of the house. Overall quality has a stronger impact than condition according to the model. 

- When prospecting for houses to sell, agents should focus on neighborhoods like Northridge or Green Hills. These locations have a positive impact on sale price. More expensive sale prices directly contribute to higher commissions. 

- Before engaging a client, agents are advised to predict the sale price with the model. This allows agents to more objectively understand the [zone of possible agreement](https://www.investopedia.com/terms/z/zoneofpossibleagreement.asp) before negotiations with both buyers and sellers.

## Conclusion

The business problem covers both prediction and inference:

1. Derive sale price **predictions**

2. **Infer** the strongest features that affect sale price.

A regression approach was selected for this business problem. Five different regression models were shortlisted and then evaluated across three criteria specially selected for this business problem: 

1. Predictive accuracy

2. Interpretability of the coefficients

3. Parsimony (number of features required by the model)

Based on all three dimensions, the Huber Regressor offers the best tradeoff in offering high accuracy and interpretability but at the cost of using all the features in the model.

For the first deliverable, the final tuned model achieves respectable predictive accuracy. The cross-validated r2 score is 0.870 and the model performs well against unseen data with no overfitting.

As for the second deliverable, while there are some caveats on the statistical rigor required for inference, the model is still able to generate reasonable feature coefficients for all features. The strongest feature chart and [`model_coefficients.csv`](output/model_coefficients.csv) were created for this purpose.

## Future Steps 

- Further model refinement is possible. Polynomial and interaction features deserve some attention in this dataset. 

- Steps can also be taken to move the model into production. Ideally an app interface can be created for stakeholders so that "predictions on demand" can be retrieved from the model instead of batch-processed. Stakeholders may also wish for business analytics to be displayed via a dashboard. 

- Lastly, the current model does not generalize well to other cities as geographical data like neighborhood categories have significant bearing on predictions as inferred from the model. If equivalent neighborhood data can be obtained for other cities, perhaps this same model (once trained) may have a chance of obtaining accurate predictions for other cities.

## Changelog
- Si Hao Tan, 14 June 2022