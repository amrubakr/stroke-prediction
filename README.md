# Stroke Prediction

**Data:** [Stroke Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset) by fedesoriano

## Versions

### v1 — First attempt
`stroke-prediction-eda-balancing.ipynb`

EDA, encoding, RobustScaler, and comparing three ways to handle class imbalance: RandomUnderSampler, RandomOverSampler and SMOTE.

### v2 — Second attempt after deeper study
`stroke-prediction-v2-after-deeper-study.ipynb` · [View on Kaggle](https://www.kaggle.com/code/amrbakr95/stroke-prediction-eda-outliers-leak-free-smote)

What changed after studying more:
- **Outliers:** the high glucose values are real (diabetes), not mistakes. People with glucose above 160 had 13% stroke vs 4.9% in all the data, so I kept them and used `log1p` instead of removing them.
- **SMOTENC instead of SMOTE:** SMOTE creates values like 0.4 in categorical columns. SMOTENC keeps categories as real categories.
- **Leak-free Pipeline:** Scaling → SMOTENC → Encoding inside an `imblearn` Pipeline after the split, so cross validation does not leak data.

## Key Findings
- Age is the strongest factor: stroke rate goes from almost 0% under 40 to 19.8% above 80.
- Heart disease (17%) and hypertension (13.3%) make the stroke rate 3 to 4 times higher.
- Higher glucose means higher stroke rate (12.9% above 200).
- In this data, gender and residence type make almost no difference.
