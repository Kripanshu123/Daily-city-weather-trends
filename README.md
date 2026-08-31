# Daily City Weather Trends & Predictive Analytics

A Python-based data analytics and machine learning pipeline for simulating, cleaning, engineering, and forecasting daily meteorological time-series data.

---

## 📌 Project Overview

This project implements an end-to-end data analytics pipeline focused on city weather patterns over a 2-year horizon:
1. **Synthetic Data Generation:** Models realistic daily meteorological parameters (Temperature, Humidity, Pressure, Wind Speed, Rainfall) using sinusoidal seasonality and stochastic noise.
2. **Data Cleaning:** Handles missing data via time-series linear interpolation and suppresses sensor outliers using Interquartile Range (IQR) bounds.
3. **Feature Engineering:** Computes rolling moving averages (7-day, 30-day), rolling volatility, diurnal temperature ranges, lag features ($t-1$, $t-7$), and statistical anomaly detection ($2\sigma$ bands).
4. **Predictive Modeling:** Trains a multi-variable Linear Regression model to forecast average temperatures.
5. **Visual Dashboard:** Renders a 4-panel diagnostic analytics dashboard.

---

## 📁 Repository Structure

```
├── weather_engine.py    # Data generation, cleaning, and feature engineering module
├── main_analytics.py    # Model training, evaluation, and dashboard visualization
└── README.md            # Project documentation
```

---

## ⚙️ Features & Pipeline Modules

### 1. Data Processing (`weather_engine.py`)
* `generate_weather_data(n_days=730, seed=42)`: Generates 2 years of daily weather records with injected nulls and sensor spikes.
* `clean_weather_data(df)`: Applies IQR outlier suppression and bidirectional linear interpolation.
* `engineer_features(df)`: Derives rolling metrics, diurnal spread, lag variables, and flags anomalies.

### 2. Analytics & Modeling (`main_analytics.py`)
* `train_weather_model(df)`: Splits data chronologically (80% train / 20% test) and fits a Linear Regression model.
* `plot_weather_dashboard(df, test_results)`: Generates a 4-panel visualization:
  * **Time Series & Anomalies:** 30-day rolling trend with statistical anomaly scatter.
  * **Monthly Spread:** Distribution boxplots by month.
  * **Correlation Matrix:** Inter-variable Pearson correlation heatmap.
  * **Actual vs. Predicted:** Evaluation scatter plot with reference perfect fit line.

---

## 🚀 Getting Started

### Prerequisites
Ensure Python 3.8+ is installed along with the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Running the Pipeline
Execute the main script from your terminal:

```bash
python main_analytics.py
```

---

## 📊 Sample Metrics & Output
* **Metrics:** Evaluates model performance via Root Mean Squared Error (RMSE) and Coefficient of Determination ($R^2$).
* **Dashboard:** Automatically opens the 4-panel Seaborn/Matplotlib visualization window upon execution.
