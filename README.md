<div align="center">

# ev-ultra

**Kaggle Playground Series S6E9 — Electric Vehicle Purchase Prediction**

[![License: MIT](https://img.shields.io/badge/License-MIT-181717?style=flat-square)](LICENSE)
[![Python 3.11](https://img.shields.io/badge/Python-3.11-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org)
[![CI](https://img.shields.io/badge/CI-GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)](.github/workflows/train.yml)
[![Kaggle](https://img.shields.io/badge/Kaggle-Playground_S6E9-20BEFF?style=flat-square&logo=kaggle&logoColor=white)](https://www.kaggle.com/competitions/playground-series-s6e9)

</div>

---

A CI-driven training pipeline for predicting electric vehicle purchases.
The full cycle — data download, feature engineering, cross-validated training,
and submission generation — runs entirely inside **GitHub Actions** via
`workflow_dispatch`, so no local environment is required.

## Pipeline

| Stage | Detail |
| --- | --- |
| Data | `kaggle competitions download -c playground-series-s6e9` |
| Target | `Will_Buy_EV` (binary: Yes / No) |
| Validation | Stratified K-Fold |
| Metric | ROC-AUC |
| Models | LightGBM, XGBoost, CatBoost, HistGradientBoosting |
| Encoding | Target encoding, label encoding, KMeans feature clustering |
| Output | `submission.csv` (uploaded as a workflow artifact) |

## Usage

1. Add repository secrets: `KAGGLE_USERNAME`, `KAGGLE_KEY`.
2. Run manually: **Actions -> ev-ultra-v3 -> Run workflow**.
3. When the run completes, download the `submission.csv` artifact.
4. Submit to [the competition](https://www.kaggle.com/competitions/playground-series-s6e9).

## Repository structure

```
.github/workflows/train.yml   # Full training pipeline (self-contained)
README.md                     # This file
LICENSE                       # MIT
```

> The training script is generated on-the-fly by the workflow, keeping the repo
> minimal and the pipeline self-contained.

## Notes

- Timeout is set to 360 minutes; ensemble stacking runs after per-model folds.
- Kaggle credentials live in repository secrets only — never in code.

## License

Released under the [MIT License](LICENSE).
