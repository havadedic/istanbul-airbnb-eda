# Istanbul Airbnb Price Prediction

## Problem Description

This project predicts the **nightly rental price (TRY)** of Airbnb listings in Istanbul, Turkey. Using publicly available listing data from Inside Airbnb, we explore how factors such as room type, neighbourhood, host activity, and availability influence pricing — helping both hosts set competitive rates and guests assess listing value.

## Dataset Source

**Inside Airbnb — Istanbul, September 2024 Snapshot**  
URL: [http://insideairbnb.com/get-the-data/](http://insideairbnb.com/get-the-data/)  
Direct CSV: `http://data.insideairbnb.com/turkey/marmara/istanbul/2024-09-20/visualisations/listings.csv`

- **Rows:** 5 000 + active listings  
- **Columns:** 18 (including 8+ numeric, 3 categorical, 1 datetime)  
- **Target variable:** `price` — nightly listing price in Turkish Lira (continuous → regression task)

> ⚠️ **Note:** Download `listings.csv` from the link above and place it in the **same folder as the notebook** before running. The `neighbourhood_group` column is empty for Istanbul and has been dropped during cleaning — neighbourhood-level analysis uses the `neighbourhood` column instead.

## Project Structure

```
/
├── README.md
├── p1/
│   ├── p1_eda_istanbul_airbnb.ipynb   ← Problem formulation & EDA
│   └── istanbul_airbnb_cleaned.csv    ← Output of cleaning pipeline (used in P2)
├── p2/
│   └── p2_modelling_istanbul_airbnb.ipynb   ← Feature engineering & model training
└── p3/
    └── p3_optimisation_istanbul_airbnb.ipynb ← Hyperparameter tuning & explainability
```

## How P1, P2, and P3 Connect

| Deliverable | Focus | Outputs |
|---|---|---|
| **P1 — EDA** | Understand the data: distributions, correlations, data quality | Cleaned CSV, insight report, feature shortlist |
| **P2 — Modelling** | Feature engineering, baseline and advanced regression models, evaluation | Trained model, performance metrics (RMSE, MAE, R²) |
| **P3 — Optimisation** | Hyperparameter tuning, SHAP explainability, optional deployment | Best model, feature importance analysis, Streamlit app (optional) |

The cleaned dataset (`istanbul_airbnb_cleaned.csv`) produced at the end of P1 is the direct input to P2, ensuring a consistent, reproducible pipeline across all three deliverables.

## How to Run

```bash
# Clone the repo
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>

# Install dependencies
pip install pandas numpy matplotlib seaborn scipy jupyter

# Launch the notebook
jupyter notebook p1/p1_eda_istanbul_airbnb.ipynb
```

⚠️ **Before running:** make sure `listings.csv` is in the same folder as the notebook (`p1/`).

## Key Findings (P1 Summary)

- **Room type** is the strongest predictor: entire homes cost 2–3× more than private rooms.
- **Location** (district and GPS coordinates) drives significant price variation across Istanbul.
- **Price is right-skewed** — a log transform will be applied in P2 before model training.
- **Reviews and availability** act as occupancy proxies and carry predictive signal.
