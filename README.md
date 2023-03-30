# Predicting Food Prices in Developing Countries

## Overview
In this project, I took historical food price data from developing countries and used **time series analysis** in order to predict what the prices would be up to two years in the future. Throughout the project I dealt with strong **seasonality** in the dataset, explored both **regression** and **ARIMA** based models, and incorporated **climate data** in order to improve my results. My final model was able to achieve mean absolute percentage error scores of around 12 % on the test set, and was robust when cross-validated, but had difficulty predicting for extreme events.

## Buisness Case
Food insecurity is a massive global issue that affects over [345 million people worldwide in 2023](https://www.wfp.org/global-hunger-crisis), with more than 900,000 of those suffering in famine-like conditions. These problems can be especially acute in sub-saharan africa and the middle-east, where conflict disrupts the local food supply and climate change makes previously productive land more marginal. The ability to predict the local price of food months or years in advance would be of great value to international aid groups trying to alleviate this issue, and would allow them to better allocate resources to where they are needed most.

## Data Sources
https://www.kaggle.com/datasets/lasaljaywardena/global-food-prices-dataset

https://ceda-wps-ui.ceda.ac.uk/

## Data Wrangling
[This notebook](Notebooks/Data_Wrangling.ipynb) involved loading in the general food price data, which was in a very condensed format where each row was a combination of country, state, market, name of the good, its price, and the date, which was converted to datetime format. In order to focus the analysis and get a single time series to work with I chose Niger as a specific country to focus on. Niger had the longest time series in the dataset, and included goods that were found in several other countries such as milllet. I wanted to compare the price of a good across several different countries, but the prices for each were listed in the local currency, making direct comparison impossible. Instead, I **averaged the percent change in price** for that good across that timeframe, and saved that as a seperate dataframe. 

![](Images/percent_change_millet.png)

## Exploratory Data Analysis
In the first part of [this notebook](Notebooks/EDA.ipynb) I selected all of the data from Niger then "unpivoted" the goods data from into seperate columns and averaged the prices across all of the markets, creating a dataframe where each row was one unique date and each good had its own column. These goods were then graphed to see overall trends and determine what good should be studied.

![](Images/Niger_food_prices.png)

Due to its completeness (and because several other countries had millet data) millet prices were chosen as the target feature, and any NaN values were **interpolated** in order to make the dataset complete. Additionally, the **seasonal decomposition**, **autocorrelation**, and **partial autocorrelation** were plotted for the millet price data in order to see the components that made up the time series, and get an idea of how an ARIMA model might be made from the data.

![](Images/Seasonal_decomp.png)

## Preprocessing and Training

## Final Modeling

## Conclusion and Next Steps