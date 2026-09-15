# Contributing

Thanks for your interest in improving this pipeline!

## How to contribute

1. Fork the repository and create a branch: `git checkout -b feat/my-improvement`.
2. Keep changes focused — one improvement per pull request.
3. Test the workflow manually via **Actions -> ev-ultra-v3 -> Run workflow** before opening a PR.
4. Open a pull request describing:
   - What you changed (features, CV setup, models, encodings).
   - The resulting CV ROC-AUC vs. the current baseline.
   - Any trade-offs (runtime, overfitting risk).

## Guidelines

- **Reproducibility first**: fixed seeds, deterministic folds, no leakage from test data.
- **No hardcoded credentials** — Kaggle auth must stay in repository secrets.
- **Runtime budget**: keep the workflow under the 360-minute timeout on standard runners.
- **Model changes** should report fold-level scores, not just the aggregate.

## Reporting issues

Open an issue with the workflow run link, the failing step, and the relevant log excerpt.
