# Forecasting U.S. GDP Growth with PCA and Shrinkage Methods

This project builds a pseudo out-of-sample forecasting system for U.S. real GDP growth using public macroeconomic data from FRED. It compares simple time-series benchmarks against higher-dimensional forecasting models that use Principal Component Analysis, Ridge Regression, and Lasso Regression.

The repository is structured as a portfolio-ready version of my Economics 424 final project, with the notebook, reproducible Python script, cleaned data, saved model outputs, and final report in one place.

## Project Highlights

- Forecasted quarterly U.S. real GDP growth using `GDPC1` from FRED and a panel of 20+ macroeconomic predictors.
- Compared six forecasting models: Naive Mean, Random Walk, Random Walk with Drift, PCA Diffusion Index, Ridge Regression, and Lasso Regression.
- Evaluated one-quarter-ahead and four-quarter-ahead forecasts using MSFE, MAE, and relative MSFE against the Random Walk benchmark.
- Used expanding-window pseudo out-of-sample evaluation to mimic real-time forecasting and reduce look-ahead bias.
- Applied stationarity transformations, standardization, PCA factor extraction, and regularized regression with Python, pandas, statsmodels, and scikit-learn.

## Key Result

Big-data models improved substantially over the Random Walk benchmark at both forecast horizons, while the Naive Mean remained the strongest short-horizon benchmark.

| Horizon | Model | MSFE | MAE | Relative MSFE vs RW |
|---|---:|---:|---:|---:|
| h=1 | Naive Mean | 3.05 | 0.69 | 0.39 |
| h=1 | Random Walk | 7.77 | 1.06 | 1.00 |
| h=1 | RW with Drift | 7.82 | 1.06 | 1.01 |
| h=1 | Diffusion Index | 5.62 | 0.85 | 0.72 |
| h=1 | Ridge | 7.88 | 0.95 | 1.01 |
| h=1 | Lasso | 9.73 | 0.94 | 1.25 |
| h=4 | Naive Mean | 3.03 | 0.68 | 0.47 |
| h=4 | Random Walk | 6.43 | 1.23 | 1.00 |
| h=4 | RW with Drift | 6.62 | 1.25 | 1.03 |
| h=4 | Diffusion Index | 3.15 | 0.78 | 0.49 |
| h=4 | Ridge | 3.03 | 0.69 | 0.47 |
| h=4 | Lasso | 3.05 | 0.70 | 0.47 |

## Visual Summary

### Real GDP Growth

![U.S. real GDP quarterly growth](figures/01_gdp_growth.png)

### PCA Scree Plot

![PCA scree plot](figures/03_scree.png)

### Relative MSFE by Model

![Relative MSFE versus Random Walk](figures/06_relative_msfe.png)

## Repository Structure

```text
.
|-- data/
|   |-- panel_cleaned.csv
|-- figures/
|   |-- 01_gdp_growth.png
|   |-- 03_scree.png
|   |-- 06_relative_msfe.png
|-- notebooks/
|   |-- FinalProject_GDP.ipynb
|-- reports/
|   |-- Final_Project_Econ_424.docx
|-- results/
|   |-- results_table.csv
|   |-- forecasts_h1.csv
|   |-- forecasts_h4.csv
|   |-- errors_h1.csv
|   |-- errors_h4.csv
|   |-- summary.json
|-- src/
|   |-- run_forecasting_experiment.py
```

## How to Run

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the forecasting pipeline:

```bash
python src/run_forecasting_experiment.py
```

Open the project notebook:

```bash
jupyter notebook notebooks/FinalProject_GDP.ipynb
```

The script downloads public macroeconomic data from FRED through `pandas-datareader`, rebuilds the forecasting experiment, and writes updated outputs to `data/`, `results/`, and `figures/`.

## Methods

- Data source: FRED macroeconomic time series
- Target: quarterly real GDP growth from `GDPC1`
- Predictors: output, employment, prices, interest rates, money, housing, sentiment, energy, and activity indicators
- Forecast design: expanding-window pseudo out-of-sample forecasting from 2015 onward
- Forecast horizons: `h=1` quarter and `h=4` quarters
- Evaluation metrics: MSFE, MAE, relative MSFE versus Random Walk
- Models: Naive Mean, Random Walk, Random Walk with Drift, PCA Diffusion Index, Ridge Regression, Lasso Regression

## Skills Demonstrated

Python, pandas, NumPy, statsmodels, scikit-learn, time-series forecasting, macroeconomic data analysis, FRED data pipelines, feature engineering, PCA, Ridge Regression, Lasso Regression, expanding-window validation, model evaluation, data visualization, econometrics.
