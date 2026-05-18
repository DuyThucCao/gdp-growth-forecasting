# Project Summary

## Research Question

Can higher-dimensional macroeconomic forecasting methods improve U.S. real GDP growth forecasts relative to simple benchmark models?

## Business and Economic Relevance

GDP forecasts are used by policymakers, investors, analysts, and businesses to understand where the economy may be headed. This project tests whether a broad panel of macroeconomic indicators can improve forecast accuracy compared with simple rules such as a historical mean or random walk.

## Data

- Target variable: Real Gross Domestic Product, `GDPC1`, from FRED
- Frequency: quarterly
- Transformation: log-difference growth rate
- Predictor panel: 20+ public macroeconomic indicators from FRED
- Categories: output, labor market, prices, interest rates, money, housing, energy, and sentiment
- Evaluation period: pseudo out-of-sample forecasts from 2015 onward

## Modeling Workflow

1. Download and clean public macroeconomic time series from FRED.
2. Transform predictors to improve stationarity.
3. Aggregate monthly and daily predictors to quarterly frequency.
4. Standardize predictors before PCA and shrinkage models.
5. Estimate six forecasting models with an expanding training window.
6. Evaluate forecast accuracy using MSFE, MAE, and relative MSFE.

## Main Finding

The PCA Diffusion Index, Ridge Regression, and Lasso Regression models generally improved over the Random Walk benchmark, especially at the four-quarter horizon. However, the Naive Mean remained difficult to beat at the short horizon, showing why simple benchmarks are important in macroeconomic forecasting.

## Resume Framing

Built a Python-based macroeconomic forecasting pipeline using FRED data, PCA diffusion indices, Ridge Regression, Lasso Regression, and expanding-window validation to evaluate U.S. GDP growth forecasts across one- and four-quarter horizons.

