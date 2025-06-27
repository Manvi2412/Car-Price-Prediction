# Car Price Prediction Using Machine Learning

This project predicts the resale price of cars using various features such as manufacturing year, fuel type, kilometers driven, and more. It combines exploratory data analysis, model tuning, explainability techniques, and deployment through a web application built with Streamlit.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Feature Engineering](#feature-engineering)
- [Modeling & Evaluation](#modeling--evaluation)
- [SHAP Explainability](#shap-explainability)
- [Residual & Drift Analysis](#residual--drift-analysis)
- [Deployment](#deployment)
- [Folder Structure](#folder-structure)
- [How to Run](#how-to-run)
- [Dependencies](#dependencies)

---

## Project Overview

This machine learning pipeline is designed to estimate a car’s market value based on historical data. The goal is to help individuals or dealers set fair resale prices and to understand what factors influence those prices the most.

---

## Dataset

- Source: Provided as `CarPrice.csv`
- Size: 299 rows × 8 columns
- Features:
  - **Year**: Manufacturing year
  - **Present_Price**: Original price of the car (in lakhs)
  - **Kms_Driven**: Kilometers driven
  - **Fuel_Type**: Petrol, Diesel, or CNG
  - **Seller_Type**: Dealer or Individual
  - **Transmission**: Manual or Automatic
  - **Owner**: Number of previous owners
  - **Selling_Price**: Target variable

---

## Exploratory Data Analysis

- **Selling Price** is right-skewed; most used cars are under ₹10 lakhs.
- **Older cars (before 2010)** typically sell for less than ₹3 lakhs.
- **Petrol cars** dominate the data, but diesel cars tend to have higher resale value.
- **Transmission type** and **seller type** also affect price significantly.
- **Kms Driven** and **Present Price** are moderately correlated with **Selling Price**.

Key visualizations included:
- Price trend by year
- Correlation heatmap
- Boxplots by categorical features
- Actual vs Predicted scatter
- SHAP summary and bar plots

---

## Feature Engineering

- Created derived features such as car age from manufacturing year.
- Applied one-hot encoding to categorical features.
- Removed outliers based on distribution of `Kms_Driven` and `Present_Price`.

---

## Modeling & Evaluation

Tested multiple regression models:
- **Linear Regression**
- **Random Forest**
- **Tuned XGBoost (final model)**

Performance comparison:

| Model              | RMSE   | R² Score |
|-------------------|--------|----------|
| Linear Regression | ~1.55  | ~0.72    |
| Random Forest     | ~0.85  | ~0.91    |
| XGBoost (Tuned)   | ~0.78  | ~0.94    |

Advanced techniques:
- **RandomizedSearchCV** for hyperparameter tuning
- **Cross-validation** to ensure stability
- **Learning curve** analysis to check for overfitting

---

## SHAP Explainability

Used SHAP (SHapley Additive Explanations) to interpret the XGBoost model:

- **Present_Price** was the most influential feature.
- **Fuel_Type** and **Transmission** significantly impacted predictions.
- Visualized global and local impact using summary and waterfall plots.

---

## Residual & Drift Analysis

- Residuals are centered around zero with a normal distribution.
- No major heteroscedasticity or underfitting signs detected.
- Year-wise drift was analyzed using boxplots to check for shifts in data distribution across time.

---

## Deployment

Deployed as a **Streamlit Web App**:

- Users input car features via sliders and dropdowns.
- App displays estimated selling price in real time.
- Model loaded using `joblib`.

Run with:
streamlit run app.py

### Folder Structure
car-price-prediction/
├── app.py
├── car_price_model.pkl
├── CarPrice.csv
├── requirements.txt
├── README.md
├── .gitignore
├── CarPriceEDA.ipynb


### How to Run
Clone the repository

Install dependencies
pip install -r requirements.txt

Run the app
streamlit run app.py

### Dependencies
Python 3.8+

streamlit

pandas

numpy

scikit-learn

xgboost

shap

seaborn

matplotlib

joblib










