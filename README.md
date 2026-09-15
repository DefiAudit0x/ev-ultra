# ev-ultra

Kaggle **Playground Series S6E9** — *Electric Vehicle Purchase Prediction*.

CI-driven training pipeline: the full cycle (data download, feature engineering,
training, submission) runs inside GitHub Actions via `workflow_dispatch`, so no
local environment is needed.

## Pipeline

| Stage | Detail |
| --- | --- |
| Data | `kaggle competitions download -c playground-series-s6e9` |
| Validation | Stratified K-Fold |
| Metric | ROC-AUC |
| Models | LightGBM, XGBoost, CatBoost, HistGradientBoosting |
| Encoding | Target encoding + label encoding, unsupervised feature clustering |
| Output | `submission.csv` (workflow artifact) |

## Usage

1. Add repository secrets: `KAGGLE_USERNAME`, `KAGGLE_KEY`.
2. Run manually: **Actions -> ev-ultra-v3 -> Run workflow**.
3. Download the submission artifact from the completed run.

## Notes

- Training script is generated on-the-fly by the workflow (no repo copy needed).
- Timeout is set to 360 minutes; ensemble stacking runs after per-model folds.
