# Bike Rental Demand Prediction

## Problem Statement
Bike-sharing companies need to predict how many bikes will be rented at a given time so they can efficiently allocate bikes across stations, plan maintenance and avoid shortages or surpluses. This project builds a regression model to predict bike rental demand based on weather and time-related conditions.

## Dataset
UCI Bike Sharing Dataset (17,379 records) — fetched directly via the `ucimlrepo` Python package. Contains hourly rental data with weather, seasonal and time-based features.

**Target Variable:** `cnt` — total bike rentals (continuous value)

**Key Features:** season, weather condition, temperature, humidity, windspeed, hour of day, weekday, working day, holiday

## Data Preprocessing
- Checked for missing values and duplicate records (none found — clean dataset)
- Converted the date column to proper datetime format
- One-hot encoded categorical features (`season`, `weathersit`) since they represent categories, not ranked values
- Removed `casual` and `registered` columns to avoid data leakage (they sum directly to the target variable)

## Exploratory Data Analysis
- Rental demand peaks sharply during commute hours (~8 AM and 5–6 PM)
- Demand is higher in Fall/Summer seasons, lower in Spring
- Clear weather conditions show significantly higher rentals than rainy/snowy conditions
- Weekday patterns show commute-hour peaks; weekends show a more spread-out midday pattern

## Model
- **Algorithm:** Linear Regression (baseline) and Random Forest Regressor (final deployed model)
- **Train/Test Split:** 80/20

## Evaluation Results (Linear Regression baseline)
| Metric | Value |
|---|---|
| MAE | 103.74 |
| MSE | 19,021.30 |
| RMSE | 137.92 |
| R² Score | 0.40 |

## Deployment
An interactive prediction app was built using **Gradio**, allowing users to input weather and time conditions and receive real-time bike demand predictions, along with a live hourly demand trend chart.

## Tech Stack
Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, Gradio

## How to Run
1. Open the notebook in Google Colab
2. Run all cells in order
3. The Gradio app will launch inline with a shareable link
