## Project plan
See the [project specification](docs_project_spec.md).

## Modeling and Evaluation

This project estimates daily bike rentals using calendar information
and recorded same-day weather.

Data was split chronologically:
- Training: January–December 2011 (365 days).
- Validation: January–June 2012 (182 days).
- Test: July–December 2012 (184 days).

The columns `casual` and `registered` were excluded because their sum
equals the target, `cnt`, which would cause target leakage.

### Model Selection

Models were compared using validation MAE as the primary metric.

| Model | Validation MAE | Validation RMSE |
|---|---:|---:|
| Training-mean baseline | 2052.44 | 2449.89 |
| Linear regression | 2064.21 | 2248.70 |
| Linear regression with elapsed-time feature | 3583.13 | 3701.48 |
| Random forest | 1925.90 | 2091.11 |

The random forest achieved the lowest validation MAE. It was then
refitted on the combined training and validation data without changing
its features or settings.

### Final Test Results

| Model | Test MAE | Test RMSE |
|---|---:|---:|
| Development-mean baseline | 2452.64 | 2694.30 |
| Final random forest | 2115.43 | 2256.88 |

The random forest reduced test MAE by approximately 13.7% compared
with the baseline. Its MAE corresponds to an average absolute error
of approximately 2,115 rentals per day.

The final test results were not used for further model tuning.

### Limitations

- Recorded same-day weather makes this retrospective demand estimation,
  not advance forecasting.
- The historical dataset may not represent current rental behavior.
- Prediction errors remain substantial despite improvement over the baseline.

### Notebook

See [the analysis notebook](01_data_exploration.ipynb) for data checks,
preprocessing, model comparisons, and final evaluation.

## How to Run

1. Download `01_data_exploration.ipynb` from this repository.
2. Open the notebook in Google Colab.
3. Download the Bike Sharing dataset from:
   https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset
4. Extract the downloaded ZIP file and locate `day.csv`.
5. In Colab, open the Files sidebar and upload `day.csv`.
6. Ensure the notebook's data-loading cell reads the uploaded file:
   `pd.read_csv("day.csv")`
7. Run all notebook cells from top to bottom.

### Dependencies

The notebook uses Python with:
- pandas
- matplotlib
- scikit-learn

### Expected Outputs

- Data-quality checks and chronological data splits.
- Validation comparisons between baseline, linear, and random forest models.
- Final test MAE and RMSE.
- A plot comparing actual and predicted rentals.

The notebook uses recorded same-day weather to estimate daily demand;
it does not forecast future demand using weather forecasts.
