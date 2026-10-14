# Credit Card Fraud Detection: Results

**Data:** 284,807 transactions, 492 fraud cases (0.173%).

**Method:** time-based split (60% train, 20% validation for threshold tuning, 20% test on the latest transactions). Features: V1 to V28, log transaction amount, and hour of day. Thresholds chosen on validation only.

**Why not accuracy:** a model that flags nothing scores 99.87% accuracy while catching zero fraud.

## Test-period metrics

| model | threshold_rule | pr_auc | roc_auc | precision | recall | false_positive_rate | alerts_per_10k | accuracy |
|---|---|---|---|---|---|---|---|---|
| Logistic Regression | max F1 on validation | 0.7484 | 0.9833 | 0.9615 | 0.6667 | 3.5e-05 | 9.1 | 0.9995 |
| Logistic Regression | precision >= 90% on validation | 0.7484 | 0.9833 | 0.9273 | 0.68 | 7e-05 | 9.7 | 0.9995 |
| Gradient Boosting | max F1 on validation | 0.7494 | 0.9548 | 0.9091 | 0.6667 | 8.8e-05 | 9.7 | 0.9995 |
| Gradient Boosting | precision >= 90% on validation | 0.7494 | 0.9548 | 0.9107 | 0.68 | 8.8e-05 | 9.8 | 0.9995 |
| Isolation Forest (unsupervised) | max F1 on validation | 0.051 | 0.9542 | 0.071 | 0.32 | 0.00552 | 59.3 | 0.9936 |

**Best model by PR-AUC:** Gradient Boosting (max F1 on validation): PR-AUC 0.7494, precision 91%, recall 67%, false positive rate 0.009%.
