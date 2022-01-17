# 🏠 NoVA-Housing-Prices
```
Predicting housing prices for homes in Northern Virginia area using data scaped from Zillow.com listings
```
## 🔍 Background
Currently in the market for my first home, I decided I needed to do my research on the Northern Virginia (NoVA) housing market to supplement the info I've been gathering on my in-person search.

But beyond performing Exploratory Data Analysis on the prices and attributes of homes in 16 different suburbs of NoVA, I wanted to create a model to predict housing prices--namely through the use of various regression models.

## 🔢 Data
The 143 properties' data was scraped from Zillow using [webscraper.io](https://webscraper.io/), which allowed me to easily use a point-and-click interface to gather various facts from each listing.

If you want to use the tool yourself to scrape Zillow or data from any other website, refer to the guide I used found [here](https://medium.com/fortune-for-future/how-to-scrape-zillow-data-for-free-without-writing-any-code-be2ac698e604).

The results of my scraping can be found in the `housing_data` folder as .csv files for each suburb. The combining of the individual suburbs' data occurs in the following script.

## ➡ Getting Started
Start by setting up the appropriate environment to run a Jupyter Notebook file to ensure you have the proper versions of the required libraries. Once that is done, you can download the data and .ipynb file and hit "Run All" on the notebook.

## 🗺 Exploratory Data Analysis
Using Seaborne, HVplot and Matplotlib, I created visualizations to better understand the distribution of prices, as well as price's relationship with other important variables scraped from the listings.

The following show the statistics and distribution of home prices (after data cleaning was performed):

![](housing_charts/price_description.jpg)

![](housing_charts/price_histogram.jpg)

The relationship between price and other variables in the data is best shown using a correlation heatmap and a pairplot:

![](housing_charts/heatmap.jpg)

![](housing_charts/pairplot.jpg)

## 📈 Predicting House Prices using Regression Models
Regression analysis was chosen as the best type of model because we are predicting the continuous dependent variable of house prices from a number of independent variables.

In preparing the data for regression models, I had to ensure 1) DV is measured on a continuous level 2) Linearity between the DV and each IV 3) No multicollinearity 4) Normal distribution of residual errors 5) Homoscedasticity and 6) Independence of errors.

After applying the appropriate transformations to variables to ensure linearity between DV and each IV, verifying variance inflation factors (VIF) of coefficients were less than 5 each to ensure no multicollinearity, checking a Q-Q plot of the model's residuals to ensure normality, using a robust regression technique to account for heteroscedasticity, and checking that the Durbin-Watson value is around 2 to check for independence of errors, all assumptions were taken care of.

After splitting the data between training and test sets, the former was trained on 6 different types of regression models: Linear, Random Sample Consensus (RANSAC), Ridge, Lasso, Elastic Net and Polynomial. Linear regression was the baseline model upon which the other types were built, and the linear regression equation's intercept and coefficients are as follows:

![](housing_charts/linreg_coefficients.jpg)

Evaluation of the 6 models is shown below:
![](housing_charts/model_evaluation.jpg)

Focusing on RMSE as the error metric to evaluate the 6 models, we see Polynomial Regression, followed by Elastic Net, performed the best:
![](housing_charts/RMSE_scores.jpg)

Using R^2 as a goodness of fit measure, Polynomial Regression and Elastic Net, respectively, were also the best performing models:
![](housing_charts/R2_square.jpg)

The equation for the Polynomial Regression model, which has a degree of 2, has the following intercept ('const') coefficients for each feature combination (e.g. 'Sqft No_ba' is the variable 'Sqft' times 'No_ba'):
![](housing_charts/polyreg_coefficients.jpg)

The equation for the Elastic Net Regression model has the following intercept and coefficients:

![](housing_charts/elasticnet_coefficients.jpg)
