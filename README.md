# ⚡ Electricity Demand Forecasting

## 📌 Overview

This project develops and evaluates time-series forecasting models to predict national electricity demand using historical demand, temporal patterns, and weather data.

The objective is to build a structured modelling pipeline, compare multiple algorithms, and identify the most effective approach based on predictive performance.

---

## 🎯 Objectives

* Build a baseline forecasting model using lag features
* Improve performance using temporal and weather features
* Compare multiple algorithms on a consistent time-series split
* Select the best-performing model using Mean Absolute Error (MAE)

---

## 📊 Dataset

* **Source:** https://www.kaggle.com/datasets/saurabhshahane/electricity-load-forecasting
* **Primary file used:** `continuous dataset.csv`

### Key Variables

* `nat_demand` — national electricity demand (target variable)
* `datetime` — timestamp for each observation
* Weather features — temperature, humidity, wind, and atmospheric conditions
* Calendar features — holidays and school schedules

A subset of weather features (single location) was selected to reduce redundancy and maintain interpretability while retaining key environmental signals.

---

## ⚙️ Methodology

### 1. Data Preparation

* Converted timestamps to datetime format
* Sorted data chronologically and set as index
* Preserved temporal order for forecasting

---

### 2. Feature Engineering

To capture demand patterns:

* **Lag Features**

  * `lag_1` → previous timestep
  * `lag_24` → same time previous day

* **Temporal Features**

  * Hour of day
  * Day of week

* **Weather Features**

  * Temperature (`T2M_toc`)
  * Humidity (`QV2M_toc`)

---

### 3. Train/Test Split

A **chronological split** was used:

* First 80% → training
* Last 20% → testing

This ensures the model is evaluated on future data, avoiding data leakage.

---

### 4. Models Implemented

* Linear Regression (baseline comparison)
* Random Forest Regressor
* Gradient Boosting Regressor

---

### 5. Evaluation Metric

* **Mean Absolute Error (MAE)** — measures average prediction error in the same units as electricity demand

---

## 📈 Results

| Model             | MAE              |
| ----------------- | ---------------- |
| Linear Regression | ~37.7            |
| Random Forest     | **~19.1 (Best)** |
| Gradient Boosting | ~22.9            |

Feature engineering reduced MAE by approximately **50%**, demonstrating its impact on model performance.

---

## 📊 Visualisation

* Electricity demand trends over time
* Actual vs predicted demand (Random Forest)
* Model comparison (MAE)
* Feature importance analysis


## 🧠 Key Insights

* Electricity demand shows strong **daily and weekly seasonality**
* **Feature engineering had the largest impact on performance**, significantly improving accuracy
* **Tree-based models outperformed linear models**, indicating non-linear relationships
* Additional lag features (e.g. weekly lag) did not improve performance, highlighting the importance of feature selection



## 🏁 Conclusion

Random Forest achieved the best performance, effectively capturing non-linear relationships between demand, time, and weather features.

This project highlights that **feature engineering is more impactful than model complexity** in time-series forecasting tasks.



## 🚀 Future Improvements

* Hyperparameter tuning for further optimisation
* Expanding weather features across multiple locations
* Time-series cross-validation
* Comparison with external or real-time forecasting systems



## 🛠️ Tech Stack

* Python
* Pandas, NumPy
* Scikit-learn
* Matplotlib



## 📌 Key Takeaway

A structured approach combining feature engineering, model comparison, and proper evaluation can significantly improve forecasting performance in real-world time-series problems.
