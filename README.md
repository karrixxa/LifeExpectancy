# Life Expectancy Prediction

This project investigates the health, social, and economic factors that influence life expectancy across countries. Using the WHO Life Expectancy dataset, supplemented with United Nations economic indicators, we built and evaluated regression models to predict life expectancy from global health data.

## Overview

The dataset includes 2,938 observations from 193 countries between 2000 and 2015. It contains variables related to mortality, disease prevalence, immunization rates, healthcare spending, GDP, education, and development status.

Main questions explored:

- What factors most strongly influence life expectancy worldwide?
- How does development status affect average life expectancy?
- Can a reliable regression model predict life expectancy using health, social, and economic indicators?

## Data Cleaning

The dataset contained missing values, skewed variables, and multicollinearity. To prepare the data, we:

- Removed unreliable variables such as `Population`
- Imputed missing values using mean or median depending on outlier patterns
- Checked correlations and VIF values to identify multicollinearity
- Dropped highly correlated predictors such as `infant.deaths`, `under.five.deaths`, `GDP`, and `thinness..1.19.years`
- Standardized numerical predictors
- Applied a Box-Cox transformation to life expectancy to improve model fit

## Models

We compared several regression models:

1. Economic indicators only  
2. Economic + social indicators  
3. Combined economic, social, and health indicators  
4. Polynomial combined model  

The polynomial model had the strongest performance, with an adjusted R² of about 0.837. However, we selected the combined linear model as the final model because it was more interpretable and better aligned with the course focus.

## Final Model

The final model included economic, social, and health-related predictors such as:

- Adult mortality
- HIV/AIDS prevalence
- BMI
- Immunization rates
- Healthcare spending
- Income composition of resources
- Schooling
- Development status

The final combined model achieved:

- Adjusted R²: 0.8057
- RMSE: 277.69 on the Box-Cox transformed scale

This means the model explained about 80.6% of the variation in transformed life expectancy.

## Key Findings

- Education, healthcare spending, immunization rates, and income-related variables were positively associated with life expectancy.
- Adult mortality, HIV/AIDS prevalence, thinness, and developing-country status were negatively associated with life expectancy.
- Adding health indicators greatly improved model performance compared to using only economic or social variables.
- The model predicted average trends well, but diagnostic tests showed some violations of normality and constant variance.

## Limitations

Although the final model performed well, it had some limitations:

- Residuals showed mild non-normality and heteroscedasticity.
- Some variables were imputed, which may affect model reliability.
- Life expectancy is complex and may not be fully captured by a linear model.
- Predictions at very low or very high life expectancy values were less reliable.

## Future Improvements

Future work could include:

- K-fold cross-validation
- Interaction terms
- More flexible transformations
- Regularization methods
- Clustering countries by region, income level, or development status
- Adding external data such as environmental quality, healthcare access, or nutrition indicators

## Tools

- R
- tidyverse
- ggplot2
- ggcorrplot
- car
- leaps
- glmnet
- Linear regression
- Box-Cox transformation
- VIF analysis
- Model diagnostics

## Contributors

- Pinar Targil
- Meaghan Ramlakhan
- Charis Xiong

## Acknowledgments

This project was completed for STAT 410: Linear Regression at Rice University.
