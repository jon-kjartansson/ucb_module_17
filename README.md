# Practical Application 3 | Bank Marketing – Classifier Comparison

**Objective.** Predict likelihood of term deposit subscription from client/campaign data to prioritize outbound calls and improve marketing efficiency.

## Data
- UCI Bank Marketing dataset (Portuguese bank).
- Target: `y` ∈ {no, yes}; positives ~11%.
- Note: `duration` is **leakage** and excluded from realistic pre-call models.

## Methods
- Preprocessing: One-hot encoding (categoricals), scaling (numeric) via `ColumnTransformer` + `Pipeline`.
- Models: Logistic Regression, KNN, Decision Tree, SVM.
- Tuning: `GridSearchCV` with stratified CV, **scoring=ROC-AUC**.
- Metrics: **ROC-AUC**, **PR-AUC**, **Lift** (deciles). Accuracy reported but not used for selection.

## Core Results (Test Set)
- All models: ROC-AUC ≈ 0.65–0.66; Decision Tree had best PR-AUC.
- Lift curves show strong early gains: top deciles capture a disproportionate share of subscribers.
- SVM training time >> others with similar AUC → not preferred operationally.

## Recommendations
- Deploy Logistic Regression (balanced) or pruned Decision Tree.
- Use score-based targeting for top deciles; monitor PR/Lift and adjust threshold to meet capacity/ROI.


## Footnote: I used Gen AI to help format this .md file, and with some of the wording.
