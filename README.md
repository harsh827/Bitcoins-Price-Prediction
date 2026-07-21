# Bitcoin Price Prediction in Databricks

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Databricks](https://img.shields.io/badge/Platform-Databricks-FF3621?logo=databricks&logoColor=white)](https://www.databricks.com/)
[![Model](https://img.shields.io/badge/Model-Linear%20Regression-2E8B57)](#model-training)



## Project Overview

This project demonstrates an end-to-end machine learning workflow for predicting the next available daily Bitcoin price using Databricks, Apache Spark, Pandas, and Scikit-learn.

Historical Bitcoin data is loaded from a managed Databricks table into a Spark DataFrame. The dataset is validated, converted to Pandas, prepared chronologically, and used to train a Linear Regression model. The model uses the current Bitcoin price and market capitalization to predict the price at the next available observation.

The project is designed as an educational baseline for learning:

- Data ingestion with Databricks and Apache Spark
- Spark-to-Pandas conversion
- Time-series data preparation
- Chronological train-test splitting
- Linear Regression modeling
- Correct forecast evaluation
- Comparison with a naive persistence baseline


---

## Business Objective

Bitcoin is a highly volatile financial asset affected by market sentiment, liquidity, regulation, macroeconomic conditions, and other external events.

The objective of this project is to examine whether the current Bitcoin price and market capitalization can predict the Bitcoin price at the next available daily observation.

The prediction problem is defined as:

```text
Input features at time t:
- Bitcoin price at time t
- Bitcoin market capitalization at time t

Target:
- Bitcoin price at the next available observation
```

---

## Dataset

The project uses the `btc-usd-ytd.csv` dataset containing historical Bitcoin market information.

### Dataset columns

| Column | Description |
|---|---|
| `snapped_at` | UTC timestamp of the observation |
| `price` | Bitcoin price in USD |
| `market_cap` | Bitcoin market capitalization in USD |
| `total_volume` | Reported Bitcoin trading volume in USD |

### Dataset summary

- **Number of records:** 4,805
- **Number of columns:** 4
- **Date range:** 28 April 2013 to 25 June 2026
- **Frequency:** Approximately daily
- **Invalid timestamps:** 0
- **Explicit null values:** 0
- **Duplicate timestamps:** 0
- **Missing calendar dates:** 2
- **Zero-volume records:** 242



## Technology Stack

- **Databricks** for notebook execution and data processing
- **Apache Spark** for loading the managed table
- **Python** for the machine learning workflow
- **Pandas** for local data preparation
- **NumPy** for numerical operations
- **Scikit-learn** for modeling and evaluation
- **Git and GitHub** for version control and project publishing

---

## Repository Structure

```text
bitcoin-price-prediction-databricks/
|
|-- README.md
|-- LICENSE
|-- .gitignore
|-- requirements.txt
|
|-- data/
|   |-- README.md
|   `-- btc-usd-ytd.csv
|
|-- notebooks/
|   |-- bitcoin_price_prediction.ipynb
|   `-- bitcoin_price_prediction.py
|
|-- docs/
|   `-- project_notes.docx
|
|-- images/
|   |-- data-preview.png
|   |-- prepared-data.png
|   |-- model-training.png
|   `-- prediction-results.png
|
`-- results/
    |-- model_metrics.csv
    `-- predictions.csv
```


## Project Workflow

```text
Databricks managed table
        |
        v
Spark DataFrame
        |
        v
Data validation
        |
        v
Conversion to Pandas
        |
        v
Chronological sorting
        |
        v
Target creation
        |
        v
Chronological train-test split
        |
        v
Linear Regression training
        |
        v
Prediction and evaluation
        |
        v
Comparison with naive persistence baseline
```

---

## Data Preparation

Correct preparation is essential because this is a time-series problem. The records must be sorted before the future target is created.

### Preparation steps

1. Load the managed Databricks table into a Spark DataFrame.
2. Inspect the schema, record count, null values, duplicate timestamps, and date range.
3. Convert the Spark DataFrame to Pandas. This is acceptable for this project because the dataset contains only 4,805 rows.
4. Convert `snapped_at` to a normalized UTC datetime column.
5. Sort the records chronologically.
6. Remove duplicate dates if any are detected.
7. Calculate the next observation date and the gap in days.
8. Create the prediction target from the next price.
9. Optionally retain only records where the following observation is exactly one calendar day later.
10. Remove the final record because it has no future target.


## License

This project may be distributed under the MIT License, subject to the licensing and redistribution terms of the original dataset.
