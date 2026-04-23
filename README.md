
# 📊 Fuel Price Prediction (2020–2026)

This project focuses on analyzing and predicting global fuel prices using historical data and machine learning models. The goal is to understand how different factors like crude oil prices, taxes, and time influence petrol prices—and then build models to forecast them.

---

## 🚀 Overview

Fuel prices are influenced by multiple variables such as:

* Crude oil (Brent) prices
* Government tax percentages
* Time-based trends
* Country-specific variations

In this project, we:

1. Clean and explore the dataset
2. Perform feature engineering
3. Train multiple regression models
4. Evaluate and compare their performance

---

## 📁 Dataset

The dataset used:

```
global_fuel_prices_2020_2026.csv
```

It contains:

* `date` — timestamp of the record
* `country` — country name
* `petrol_usd_liter` — fuel price per liter
* `brent_crude_usd` — crude oil price
* `tax_percentage` — applied fuel tax

---

## 🛠️ Tech Stack

* Python
* Pandas & NumPy (data handling)
* Matplotlib & Seaborn (visualization)
* Scikit-learn (ML models)

---

## 🔍 Workflow

### 1. Data Loading & Exploration

* Loaded dataset using Pandas
* Checked structure with `.info()`, `.describe()`
* Identified missing values and distributions

---

### 2. Feature Engineering

Some meaningful features were created:

* **Date conversion**

  ```python
  df['date'] = pd.to_datetime(df['date'])
  ```

* **Tax value (actual impact)**

  ```python
  df['tax_val'] = df['petrol_usd_liter'] * (df['tax_percentage'] / 100)
  ```

* **Lag feature (previous crude price)**

  ```python
  df['brent_lag_1'] = df.groupby('country')['brent_crude_usd'].shift(1)
  ```

This lag feature helps the model understand temporal dependencies (very important for time-based data).

---

### 3. Data Preprocessing

* Sorting data by country and date
* Handling missing values (especially from lag features)
* Encoding categorical variables (e.g., country)
* Scaling numerical features

---

### 4. Model Training

We trained multiple regression models:

* Linear Regression
* Decision Tree Regressor
* Random Forest Regressor

---

### 5. Evaluation Metrics

Models were evaluated using:

* MAE (Mean Absolute Error)
* MSE (Mean Squared Error)
* RMSE
* R² Score

---

## 📈 Results

* **Linear Regression**: Simple but limited in capturing non-linearity
* **Decision Tree**: Better at handling complex patterns but prone to overfitting
* **Random Forest**: Best overall performance due to ensemble learning

👉 Random Forest generally performed the best in terms of accuracy and stability.

---

## 💡 Key Insights

* Brent crude price is a strong predictor of petrol prices
* Tax percentage has a significant localized impact
* Lag features improve prediction accuracy
* Tree-based models outperform linear models for this dataset

---

## ⚙️ How to Run

1. Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

2. Run the notebook:

```bash
jupyter notebook DS_Final_Project.ipynb
```


