# AISE 4010 Course Project — Group 1

Day-ahead forecasting of Germany's hourly electricity load with the Open Power System Data time series package. All modelling, analysis and figures live in one notebook, `AISE4010_Project_Group01.ipynb`.

## Problem

Every hour, forecast the next 24 hours of national electricity load (MW) from the previous 168 hours of load and two calendar features (hour of day, day of week). Models are compared under one protocol: chronological 60/20/20 split, the same windows and the same metrics (MAE, RMSE, MAPE).

## Dataset

- Source: Open Power System Data, Time series package version 2020-10-06, https://doi.org/10.25832/time_series/2020-10-06
- File: `time_series_60min_singleindex.csv` (about 124 MB, not committed)
- Target: `DE_load_actual_entsoe_transparency` in MW, hourly, 2015-01-01 to 2020-09-30 (UTC)

## Setup

```bash
pip install -r requirements.txt
```

On Google Colab, skip the install; the preinstalled TensorFlow, scikit-learn and pandas are enough. A GPU is not needed.

## Data

The notebook downloads the CSV into `data/` on its first run. See `data/README.md` to place it by hand.

## Run Order

1. Open `AISE4010_Project_Group01.ipynb`.
2. Restart the kernel and run all cells top to bottom.

Expected runtime: about 5–10 minutes on a laptop CPU, most of it model training in Sections 7–11. The smoke test in Section 12 reloads the saved model and checks its forecasts in a few seconds.

## Outputs

`artifacts/` holds the selected model (`best_model.keras`), its configuration and scaler statistics (`final_config.json`), the grid search table and the test comparison table.

## Checkpoints

| Stage | Lab | Commit |
|---|---|---|
| Stage 1: baselines, MLP, CNN, grid search | Lab 6 | this commit (added after the demo, when the group repo was created) |
