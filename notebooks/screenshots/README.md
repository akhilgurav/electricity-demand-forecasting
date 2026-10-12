# Electricity Demand Forecasting Using Databricks, PySpark, XGBoost & Power BI

## 📌 Project Overview
This project analyzes electricity demand data for Karnataka and Maharashtra using a big data processing pipeline and machine learning. It uses Databricks and PySpark for data preparation, XGBoost for next-day electricity demand prediction, and Power BI for interactive visualization.

## 🏗️ Architecture

**Data Sources → Bronze → Silver → Gold → XGBoost Model → Power BI Dashboard**

- **Bronze Layer:** Ingest and organize raw electricity demand and weather data.
- **Silver Layer:** Clean and join electricity demand with weather data.
- **Gold Layer:** Prepare analytical datasets, calendar-based lag features, and forecasting data.
- **Machine Learning:** Train an XGBoost regression model using historical demand, calendar, and weather features.
- **Visualization:** Present demand trends, forecasts, and model performance in Power BI.

## 🛠️ Technologies Used
- **Big Data:** Databricks, Apache Spark, PySpark
- **Programming:** Python, SQL
- **Machine Learning:** XGBoost, Pandas, NumPy, scikit-learn
- **Cloud/Data Platform:** Databricks
- **Visualization:** Microsoft Power BI
- **Data Engineering:** Bronze, Silver, and Gold architecture, data cleaning, feature engineering

## 📊 Model Performance
The XGBoost model was evaluated using a chronological train-test split.

| Metric | Test Result |
|---|---:|
| MAE | 1,023.30 MU |
| RMSE | 1,336.87 MU |
| R² Score | 96.17% |

These results describe performance on the held-out test data. They do not guarantee the same accuracy on future data.

## 📈 Power BI Dashboard
The dashboard includes:
- Executive Overview of electricity demand
- Forecast & Prediction
- Model Performance, including actual versus predicted demand and prediction errors

### Dashboard Screenshots
See the [`notebooks/screenshots`](notebooks/screenshots/) folder.

## 🧹 Data Quality
- Identified and removed exact duplicate records from the modeling dataset.
- Kept conflicting date records separate for audit and excluded those dates from modeling.
- Joined electricity demand and weather datasets for Karnataka and Maharashtra.
- Created calendar-based lag features for demand forecasting.

## 📁 Repository Structure
```text
electricity-demand-forecasting/
├── notebooks/
│   ├── Bronze_data_ingestion.ipynb
│   └── screenshots/
├── README.md
├── requirements.txt
└── .gitignore
```

## 🚀 How to Explore
1. Review the Databricks notebook in `notebooks/`.
2. Explore the Power BI dashboard screenshots in `notebooks/screenshots/`.
3. Review `requirements.txt` for the Python dependencies.

## 👨‍💻 Author
**Akhilesh Gurav**

GitHub: [akhilgurav](https://github.com/akhilgurav)

---

*Built as a big data analytics and machine learning project focused on electricity demand forecasting.*
