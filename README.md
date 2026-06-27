# Demand Forecasting Case Study

## Project Overview

This project develops a machine learning-based demand forecasting solution to predict product demand across multiple supermarkets and SKUs. The objective is to support production planning by reducing stock-outs and minimizing excess inventory through accurate demand forecasting.

The project includes data exploration, feature engineering, predictive modeling using XGBoost, model evaluation, and business recommendations.

---

## Problem Statement

A retail demand planning team has experienced increasing stock-outs and inventory write-offs due to inaccurate demand forecasts.

The objective is to forecast demand for each supermarket–SKU combination **eight weeks in advance** using historical sales and promotional data.

---

## Dataset

Two datasets are provided:

### 1. demand.csv

Historical daily demand data.

| Column | Description |
|---------|-------------|
| date | Calendar date |
| supermarket | Supermarket chain |
| sku | Product |
| demand | Units sold |

### 2. promotions.csv

Promotion schedule.

| Column | Description |
|---------|-------------|
| promotion_date | Promotion start date |
| supermarket | Supermarket chain |
| sku | Product |

Each promotion lasts for one week from the listed start date.

---

## Project Workflow

The project follows the following workflow:

```
Data Loading
      ↓
Data Quality Assessment
      ↓
Exploratory Data Analysis
      ↓
Feature Engineering
      ↓
Model Development
      ↓
Model Evaluation
      ↓
Business Recommendations
```

---

## Exploratory Data Analysis

The following analyses were performed:

- Data quality assessment
- Missing value analysis
- Duplicate detection
- Demand trend analysis
- Monthly seasonality
- Weekly seasonality
- Supermarket-wise demand comparison
- SKU-wise demand comparison
- Promotion impact analysis

### Key Insights

- Organic Milk has the highest average demand.
- DailyNeeds records the highest average demand among supermarkets.
- Demand peaks on Thursdays.
- Promotions are associated with higher demand.
- Historical demand remains relatively stable with occasional spikes.

---

## Feature Engineering

The following features were created:

### Calendar Features

- Year
- Month
- Day
- Day of Week
- Week of Year
- Quarter
- Weekend Indicator

### Promotion Feature

- Promotion indicator

### Historical Demand Features

- 7-day lag
- 14-day lag
- 28-day lag

### Rolling Statistics

- 7-day rolling mean
- 14-day rolling mean
- 28-day rolling mean

### Encoded Features

- Supermarket
- SKU

Missing demand values were imputed within each supermarket–SKU series using interpolation followed by forward/backward filling where necessary.

---

## Model Selection

An **XGBoost Regressor** was selected because it:

- Performs well on structured tabular datasets.
- Captures complex non-linear relationships.
- Handles interactions between historical demand, seasonality, and promotions.
- Requires minimal preprocessing.
- Is widely used for retail demand forecasting problems.

A chronological train-test split was used to prevent data leakage.

---

## Model Evaluation

The model was evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

### Results

| Metric | Value |
|---------|--------:|
| MAE | 8.00 |
| RMSE | 30.38 |
| R² | 0.213 |

### Interpretation

The model predicts demand with an average error of approximately **8 units**. While it performs well for regular demand patterns, it tends to underestimate sudden demand spikes, likely due to external factors such as holidays or weather that are not included in the dataset.

---

## Feature Importance

The model identified the following as the most influential predictors:

- 28-day Rolling Mean
- 14-day Rolling Mean
- 14-day Lag
- 7-day Lag
- Month

These results indicate that historical demand patterns are the strongest drivers of future demand.

---

## Business Recommendations

Based on the analysis:

- Use historical demand as the primary forecasting signal.
- Incorporate weekly demand patterns into production planning.
- Continue accounting for promotions in demand forecasts.
- Include external variables such as holidays, weather, pricing, and competitor activity to improve forecasting accuracy.
- Use the model as a baseline forecasting tool to reduce stock-outs and inventory write-offs.

---

## Repository Structure

```
DemandForecasting/
│
├── data/
│   ├── demand.csv
│   └── promotions.csv
│
├── notebook/
│   └── Demand_Forecasting.ipynb
│
├── outputs/
│   ├── forecast_results.csv
│   ├── feature_importance.csv
│   └── xgboost_model.pkl
│
├── slides/
│   └── Business_Summary.pdf
│
├── requirements.txt
│
├── README.md
│
└── .gitignore
```

---

## Installation

Clone the repository:

```bash
git clone <repository-url>
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the environment:

**Windows**

```bash
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Running the Project

Open the notebook:

```
notebook/Demand_Forecasting.ipynb
```

Run all cells sequentially to reproduce the analysis, feature engineering, model training, evaluation, and output generation.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- XGBoost
- Joblib

---

## Author

**Disa Bandhu**

