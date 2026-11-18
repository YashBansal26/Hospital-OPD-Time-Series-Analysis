# Hospital OPD Time Series Analysis

This project forecasts hospital outpatient department (OPD) demand and compares classical, machine-learning and deep-learning time-series models. The main deliverable is the Jupyter notebook; `data/opd_data.csv` is required to run it.

## Project contents

- `Hospital_OPD_Time_Series_Analysis.ipynb`: the complete analysis. It covers data cleaning, EDA, stationarity tests, AIC-based parameter selection, model comparison, forecasts and interpretation.
- `data/opd_data.csv`: the source dataset.
- `outputs/`: plots, tables and forecast files. The notebook creates this folder when it runs.
- `presentations/Hospital_OPD_Time_Series_Analysis_Final.pptx`: the final presentation.
- `report/Hospital_OPD_Final_Report.docx`: the final project report.

## Setup

Python 3.10 or later is recommended. Install the packages:

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn statsmodels
pip install prophet xgboost torch darts pytorch-lightning autots tsfresh arch
```

The second line installs the advanced and supplemental libraries. If any of them is missing, its cell prints an install message and skips that model instead of stopping the notebook.

## Run the notebook

1. Open a terminal in this project folder and start Jupyter with `jupyter notebook`.
2. Open `Hospital_OPD_Time_Series_Analysis.ipynb`.
3. Choose **Run All**.

A full run takes about 10–15 minutes on a laptop CPU. AutoTS and the Temporal Fusion Transformer take the longest.

## What the notebook covers

| Requirement | Where |
|---|---|
| EDA, cleaning, decomposition | Sections 3–7 |
| Hourly series (3,650 observations, at least the 500 required) | Sections 5b and 10b |
| Stationarity (ADF/KPSS, ACF/PACF) | Section 8 |
| Parameter selection and justification (AIC, training data only) | Section 9b |
| AR, MA, ARMA, ARIMA, SARIMA, Holt-Winters, ARIMAX | Section 10 |
| Model assumption checks (Ljung-Box, residual diagnostics) | Section 10a |
| VAR / VARIMA (departments) | Section 11 |
| 30-day forecast | Section 12 |
| TSFresh, Prophet, Darts, AutoTS (all scored on the common holdout) | Sections 13–14 |
| XGBoost, LSTM, GRU, Temporal Fusion Transformer (tuned) | Section 14 |
| ARCH/GARCH volatility test | Section 14b |
| Final comparison table, plots and insights | Section 15 |
| Residual diagnostics and run report | Sections 16–17 |

## Evaluation and assumptions

- The data covers 2024-04-19 to 2025-04-18 for six departments. `patient_count` is summed into 365 daily totals and 3,650 clinic-hour totals.
- Every model is scored on the same holdout: the last 20% of dates (73 days), using MAE, RMSE and MAPE.
- Model orders and hyper-parameters are chosen using training data only.
- The `is_holiday` flag is identical to Sunday. ARIMAX therefore uses weekday dummy variables instead.
- Dates with no records would be treated as zero visits; this dataset has no missing dates.
- Exact duplicate rows are flagged but not deleted.
