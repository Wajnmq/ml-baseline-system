# Week 3 — Ship-Ready Baseline ML System  
**Train • Evaluate • Predict (Reproducible & Offline-First)**

This project implements a complete, end-to-end **baseline machine learning system**:
from a feature table → training → evaluation → batch prediction,  
with reproducibility, versioned artifacts, and clear documentation.

It is designed as a **portfolio-ready reference implementation** for real-world ML workflows.

---

## ✨ Key Features

- ✅ Offline-first (no external services or APIs)
- ✅ Reproducible runs (run metadata + environment capture)
- ✅ Versioned model artifacts
- ✅ Schema-validated batch prediction
- ✅ Clear separation between training, evaluation, and inference
- ✅ Model Card + Evaluation Summary for responsible ML reporting

---

## 📁 Repository Structure (High-Level)

```
src/                # Core ML logic (train / predict / evaluation)
data/
  processed/        # Feature tables (CSV / Parquet)
models/
  runs/             # Versioned training runs (models + metrics + schema)
  registry/         # Pointer to latest run
reports/
  model_card.md     # What the model does, limits, metrics
  eval_summary.md   # Executive evaluation summary
outputs/            # Batch prediction outputs
tests/              # Automated tests
```

---

## 🚀 Quickstart

### 1) Setup environment
```bash
uv sync
```

---

### 2) Create sample data (demo only)
```bash
uv run ml-baseline make-sample-data
```

Creates a small deterministic feature table:
- `data/processed/features.csv`
- `data/processed/features.parquet` (if supported)

---

### 3) Train a baseline model
```bash
uv run ml-baseline train --target is_high_value
```

This will:
- split data into train / holdout
- train a baseline classifier
- evaluate performance
- save all artifacts under a unique run id

Artifacts are written to:
- `models/runs/<run_id>/`
- `models/registry/latest.txt` → points to the most recent run

---

### 4) Batch predict (safe inference)

First, read the latest run id:
```bash
$RID=$(cat models/registry/latest.txt)
```

Then run prediction on a **schema-safe input** (no target column):
```bash
uv run ml-baseline predict \
  --run latest \
  --input "models/runs/$RID/tables/holdout_input.csv" \
  --output outputs/preds.csv
```

Output:
- `outputs/preds.csv` (scores + predictions)

---

### 5) Run tests
```bash
uv run pytest
```

---

## 📊 Model Reporting

This repository includes two formal ML reports:

### 1) Model Card (`reports/model_card.md`)
Documents:
- problem definition
- dataset + hash
- training split
- baseline vs model metrics
- limitations and monitoring sketch
- full reproducibility details

### 2) Evaluation Summary (`reports/eval_summary.md`)
Executive-level summary covering:
- what was trained
- performance results
- error analysis
- ship / no-ship recommendation

These reports make the project suitable for:
- technical reviews
- ML audits
- portfolio presentation

---

## 🔁 Reproducibility Guarantees

Each run captures:
- dataset hash (sha256)
- configuration (target, split, seed)
- evaluation metrics
- input schema
- trained model
- Python environment (`pip_freeze.txt`)

Any run can be reloaded and re-used deterministically.

---

## 🧭 Notes

- This is a **baseline system**, not a production-ready model.
- The dataset is small and synthetic (for demonstration only).
- The focus is on **correct ML system design**, not raw performance.

See `architecture.md` for design rationale and stretch goals.
