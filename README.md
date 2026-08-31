# Retail Demand Intelligence & Forecasting

A machine learning-based retail demand forecasting project that predicts **store-item level sales** using historical demand patterns, seasonality, time-series features, and XGBoost.

## 📌 Project Overview

Accurate demand forecasting helps retailers improve inventory planning, replenishment, and resource allocation. This project analyzes historical sales across **10 stores and 50 items** and develops an XGBoost regression model to forecast future demand at the store-item level.

The project combines exploratory data analysis, time-series feature engineering, machine learning, model evaluation, and a **30-day future demand forecast**.

## 🎯 Objectives

* Identify temporal, weekly, and yearly demand patterns.
* Analyze sales differences across stores and products.
* Engineer time-series features to capture demand trends and seasonality.
* Build and evaluate an XGBoost demand forecasting model.
* Generate 30-day forecasts for every store-item combination.
* Translate forecasting results into actionable inventory and demand-planning insights.

## 📊 Dataset

**Store Item Demand Forecasting Dataset — Kaggle**

The dataset contains historical daily sales for:

* **10 stores**
* **50 items**
* Multiple years of daily observations

Key columns include:

* `date`
* `store`
* `item`
* `sales`

## 🔍 Exploratory Data Analysis

The analysis identified several important demand patterns:

* Daily sales exhibit a **right-skewed distribution**, with occasional high-demand days.
* Sales follow a clear **weekly seasonal pattern**, gradually increasing from Monday toward Sunday.
* Monthly demand generally increases from **January through July**, followed by a decline.
* Yearly sales exhibit a recurring wave-like pattern, with **peak demand increasing across years**.
* Store-level demand varies considerably, with **Store 2** having the highest historical sales and **Store 7** the lowest.
* The highest-selling items are **15, 28, 13, 18, 25, 45, 38, 22, 36, and 8**.

## ⚙️ Feature Engineering

Time-series features were created to capture recent demand, seasonality, and demand variability.

### Lag Features

* Lag 1
* Lag 7
* Lag 14
* Lag 28

### Rolling Features

* 7-day rolling mean
* 14-day rolling mean
* 28-day rolling mean
* 7-day rolling standard deviation

### Additional Features

* 1-day sales change
* 7-day sales growth
* Year
* Month
* Day of week
* Week of year

The strongest model features were **7-day rolling mean, 14-day rolling mean, and lag-7 sales**, highlighting the importance of recent demand and weekly seasonality.

## 🤖 Modeling

**Model:** XGBoost Regressor

The data was split chronologically, using the **last 90 days as the test set** and all preceding observations for training. This approach reflects a realistic forecasting scenario where historical data is used to predict future demand while avoiding temporal leakage.

### Baseline

A **lag-7 forecasting baseline** was established for comparison.

**Baseline MAE:** 9.07

### XGBoost Performance

| Metric                       |     Result |
| ---------------------------- | ---------: |
| MAE                          |   **5.95** |
| RMSE                         |   **7.70** |
| MAPE                         | **13.04%** |
| Actual-Predicted Correlation |  **0.963** |
| Prediction Bias              |  **-0.12** |

The XGBoost model achieved approximately **34.4% lower MAE than the lag-7 baseline**.

## 🔮 Future Demand Forecast

The trained model was used to generate a **30-day forecast for every store-item combination**.

**Forecast Period:** January 1–30, 2018

| Forecast Metric        |       Value |
| ---------------------- | ----------: |
| Total Forecasted Sales | **634,146** |
| Average Daily Forecast |  **21,138** |
| Minimum Daily Forecast |  **16,831** |
| Maximum Daily Forecast |  **25,400** |

The forecast preserved the recurring seasonal pattern observed in the recent historical data while adapting to changes in recent demand levels.

## 🏪 Store-Level Forecast Insights

The highest forecasted store demand was:

1. Store 2 — **81,275**
2. Store 8 — **77,344**
3. Store 3 — **72,478**
4. Store 10 — **70,684**
5. Store 4 — **67,306**

Store 2 historically had the highest sales and also received the highest future demand forecast.

Store-level forecast errors ranged from approximately **4.93 to 6.81 MAE**, with Store 7 being the most predictable and Store 2 having the highest forecast error.

## 📦 Item-Level Forecast Insights

The top forecasted items were:

**28, 15, 13, 18, 25, 38, 45, 22, 36, 8**

These closely match the historical top-selling items, indicating that the model preserves the established product-demand hierarchy in its future predictions.

High-demand items such as **28, 15, 13, 38, and 25** also exhibited relatively higher forecasting errors, suggesting greater demand variability and forecasting difficulty.

## 💼 Business Insights

The analysis suggests several practical applications:

* **Store-specific inventory allocation:** High-demand stores can receive greater inventory allocation based on expected demand.
* **Product prioritization:** High-demand items can receive closer replenishment monitoring.
* **Risk-aware inventory planning:** High-volume and high-volatility stores/items may require more flexible replenishment and safety-stock strategies.
* **Seasonal planning:** Weekly and annual demand patterns can support staffing, inventory, and supply planning.
* **Store-item forecasting:** Forecasting at the store-item level enables more granular planning than using a single aggregate demand forecast.

## ✅ Forecast Validation

Additional validation checks showed:

* **0 negative predictions**
* Strong actual-vs-predicted correlation of **0.963**
* Prediction bias close to zero (**-0.12**)
* Future forecasts retained the seasonal structure observed in recent historical demand.

## 🛠️ Technologies & Skills

**Python · XGBoost · Time-Series Forecasting · Feature Engineering**



The project demonstrates how machine learning and time-series feature engineering can transform historical retail sales data into **store-item level demand forecasts** that support inventory planning, replenishment, and operational decision-making.
