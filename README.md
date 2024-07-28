# Analyzing Model Performance in Online Sales from India: A Case Study on Amazon's 2022 Sales Report
This paper focuses on identifying the most effective modeling techniques for analyzing e-commerce data. We initially compared four models—Multiple Linear Regression, Logistic Regression, Random Forest, and Decision Tree—to determine which would best fit the dataset. Details about the variables used in these models are outlined in the capstone two ((https://github.com/jadspringgit23/FinalProject_Report.git). Since the results did not provide conclusive evidence favoring one model over the others, there is potential for improvement in future analyses of similar datasets. Given that the data is time-stamped, time series analysis will be employed to explore how the selected variables are correlated over time. Consequently, this study will utilize the ARIMA model to analyze the variable "Sales," derived from "Qty" and "Amount," with respect to the date. Such a variable that was exclude while conducting the test for the previous four models.

# Data Preparation for the Time Series Analysis
This study focuses exclusively on data manipulation techniques relevant to time series analysis. The data manipulation methods from capstone two are not covered here, as they are detailed in that earlier work. To reiterate, this time series analysis uses the same dataset as capstone two, with the addition of the "Date" variable, which has been converted to the "datetime" format, and the newly created "Sales" variable, derived from "Qty" and "Amount.

# Executive Summary
This project builds upon Capstone Two, with the primary goal of assessing the dataset using time series analysis. While the data source, total observations, and variables remain the same, there are notable updates: the inclusion of the “Date” variable, which was omitted in the previous study, and the introduction of a new variable, “Sales,” derived from “Qty” and “Amount.” It is important to note that the results from the previous study will not be the focus of this analysis; they are only used to compare improvements against the current time series model. The last transformed dataset from the previous study was utilized to incorporate the “Date” and “Sales” variables. We began with exploratory data analysis (EDA) on both the original and transformed datasets. Following this, we performed data transformation and visualization to identify the optimal parameters (p, d, and q) for the ARIMA model, using AIC as the error criterion. These parameters were determined using the Auto-ARIMA model. The dataset, sourced from Kaggle and titled 'Amazon Sales Report,' pertains to online sales from India. The primary objective of this study is to perform time series analysis using ARIMA with the “Sales” variable, applying the best parameters [5,1,0] provided by the Auto-ARIMA model.

# Introduction
The dataset used in this study covers online sales from April to July. Although it is labeled as the Amazon online selling report for 2022, the limited timeframe of the data appears disproportionate relative to India’s large population. This discrepancy raises questions about potential factors such as limited internet availability, competition from other online retailers, or the nascent stage of e-commerce in India. Despite these challenges, internet penetration in India has been increasing since 2022, with usage exceeding 60%. Given India's population of over 1.4 billion, the market shows significant promise for online sales. Although India’s internet penetration is lower compared to developed nations, its growing online user base, projected to expand further by 2024, highlights its potential as a lucrative market. Therefore, this study aims to analyze the "Sales" data using an ARIMA model to forecast sales trends. The objective is to evaluate sales patterns with the optimal parameters [5,1,0] to inform decision-making for product development and market strategy.

# Data Collection, Preparation, and Visualization

## Data Colection
The data utilized in this study were sourced from Kaggle and are described as follows: 3 categorical variables listed in figure1,  4 numerical variables, and  3 float variables. 
![image](https://github.com/user-attachments/assets/8fbf8c6b-0530-437c-9d1c-3ec5625b3fcf)

## Data Preparation
This study focuses exclusively on data manipulation techniques relevant to time series analysis. The data manipulation methods from the previous capstone are not covered here, as they are detailed in that earlier work. To clarify, this time series analysis uses the same dataset as the previous capstone, with the addition of the "Date" variable, converted to the "datetime" format, and the newly created "Sales" variable, derived from "Qty" and "Amount." In other words, the dataset for this analysis is the final version from the previous study, enhanced with the "Date" and "Sales" variables. It is important to note that, unlike previous models, dummy variables have been applied to the three categorical variables to make the dataset more suitable for regression analysis, although regression is not the focus of this study. Following data transformation and parameter selection using Auto-ARIMA, the best ARIMA model identified had the parameters [5,1,0] for p, d, and q, respectively.

## Data Visualization
![image](https://github.com/user-attachments/assets/f8178146-9a58-44de-8e16-7eebf35891e9)
![image](https://github.com/user-attachments/assets/c072f099-b7bb-4f42-b756-bb2bdd1fde50)
![image](https://github.com/user-attachments/assets/a1aaca89-5734-4da9-ad87-36cc64028f20)
![image](https://github.com/user-attachments/assets/a1d7829d-9d55-40d3-a64e-3aef766ae148)

# Methodology
To conduct the analysis, we began with data visualization to select the values for p, d, and q, using lag plots. These plots revealed that the correlation could be either positive or negative, leading us to perform an autocorrelation test. This test confirmed that the overall data trend is negatively correlated. Since our goal was to analyze the Sales trend over time, we proceeded with the ACF (Autocorrelation Function) and PACF (Partial Autocorrelation Function) tests for the "Sales" variable. The ACF plot confirmed a negative correlation trend for "Sales," indicating that the data is not suitable for direct autoregression without transformation. The PACF showed considerable changes in autocorrelation, with a notable dominance of positive data points in the first differencing. To determine the best order for the ARIMA model, we used the ADF (Augmented Dickey-Fuller) test to evaluate the p-values. However, the p-values did not reveal a significant difference between the differentiations, providing insufficient evidence to determine the optimal values for p, d, and q. As a result, we employed Auto-ARIMA to find the optimal parameters using the Akaike Information Criterion (AIC) as the error metric. Based on the Auto-ARIMA results, our final ARIMA model was defined as ARIMA(p=5, d=1, q=0), as shown in the screenshot below:
![image](https://github.com/user-attachments/assets/6a318fa3-e7ba-4b78-9b0f-8990444013e6)

Additionally, to perform the analysis, we first applied the decomposition method using an additive model to visualize the trend, seasonality, and residuals of the data. We then transformed the data to achieve stationarity. For model evaluation, we split the dataset into 70% training data and 30% test data. Then forecasting for April 23rd, and the entire month of June. 

# Modeling
The modeling involved applying the ARIMA model to the dependent variable "Sales" using the parameters [5,1,0], as determined by the Auto-ARIMA test. Mathematically, the model is described as follows:
arima_model=sm.tsa. ARIMA(data12['Sales'], order = (5,1,0))
model55 = arima_model44.fit()

# Evaluation and Conclusion
By evaluating the model using a 70% training set and a 30% test set, the results were consistent with those provided by the ARIMA model, as both followed the same trend. For example, the autoregressive terms in both models had p-values below the significance level of 0.01. This indicates that the autoregressive coefficients are statistically significant in both models, justifying their inclusion.
In all, the time series analysis provided valuable insights into online selling in India, revealing that sales are concentrated during specific periods. While the previous four models (from Capstone 2) did not conclusively favor one over another, the time series analysis highlighted limitations affecting forecasting performance.








