# Streaming Data Management and Time Series Analysis

## Time Series Forecasting of Hourly Pedestrian Counts

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Statsmodels](https://img.shields.io/badge/Statsmodels-Time%20Series-orange)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine%20Learning-green)
![License](https://img.shields.io/badge/License-Academic-lightgrey)

---

# Project Overview

The objective is to forecast future **hourly pedestrian counts** from historical observations using statistical and machine learning techniques. Three different forecasting models are implemented and compared:

- Seasonal ARIMA (SARIMA)
- Unobserved Components Model (UCM)
- Gradient Boosting Regression

The project demonstrates a complete forecasting workflow, including data preprocessing, exploratory data analysis, feature engineering, model development, forecasting, residual diagnostics, and submission generation.

---

# Objectives

The main objectives of this project are to:

- Analyze historical pedestrian count data.
- Explore temporal patterns and seasonality.
- Develop statistical forecasting models.
- Develop a machine learning forecasting model.
- Compare different forecasting approaches.
- Generate future predictions for the required forecasting horizon.

---

# Dataset

The dataset contains hourly pedestrian counts with timestamps.

Main variables include:

- **time** – Timestamp of each observation.
- **value** – Hourly pedestrian count.

The timestamp column is converted to a datetime format and sorted chronologically before analysis.

---

# Project Workflow

## 1. Data Loading and Preprocessing

The project begins by:

- Loading the dataset using Pandas.
- Converting timestamps into datetime format.
- Sorting observations chronologically.
- Separating historical observations from the forecasting horizon.

---

## 2. Exploratory Data Analysis

Several exploratory analyses are performed to understand the data, including:

- Time series visualization
- Hourly pedestrian count trends
- Average daily patterns
- Average weekly patterns

These analyses help identify temporal trends and recurring seasonal behavior.

---

## 3. Data Transformation

To stabilize variance and improve model performance, the pedestrian counts are transformed using the logarithmic transformation:

\[
\log(1+x)
\]

The inverse transformation is applied after forecasting to obtain predictions on the original scale.

---

# Forecasting Models

## Model 1 – Seasonal ARIMA (SARIMA)

A Seasonal ARIMA model is implemented to capture both short-term dependencies and daily seasonality.

### Configuration

- ARIMA(1,0,1)
- Seasonal Order:
  - (1,1,1,24)

The model is evaluated using:

- Akaike Information Criterion (AIC)
- Residual diagnostics
- Ljung–Box test

Future forecasts are generated and transformed back to the original scale.

---

## Model 2 – Unobserved Components Model (UCM)

The second forecasting approach uses a state-space model with:

- Local linear trend
- Daily seasonal component
- Weekly seasonal component

The model captures long-term trends while accounting for multiple seasonal patterns.

Forecasts are generated and transformed back to the original data scale.

---

## Model 3 – Machine Learning Forecasting

A Gradient Boosting Regression model is developed using engineered temporal features.

### Feature Engineering

Calendar Features

- Hour of day
- Day of week
- Month
- Day of year

Cyclical Features

- Hour (sine/cosine)
- Day of week (sine/cosine)

Lag Features

- Previous hour
- Previous day (24-hour lag)
- Previous week (168-hour lag)

Rolling Statistics

- 24-hour rolling mean
- Weekly rolling mean

The model is trained using a chronological train-validation split to preserve temporal order.

---

## Recursive Forecasting

Future observations are generated recursively.

Each newly predicted value is fed back into the feature engineering process to forecast the next time step until the entire forecasting horizon is completed.

---

# Model Evaluation

The project evaluates forecasting performance using:

- Akaike Information Criterion (AIC)
- Residual analysis
- Ljung–Box test
- Forecast comparison

Residual diagnostics are used to verify whether model residuals behave similarly to white noise.

---

# Output

The final predictions are exported as a submission file containing:

- Time
- ARIMA Forecast
- UCM Forecast
- Machine Learning Forecast

The project automatically saves the results as CSV for submission.

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Statsmodels
- Scikit-learn
- Jupyter Notebook

---

# Skills Demonstrated

- Time Series Forecasting
- Seasonal ARIMA
- State Space Models
- Unobserved Components Models
- Machine Learning Regression
- Feature Engineering
- Lag Feature Construction
- Recursive Forecasting
- Residual Diagnostics
- Statistical Model Evaluation

---

# How to Run

1. Clone the repository.

```bash
git clone https://github.com/yourusername/Streaming-Data-Management-and-Time-Series-Analysis.git
```

2. Install the required libraries.

```bash
pip install pandas numpy matplotlib statsmodels scikit-learn
```

3. Open the notebook.

```
streaming data management and time series analysis.ipynb
```

4. Update the dataset path if necessary.

5. Run all notebook cells sequentially.

---

# Future Improvements

Possible extensions include:

- Prophet forecasting
- LSTM and GRU neural networks
- XGBoost forecasting
- Hyperparameter optimization
- Cross-validation for time series
- Ensemble forecasting

---

# License

This repository is intended for academic and educational purposes.
