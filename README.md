# Air Quality Index (AQI) Prediction System

## Overview
A machine learning system that predicts Air Quality Index using 5.8 million+ air quality from 123 monitoring stations across Taiwan (2016-2024). Achieved 95.8% R^2 score using Gradient Boosting.

## Problem Statement
Air quality prediction is crucial for public health warnings and policy decisions. This project aims to build an accurate real-time AQI forecasting system using historical pollution data.

## Dataset
- Source: Taiwan EPA Air Quality Monitoring Network
- Size: 5.8M+ records
- Features: PM2.5, PM10, NO2, SO2, CO, O3, temperature, humidity
- Time Period: 2016-2024

## Approach

### 1. Data Preprocessing
- Handled missing values using forward fill and interpolation
- Removed outliers using IQR method
- Feature scaling using StandardScaler

### 2. Feature Engineering
- Created 70+ features including:
      - Rolling averages (3-day, 7-day, 30-day windows)
      - Lag features for pollutant values
      - Pollution ratios (PM2.5/PM10, etc.)
      - Temporal features(hour, day, month, season)

### 3. Feature Selection
- Correlation analysis
- ANOVA F-test
- Mutual Information scores
- Lasso regularization
- Random Forest feature importance

### 4. Model Development
Compared 6 regression models:
- Linear regression
- Ridge regression
- Lasso regression
- Random Forest
- Grandient Boosting
- Support Vector Regression (SVR)

Used K-Fold cross-validation (k=5) and GridSearchCV for hyperparameter tuning.

## Results
 | Model                 | R2 Score | MAE   | RMSE  |
 | --------------------- | -------- | ------| ------|
 | Linear                | 0.823    | 0.312 | 0.445 | 
 | Ridge                 | 0.826    | 0.308 | 0.441 |
 | Lasso                 | 0.825    | 0.310 | 0.443 | 
 | Random Forest         | 0.941    | 0.178 | 0.256 | 
 | **Gradient Boosting** | **0.958** | **0.144** | **0.206**|
 | SVR                   | 0.887    | 0.245 | 0.355 | 

**Best Model: Gradient Boosting with 95.8% R2 score**

## Key Learnings
- Feature engineering significantly improved model performance
- Ensemble methods (RF, GB) outperformed linear models
- Temporal and lag features were most important predictors
- Cross-validation prevented overfitting

## Technologies Used
- **Python 3**
- **Libraries**: Pandas, Numpy, Scikit-learn, Matpotlib, Seaborn
- **Models**: Gradient Boosting, Random Forest, Linear Regression
- **Tools**: Jupyter Notebook, GridSearchCV
