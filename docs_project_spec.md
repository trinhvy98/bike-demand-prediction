# Bike Rental Demand Prediction — Project Specification

## Problem
Estimate total daily bike rentals from calendar and weather information.

## Portfolio goal
Demonstrate data preparation, leakage prevention, regression modeling,
chronological evaluation, and clear communication of results.

## Dataset
Source: UCI Machine Learning Repository — Bike Sharing
URL: https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset
File: day.csv
License: CC BY 4.0
Citation: Fanaee-T, H. (2013). Bike Sharing [Dataset].
https://doi.org/10.24432/C5W894

## Target
cnt — total daily bike rentals.

## Initial candidate predictors
season, mnth, weekday, holiday, workingday,
weathersit, temp, hum, windspeed.

## Excluded columns
- casual and registered: components of the target; including them causes leakage.
- instant: row identifier.
- dteday: retained for chronological splitting, not directly used as a predictor.

## Evaluation plan
- Training: January–December 2011.
- Validation: January–June 2012.
- Final test: July–December 2012.
- Keep final test data out of model selection and tuning.

## Planned models
1. Training-set mean baseline.
2. Linear regression.
3. Random forest regression.

## Planned metrics
- MAE: primary metric, expressed in daily rentals.
- RMSE: secondary metric emphasizing larger errors.

## Limitations
Recorded same-day weather makes this a retrospective demand-estimation
project. Advance forecasting would require weather forecasts available
at prediction time.

The historical data may not represent current travel behavior.

## Current status
Planning stage. No models trained or results reported.
