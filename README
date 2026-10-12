# Electricity Demand Forecasting

Forecast electricity demand for Karnataka and Maharashtra using Databricks, PySpark, XGBoost, and Power BI.

## Project overview
The workflow organizes data into Bronze, Silver, and Gold layers in Databricks, trains an XGBoost next-day demand regression model, and presents historical demand, a seven-day forecast, and model performance in Power BI.

## Architecture
```text
Electricity demand + state weather
              |
              v
       Bronze (Databricks)
              |
   duplicate/conflict handling
              |
              v
        Silver (PySpark)
   demand + state-level weather
              |
              v
       Gold feature layer
 calendar features, exact-date lags,
 rolling features, next-day target
              |
              v
        XGBoost regression
              |
              v
     Final prediction results
              |
              v
          Power BI report
```

## Technologies
- Databricks and Delta tables
- Apache Spark / PySpark
- Python, pandas, NumPy
- XGBoost
- scikit-learn evaluation metrics
- Power BI

## Dataset and data-quality decisions
The modeling workflow covers Karnataka and Maharashtra. The cleaned modeling dataset contains 3,888 dates per state from 2013-01-01 through 2024-04-28 before feature/target eligibility filtering.

The Bronze source contained duplicate dates. Exact duplicate rows were removed in a separate candidate table. Twelve dates with conflicting records were excluded from the modeling dataset because no authoritative original record or ingestion timestamp was available. The original Bronze table and a conflict table were retained for audit.

The date series has missing calendar dates. Calendar-date lag features were created using exact-date lookups rather than assuming the previous row is the previous calendar day. Rows with missing required lag/target values were excluded from training.

## Model and evaluation
The retrained XGBoost model used a chronological train/test split.

| Item | Result |
|---|---:|
| Training rows | 5,188 |
| Test rows | 1,298 |
| Split date | 2022-03-22 |
| MAE | 1,023.30 |
| RMSE | 1,336.87 |
| R² | 0.9617 (96.17%) |

These are the recorded evaluation results for the current test set. Confirm the source dataset's exact unit definition before interpreting the demand scale operationally.

## Limitations
- Twelve conflicting source dates were excluded rather than resolved against an authoritative source.
- The dataset has 248 missing calendar dates over its date range.
- Rolling features in the current Gold implementation use previous available observations, not a complete calendar window.
- The seven-day recursive forecast holds future weather features constant; it is a demonstration forecast, not an operational weather-aware forecast.
- Test-set results do not guarantee future performance.

## Databricks tables
Catalog/schema: `electricity_catalog.electricity_schema`

- `bronze_energy`
- `bronze_karnataka_weather`
- `bronze_maharashtra_weather`
- `bronze_energy_exact_clean`
- `bronze_energy_conflicts`
- `bronze_energy_modeling`
- `silver_electricity_weather`
- `gold_electricity_demand`
- `gold_electricity_demand_calendar`
- `gold_7day_demand_forecast`
- `ml_prediction_results`
- `ml_prediction_results_final`
- `state_demand_summary`

## Repository structure
```text
.
├── README.md
├── requirements.txt
├── .gitignore
├── docs/
├── notebooks/
├── src/
├── powerbi/
└── screenshots/
```

Export your actual Databricks notebooks into `notebooks/` before presenting this repository as fully reproducible. Add screenshots of the completed Power BI pages to `screenshots/`. Only include the `.pbix` file if you have checked it for credentials and private data.

## Reproducing the workflow
1. Configure Databricks access and create the catalog/schema.
2. Load the electricity-demand and weather datasets into Bronze Delta tables.
3. Run the cleaning and Silver/Gold feature-engineering notebooks.
4. Train XGBoost with a chronological split and evaluate on held-out dates.
5. Save prediction results to Delta.
6. Connect Power BI to the final prediction table and refresh the report.

Never commit personal access tokens, passwords, credential files, or private/raw datasets.

## Author
Akhilesh Gurav
