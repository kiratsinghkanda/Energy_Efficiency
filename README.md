# Energy Efficiency — ENB2012 Analysis

This repository contains an exploratory and modeling notebook for the ENB2012 Energy Efficiency dataset.

## Contents

- `ENB2012_data.csv` — the dataset used for modelling (two target variables: `Y1`, `Y2`).
- `Energy_Efficiency.ipynb` — the primary Jupyter Notebook with EDA, preprocessing, and models (Linear Regression, Decision Tree, Random Forest).
- `requirement.txt` — (project dependencies). Install these before running the notebook.
- `LICENSE.txt` — project license.

## Overview

The notebook standardizes features, performs basic EDA (boxplots, skewness), and trains three baseline regressors:

- Linear Regression (multi-output)
- Decision Tree Regressor
- Random Forest Regressor

It prints labeled evaluation metrics (MSE, MAE, RMSE, R2) for each model.

## Quick start (Windows PowerShell)

1. Create and activate a virtual environment (recommended):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install dependencies:

```powershell
pip install -r requirement.txt
```

3. Launch Jupyter and open the notebook:

```powershell
jupyter notebook Energy_Efficiency.ipynb
```

4. Run cells top-to-bottom. The notebook prints metrics for each model and includes notes about scaling and data leakage.

## Notes & recommendations

- Scaling currently runs on the whole dataset for simplicity. For production or stricter evaluation, fit the scaler on the training set only and apply it to the test set to avoid data leakage. Consider using `sklearn.pipeline.Pipeline` and `ColumnTransformer`.

- Pairplots can be slow; you may want to switch to a sampled subset for quick visual checks (e.g., `data.sample(200)`).

- The notebook trains models on both targets together (multi-output). If you prefer separate models per target, split `Y1` and `Y2` and train independently.

- Consider adding cross-validation, hyperparameter search (GridSearchCV or RandomizedSearchCV), and a small comparison table of metrics for repeatable model selection.

## Next steps (optional)

- Move scaling into a pipeline and add feature importances/partial dependence plots.
- Add a results/metrics DataFrame comparing models and persist best model with `joblib`.
- Add unit tests for preprocessing/transforms.

## License

See `LICENSE.txt` for licensing details.

