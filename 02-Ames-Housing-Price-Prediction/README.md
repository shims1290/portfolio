<img src="http://imgur.com/1ZcRyrc.png" style="float: left; margin: 20px; height: 20px">


# Project 2 - Ames Housing Data and Kaggle Challenge

## Executive Summary

This project seeks to develop a housing sale price prediction model to help home sellers overcome imperfect information in the housing market, so that they can reliably predict housing prices and sell their houses at a fair value. 

Our attempt to develop a model yielded poor predictions on first try. This poor outcome is likely due to the highly restrictive feature selection process from the outset. We did not accomplish the intended goal of achieving predictions with root mean squared error lower than the cost of imperfect information in the housing market (estimated to be ~ \$10,000 per sale). From this, we learn that there is a need to include more features (> 30) to train future models so that it can account for the wide variations sale prices in the unseen data. 

Beyond building a more complex model for housing sale price predictions, data scientist can also replicate the modelling process using housing sales dataset from other regions in the US (outside of Ames, Iowa) in future so that the model can be extended to predict housing prices in other geographical areas. 

## Background

With little understanding of the housing market, home sellers may encounter unfortunate events of mispricing of housing units at their point of sale.

[Levitt and Syverson (2008)](https://ideas.repec.org/a/tpr/restat/v90y2008i4p599-611.html) flagged that **agents were often better informed than the clients who hire them**. Real estate agents may exploit this informational advantage and convince their clients to sell their houses too cheaply. Based on their research while controlling for observables, **they found that homes owned by real estate agents sold for 3.7% more than other houses**. This finding is worrying as it suggests that home sellers are likely to be disadvantaged when making a housing transaction with imperfect information.

> According to the [Federal Reserve Bank of St. Louis](https://fred.stlouisfed.org/series/ASPUS), the average sales price of houses sold for the United States is **\$278,000** in 2010 Q4. 

What this means is that imperfect information could cause home sellers to lose ~ **\$10,000** (i.e. 3.7% * \$278k) in housing value for the average transaction! 

Given there are **4.18 million** homes sold in the United States in 2010 [(source)](https://www.statista.com/statistics/226144/us-existing-home-sales/), the total cost of housing units mispricing (assuming 95% of these homes are not property agent owned) can come up to **\\$39 billion** per annum (i.e. 4.18million * \$10k) ! 

## Problem Statement

We want to help **uninformed home sellers** understand what constitute as fair housing prices by developing a regression model to **predict the sale prices of houses**. Specifically, we use linear models, i.e. ordinary least squares (OLS), Ridge and Lasso regressions. 

A successful housing price prediction model should be able to **predict housing prices with error term or root mean squared error that is ideally lower than $10,000** (i.e. the cost of imperfection information in the housing market).

## Data 

We model and predict housing prices using the following datasets, drawn from housing sales in Ames, Iowa from 2006 to 2010:

* `Train data:` [train.csv](./data/train.csv)
* `Test data:` [test.csv](./data/test.csv)

A data dictionary for the variables included in these datasets can be found [here](https://www.kaggle.com/c/dsi-us-11-project-2-regression-challenge/data). 

## Methodology

This project follows the following workflow:

**1) Feature Selection**
Apart from the housing sale prices, the train and test datasets contain 80 housing-related variables. We exercise judgement to include only select features that will most likely affect housing sale prices within our baseline model. This is to mitigate risks of overfitting and multicollinearity. We use pairplots to provide visualise and assess:

- Whether variable has a linear relationship with target sale prices
- The amount of variations within each variable 
- Possible collinearity and relationship between similar variables

**2) Data Cleaning**
We impute missing values and remove outliers.

**3) Features Engineering**
We dummify categorical variables (using drop_first), assign numerical rank values for ordinal variables, add interaction terms and engineer new features to strengthen the linear relationship of variable(s) with sale prices. 

**4) Model Preparation**
We use the train-test split method to evaluate our model and scale our train (and test) data accordingly using StandardScaler.

**5) Model Selection & Deployment**
The best model among OLS, Ridge and Lasso regressions are selected using r2 scores metrics based on cross validation and initial model fitting between the train and test sets. 

The best model is then fitted and deployed to predict housing sale prices in the test data. 

## Findings and Recommendation

**Key Findings:**

After submitting the predicted housing sale prices to kaggle, we obtained a **very high RMSE score of more than 100,000**. This suggests that our model is **not** generalizable to unseen data. As the RMSE is much higher than \$10,000 (i.e. the estimated cost of imperfect information in the housing market - see background), it is **unlikely that home sellers will benefit from the use of this sale price prediction model**. 

Nevertheless, we learn from this modelling exercise that the quality of the housing aspects are much more important than its corresponding condition. Home sellers hoping to raise the value of their future housing sales should look into improving the overall, external quality of their homes. 

This failure of this data science project could be due to the highly restrictive feature selection process from the outset. As there is a large spread and types of housing units included in the training and test datasets, inclusion of more features ( > 30) will be required to train the model and account for more variations in sale prices of the unseen data. 

**Recommendation:**

We recommend for a ***new*** model to be developed to improve housing sale price prediction with at least 30 housing features incorporated as the existing model is too weak in terms of sale price prediction to be useful for our stakeholders. Perhaps, a better way to approach feature selection in this context is to include all variables from the outset and apply lasso regression to regularize the model. 

**Future Scope:**

Beyond building a more complex model for housing sale price predictions, data scientist can also replicate the modelling process using housing sales dataset from other regions in the US (outside of Ames, Iowa) in future so that the model can be extended to predict housing prices in other geographical areas. 