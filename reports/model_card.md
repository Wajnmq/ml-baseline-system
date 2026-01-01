# Model Card - Week 3 Baseline

## Problem
- Target: is_high_value
- Unit of analysis: one row = one user
- Decision enabled: identify users who are likely to be high-value customers

## Data
- Feature table: data/processed/features.csv
- Dataset hash (sha256): 6bda418ff35552e80ee9f66ce1a24c434e51ac59d69d0ff099c68ea623456ebe

## Splits
- Holdout: random split, test_size=0.2, seed=42

## Metrics (holdout)
- Baseline:
  - accuracy: 0.8
  - precision: 0.0
  - recall: 0.0
  - f1: 0.0
  - roc_auc: 0.5
- Model:
  - accuracy: 1.0
  - precision: 1.0
  - recall: 1.0
  - f1: 1.0
  - roc_auc: 1.0

## Limitations
- Trained on a small synthetic demo dataset; results are not representative of production performance.
- The target is derived from a fixed threshold on total_amount, which may not generalize.
- Holdout set is small, making metrics potentially unstable.

## Monitoring sketch
- Monitor prediction rate and average score over time.
- Track feature distribution drift for n_orders, avg_amount, and total_amount.
- Alert on schema violations or missing required features at inference time.

## Reproducibility
- Run id: 2026-01-01T16-09-06Z__classification__seed42
- Git commit: 73c31a61aca3ca3f7bb23d8c019576ef29e14926
- Env: models/runs/2026-01-01T16-09-06Z__classification__seed42/env/pip_freeze.txt
- Schema: models/runs/2026-01-01T16-09-06Z__classification__seed42/schema/input_schema.json
