# Hospital OPD Time Series Analysis

This project analyzes historical outpatient department (OPD) demand and compares time-series forecasting models. The teacher-facing deliverable is the Jupyter notebook; the CSV in `data/` is required to run it.

## Project contents

- `Hospital_OPD_Time_Series_Analysis.ipynb` — complete analysis, model comparison, plots, forecasts, and interpretation prompts.
- `data/opd_data.csv` — source dataset used by the notebook.
- `outputs/` — created by the notebook when it is run; contains plots, tables, and forecast files.

## Run the notebook

1. Install Python and Jupyter Notebook or JupyterLab.
2. Install the core packages:

   ```bash
   pip install pandas numpy matplotlib seaborn scipy scikit-learn statsmodels
   ```

3. Open a terminal in this project folder and start Jupyter:

   ```bash
   jupyter notebook
   ```

4. Open `Hospital_OPD_Time_Series_Analysis.ipynb` and choose **Run All**.

The notebook expects `data/opd_data.csv` relative to the project folder. Run cells from top to bottom.

## Analysis and deliverables

The notebook covers data cleaning and quality checks, daily aggregation, EDA, stationarity checks, and chronological holdout evaluation using MAE, RMSE, and MAPE. It compares naive baselines with AR, MA, ARMA, ARIMA, SARIMA, Holt-Winters, and holiday-based ARIMAX. It also includes department-level VAR and VARIMA workflows, a 30-day forecast, and a domain interpretation section.

The supplemental requirements are addressed with TSFresh feature extraction, Prophet, Darts, and AutoTS. TSFresh, Prophet, and Darts run only when their packages are available. AutoTS is included as a separate automatic model search. Optional package installation instructions appear in the relevant notebook cells.

## Dataset and assumptions

The supplied dataset contains 52,343 rows covering 2024-04-19 through 2025-04-18, across six departments. `patient_count` is summed by date and department, creating 365 daily observations. Dates with no records are treated as zero visits; confirm this assumption against the data source. Exact duplicate rows are reported for review and are not deleted automatically.

The last 20% of dates form the test period. Model forecasts are compared on this chronological holdout. The holiday flag is used as an external regressor for ARIMAX during historical holdout evaluation; it is not assumed to be available for the separate future forecast.

## Presentation reminder

Before presenting, run all notebook cells and review the generated metrics and plots. Complete the interpretation prompts using the actual run results. If VAR or VARIMA reports a fitting/convergence failure, state that clearly rather than presenting it as a successful result.
