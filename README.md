# Smart-Targeting-for-Bank-Term-Deposits
## Goal :-  Train a quick binary model that ranks customers for a term-deposit campaign.


Data + Split

● Load the Kaggle Bank Marketing dataset (link above).

● Exclude leakage: drop duration from features.

● Train/test split: stratified by target y, with a fixed random seed (e.g., 42).

Minimal Preprocessing

● One-hot encode categoricals; keep numerics as is (standardize only if your model needs it).

● Optional: handle rare categories by “other” or let one-hot handle naturally.

Model

● Train one fast classifier (e.g., Logistic Regression with class_weight="balanced", or a small
tree/GBM).
● Use the train set only (no peeking).

## Scoring + Metrics

● Score the test set → predicted probability p = P(y=1).

● Compute:

○ ROC-AUC (and/or PR-AUC; ROC-AUC required).

○ Top-k precision where k = round(0.10 * test_size).

● Build a Top-15 table sorted by p desc with columns:

row_id (or customer_id), predicted_prob.

What to Print (exact)

Print these lines (replace ALL CAPS with your values):

● AUC_ROC: XX.XXX

● TopK_Precision@10%: XX.XXX

● Top 15 table: row_id, predicted_prob (rounded to 3–4 decimals).
Short Notes (final cell, 3–5 lines total)
● Which features mattered: list 2–3 (e.g., top coefficients or importances).
● How we’d deploy daily: batch scoring on latest data, rank by p, contact top N given capacity;
monitor AUC, conversion rate, and drift.
