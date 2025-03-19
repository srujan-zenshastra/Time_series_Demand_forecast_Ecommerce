# Demand Forecasting for E-Commerce

## Project Overview
This project focuses on time series forecasting to predict daily sales for an e-commerce dataset, specifically targeting Store 1, Item 1 from the [Store Item Demand Forecasting Challenge](https://www.kaggle.com/competitions/demand-forecasting-kernels-only) on Kaggle. The goal is to compare the performance of various forecasting models, including statistical methods (ARIMA, SARIMA, ARIMAX, SARIMAX), machine learning techniques (Linear Regression, Logistic Regression, XGBoost), and an ensemble approach. The project includes exploratory data analysis (EDA), feature engineering, model training, evaluation, and visualization of predictions against actual sales.

## Dataset
- **Source**: [Store Item Demand Forecasting Challenge](https://www.kaggle.com/competitions/demand-forecasting-kernels-only)
- **Description**: The dataset contains 5 years of daily sales data for 50 items across 10 stores. This project focuses on Store 1, Item 1 for simplicity.
- **Columns**:
  - `date`: Date of the sale (parsed as datetime).
  - `store`: Store ID (filtered to 1).
  - `item`: Item ID (filtered to 1).
  - `sales`: Number of units sold (target variable).

## Features
- **EDA**: Visualizations include time series plots, seasonal decomposition, autocorrelation, sales distribution, and monthly trends.
- **Feature Engineering**:
  - `day_of_week`: Day of the week (0-6, Monday-Sunday).
  - `month`: Month of the year (1-12).
  - `lag_7`: Sales lagged by 7 days.
  - `rolling_mean_7`: 7-day rolling mean of sales.
  - `is_holiday`: Binary flag for synthetic holidays (Christmas: Dec 25, 2015-2017).
- **Models**:
  - **ARIMA**: Autoregressive Integrated Moving Average with grid search for optimal `(p, d, q)`.
  - **SARIMA**: Seasonal ARIMA with grid search for `(p, d, q)(P, D, Q, 7)`.
  - **ARIMAX**: ARIMA with exogenous variables.
  - **SARIMAX**: Seasonal ARIMA with exogenous variables.
  - **Linear Regression**: Baseline regression model.
  - **Logistic Regression**: Binary classification (sales above/below median).
  - **XGBoost**: Gradient boosting regressor.
  - **Ensemble**: Average of SARIMAX and XGBoost predictions.
- **Evaluation**: Root Mean Squared Error (RMSE) for regression models; accuracy for Logistic Regression.
- **Visualizations**: Individual plots of each model’s predictions vs. actual sales, combined forecast comparison, and RMSE bar plot.

## Requirements
- **Python**: 3.10+
- **Libraries**:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`
  - `statsmodels`
  - `sklearn`
  - `xgboost`
  - `itertools` (standard library)

These are pre-installed in Kaggle’s notebook environment.

## Setup Instructions
1. **Kaggle Account**: Sign up/log in to Kaggle.
2. **Join Competition**: Go to the [Store Item Demand Forecasting Challenge](https://www.kaggle.com/competitions/demand-forecasting-kernels-only) and click "Join Competition" to access the dataset.
3. **Create Notebook**:
   - Click "Code" > "New Notebook" on the competition page.
   - Add the dataset via "+ Add Data" > search "demand-forecasting-kernels-only".
4. **Copy Code**: Copy the notebook cells from this project into your Kaggle notebook.
5. **Run**: Execute cells sequentially (Shift + Enter). No additional package installation is needed as all dependencies are pre-installed.

## Notebook Structure
- **Cell 1**: Import libraries.
- **Cell 2**: Load and preprocess data.
- **Cells 3-8**: EDA (info, time series, decomposition, autocorrelation, distribution, monthly trends).
- **Cell 9**: Feature engineering.
- **Cell 10**: Train-test split (last 90 days as test).
- **Cells 11-18**: Model training and evaluation (ARIMA, SARIMA, ARIMAX, SARIMAX, Linear Regression, Logistic Regression, XGBoost, Ensemble).
- **Cell 19**: Individual model plots vs. actual sales.
- **Cell 20**: Combined forecast comparison plot.
- **Cell 21**: RMSE bar plot.
- **Cell 22**: Summary of results.

## Outputs
- **EDA Plots**: Insights into trends, seasonality, and data distribution.
- **Model Performance**:
  - RMSE for each regression model.
  - Accuracy for Logistic Regression.
- **Visualizations**:
  - 4x2 subplot grid showing each model’s predictions vs. actual sales.
  - Combined forecast plot for all models.
  - Bar plot comparing RMSE across models.

## Usage
- **Run All**: Use "Run All" in Kaggle to execute the entire notebook.
- **Customize**:
  - Extend to other stores/items by modifying the filter in Cell 2.
  - Adjust grid search ranges in Cells 11 and 12 for better model tuning.
  - Add more features (e.g., additional lags, external data) in Cell 9.

## Notes
- **Scalability**: The current implementation focuses on Store 1, Item 1. For multi-store/item analysis, loop over `store` and `item` in Cell 2.
- **Computation**: Grid search for ARIMA/SARIMA may take time; reduce parameter ranges (e.g., `range(0, 2)`) for faster execution.
- **Holidays**: The `is_holiday` feature is synthetic. For better accuracy, merge with a real holiday dataset.

## License
This project is open-source and uses the Kaggle dataset under its competition rules. Code is provided under the MIT License.

## Acknowledgments
- Dataset provided by the Kaggle community.
- Built with Python data science libraries and Kaggle’s notebook environment.
