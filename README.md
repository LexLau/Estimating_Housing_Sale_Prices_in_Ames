# Project 2 - Ames Housing Data and Kaggle Challenge

### By Alex Lau

- [Problem Statement](#Problem-Statement)
- [Project Files](#Project-Files)
- [Executive Summary](#Executive-Summary)
- [Data Dictionary](#Data_Dictionary)
- [Conclusion/Recommendations](#Conclusion/Recommendations)


## Problem Statement

Each year hundreds of households in Ames, Iowa purchase and sell homes that range in price from as low as 13,000 USD to over 600,000 USD. With so many variations depending on vast amounts of features, how can people ensure their homes are appropriately priced? We will build a model to predict housing prices using a variety of regressions to analyze 78 features for over 2,000 homes sold between 2006 and 2010. Our goal is to identify key housing features that would influence the sale price by striving for a 90% prediction accuracy rate. We will also determine the best type of regression. This tool will help buyers and sellers come to a fair price.

---

## Project Files

Below are supporting files for our project:

- [Ames Housing Data Slides](./Aimes_Housing_Sales_Prices.pptx)
- [Ames Housing Data Notebook](./Ames_Housing_Data_Alex_Lau.ipynb)
- [Train Data Set](./datasets/train.csv)
- [Test Data Set](./datasets/train.csv)


---

## Executive Summary

Our approach was to first decide where to pull the datasets from. We have partnered with the city of Ames to analyze homes sold between 2006 to 2010. Although these are logged with the city, our vast experience reveals there are almost always outliers to address. Through Exploratory data analysis, we identified several outliers that were exteremely low in price comparied to homes with similar features. These were excluded from our model to maintain integrity. 

We incorporated Pandas, Sklearn, and Statsmodels to derive at the correlations, P-values, and coefficients for each feature in relation to the sale price. From our analysis, we have identified that housing prices are positively skewed, with a mean of 181,000 USD but a median of 162,500 USD. This means in order to have a more normal distribution, we could log the values to reduce heteroscedasticity that exists toward the higher selling homes. 

We also encountered some missing values that needed to be dealt with. We decided to replace missing values with the medians for ordinal and continuous features. We also encountered ordinal string data which we converted to numbers, and categorical data which we've re-created as distinct features. Ultimately this allows us to build a dataset that is more suitable for a machine, with number values only. 

We will 4 types of regressions: linear, ridge, LASSO, and elastic net. We will idenfity R-squared scores, and Root Mean Squared errors to identify the best model with lowest variances. 

---

## Conclusion/Recommendations

We have identified correlation values associated to each of the 78 features we analysed and have narrowed down to 5 that sellers should focus on achieve the highest sale prices: Overall Quality, Living Square Footage, Exterior Quality, Kitchen Quality, and Total Basement Square Footage. Improving or reducing the value of these features will directly affect the sales prices of homes. 

Linear model performed the worst in our tests. It obtained an R-squared of -15.92% and a root mean squared error of 74,074 USD. 
Ridge model did much better with an R-squared of 91.46% and a rood mean squared error of 21,281 USD.
LASSO model achieved an R-squared of 92.36% and a root mean squared error of 20,088 USD. 
Elastic net model outperformed the rest with an R-squared of 92.41% and a root mean squared error of 20,079 USD. 

After running simulations through Linear, Ridge, LASSO, and Elastic Net Regression, we have found Elastic Net Regression to be the most flexible. When we provide too much data, linear regression creates an overfit model that does well in training, but poorly on testing. Ridge regression keeps all features in the model, even if there is a poor correlation, but idenfities when to assign a low coefficient. LASSO regression, on the other hand, drops features it deems not helpful. Elastic Net Regression allows us to identify the optimal proportion of Ridge vs LASSO regression the best of both worlds. Unforunately, there will always be outliers that negatively affect our model, along with variances that cannot be explained by the data within our model, but the goal is build one that can generalize well. We have successully accurately predicted over 90% of the sales prices with our model.


---
## Data Dictionary
- [Ames Data Dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)
---
## Source Documentation and Data Dictionary

- [City of Ames Site](http://www.cityofames.org/assessor/)

Individual homes within the data set can be referenced directly from the Ames City Assessor webpage. Click on “property search” and enter the Parcel ID (PID) found in the data set to find more information on that property. Note these are nominal values (non-numeric) so preceding 0’s must be included in the data entry field on the website. A city map showing the location of all the neighborhoods is also available on the Ames site and can be accessed by clicking on “Maps”  and then “Residential Assessment Neighborhoods (City of Ames Only)”.

- [Beacon Site](http://beacon.schneidercorp.com/Default.aspx)

An alternative method of accessing this database is through the Beacon website and inputting Iowa and Ames in the appropriate fields.

