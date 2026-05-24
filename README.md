#  Spatio-Temporal Crime Forecasting (Chicago)

## Overview
This repository contains an end-to-end **spatio-temporal crime forecasting system** built using the public **Chicago Crime Dataset**.  
The project predicts **future crime patterns at the police district level** and converts forecasts into **actionable insights for law-enforcement planning**.

The work is implemented across **two complementary notebooks**, demonstrating both **modeling depth** and **real-world decision focus**.

---

## Objectives
- Forecast crime counts **per police district over time**
- Capture **trend, seasonality, and regime shifts**
- Handle **spatial heterogeneity** across districts
- Compare **statistical, machine learning, and deep learning models**
- Predict **future district-level crime risk**
- Support **proactive police resource allocation**

---

##  Dataset
- **Source**: Public Chicago Crime Dataset  
- **Raw Size**: ~1M+ crime incidents  
- **Data Type**: Event-level records  
- **Final Structure**: Panel time series  

Each raw record represents a **single crime incident**, which is aggregated into:

(District, Time) → Crime Count

---

## Repository Structure

    ├── notebook_1_weekly_model_comparison.ipynb 
    ├── notebook_2_monthly_district_forecasting.ipynb
    ├── README.md



---

## Notebook 1 — Weekly Crime Forecasting & Model Comparison

### Focus
Methodology, benchmarking, and model evaluation

### Granularity
- Time: Weekly  
- Space: Police District  

### Pipeline
- Data cleaning and aggregation
- Weekly crime counts per district
- Exploratory analysis (trend, seasonality, volatility)
- Time-aware train/validation split (no leakage)
- Feature engineering:
  - Lag features
  - Rolling statistics
  - Calendar features
  - District as categorical feature

### Models Implemented
- Naive baseline
- SARIMA (classical benchmark)
- LightGBM (global machine learning model)
- LSTM (deep learning)

### Model Performance
| Model | MAE | RMSE |
|------|-----|------|
| Naive Baseline | 22.38 | 31.15 |
| SARIMA | 42.19 | 49.99 |
| **LightGBM** | **21.87** | **29.86** |
| LSTM | 22.99 | 32.24 |

**Key Insight**  
Gradient boosting outperformed both classical and deep learning approaches on structured weekly crime data.

---

## Notebook 2 — Monthly District Forecasting & Crime Risk

### Focus
Police-oriented forecasting and decision support

### Granularity
- Time: Monthly  
- Space: Police District  

### Pipeline
- Monthly crime aggregation per district
- Panel time-series construction
- Feature engineering:
  - Lag features (1, 3, 12)
  - Rolling mean and volatility
  - Month encoding
  - District identity
- Seasonal naive baseline
- XGBoost global spatio-temporal model

### Results
- XGBoost reduced:
  - **MAE by ~42%**
  - **RMSE by ~39%**
  compared to the seasonal naive baseline.

### Forecasting & Risk Analysis
- Recursive multi-step forecasting (6 months)
- District-wise future crime predictions
- Crime rate estimation using population proxies
- High-risk district ranking for proactive deployment

---

## 🚓 Practical Use-Cases
- Patrol and manpower planning
- Seasonal crime preparedness
- District-level risk prioritization
- Data-driven public safety decision support

---

## ⚠️ Limitations
- District population values are approximated
- Recursive forecasting accumulates uncertainty over long horizons
- External factors (weather, events, policy changes) are not modeled
- Forecasts are for aggregate crime counts only

---
