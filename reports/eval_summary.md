\# Evaluation Summary - Week 3



\## What you trained

\- Model family: Logistic Regression (classification)

\- Preprocessing: Pipeline with one-hot encoding for country + numeric features

\- Key hyperparameters: seed=42, test\_size=0.2, threshold=0.5



\## Results

\- Baseline metrics (holdout): accuracy=0.8, precision=0.0, recall=0.0, f1=0.0, roc\_auc=0.5

\- Model metrics (holdout): accuracy=1.0, precision=1.0, recall=1.0, f1=1.0, roc\_auc=1.0

\- Confidence intervals (optional): roc\_auc CI = \[1.0, 1.0]



\## Error analysis

\- Worst cases: not meaningful on this tiny holdout set (only 10 rows).

\- Any obvious leakage? No direct leakage in inference because the target column is forbidden by schema validation.

\- Next data fixes to try: use a larger and more realistic dataset; re-check class balance; evaluate stability with cross-validation.



\## Recommendation

Do not ship this as a real production model yet because the dataset is synthetic and very small, but the end-to-end training + prediction system is working as a baseline.



