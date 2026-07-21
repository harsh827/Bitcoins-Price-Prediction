\# Bitcoin Price Prediction in Databricks



https://img.shields.io/badge/Python-3.x-blue

https://img.shields.io/badge/Platform-Databricks-red

https://img.shields.io/badge/Model-Linear%20Regression-green

https://img.shields.io/badge/Status-Baseline%20Project-orange



\## Project Overview



This project demonstrates an end-to-end machine learning workflow for predicting the next available daily Bitcoin price using Databricks, Apache Spark, Pandas, and Scikit-learn.



Historical Bitcoin data is loaded from a Databricks table into a Spark DataFrame. The data is cleaned and converted to Pandas for exploratory processing and model development. A Linear Regression model is then trained using the current Bitcoin price and market capitalization as input features.



The project is intended as an educational baseline for understanding:



\- Data ingestion in Databricks

\- Spark and Pandas integration

\- Time-series target preparation

\- Chronological train-test splitting

\- Regression model training

\- Forecast evaluation

\- Comparison with a naïve persistence baseline



> \*\*Important:\*\* This project is for educational purposes only. It is not financial advice and should not be used for investment or trading decisions.



\---



\## Business Problem



Bitcoin prices are highly volatile and influenced by market sentiment, liquidity, macroeconomic events, regulation, and investor behavior.



The objective of this project is to investigate whether the current Bitcoin price and market capitalization can be used to predict the next available daily Bitcoin price.



The prediction problem is defined as:



```text

Input features at time t:

\- Bitcoin price at time t

\- Bitcoin market capitalization at time t



Prediction target:

\- Bitcoin price at the next available observation

