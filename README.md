# 🔎 KYC/KYB Entity Risk Scoring Engine

> **End-to-end KYC/KYB due diligence platform** that generates synthetic business entity data, applies multi-dimensional risk screening, and scores entities using a Gradient Boosting ML model — visualised in a professional compliance dashboard.

---

## 📌 Project Overview

This project simulates a **Know Your Customer / Know Your Business (KYC/KYB)** onboarding and monitoring system used by banks, fintechs, and payment platforms. It models the full due diligence lifecycle — from entity data collection and watchlist screening to ML-powered risk scoring and dashboard reporting.

**Relevance:** Directly mirrors KYB workflows at Tazapay (cross-border payments KYB), Deloitte USI (compliance advisory), Oracle FCCM, and BFSI onboarding teams.

---

## 🏗️ Project Structure

```
kyc-kyb-risk-engine/
│
├── generate_entities.py      # Synthetic entity generator (1,000 business entities)
├── train_model.py            # Gradient Boosting + Random Forest ML pipeline
├── kyb_dashboard.html        # Interactive KYB risk dashboard (Chart.js)
│
├── entities.csv              # Raw synthetic entity dataset
├── entities_scored.csv       # Enriched dataset with ML risk scores & tiers
├── model_results.json        # Metrics, feature importances, confusion matrix
│
└── README.md
```

---

## 🚨 KYB Risk Factors Modelled

| Risk Category | Indicators Modelled |
|---|---|
| **UBO Opacity** | Undisclosed UBOs, PEP match, sanctions against beneficial owners |
| **Jurisdiction Risk** | Offshore incorporation (BVI, Cayman, Panama, Seychelles, etc.) |
| **Sector Risk** | Cryptocurrency, Arms & Defense, Gambling, Oil & Gas Trading, Mining |
| **Corporate Structure** | Shell company flag, complex layering, subsidiary count, layering depth |
| **Watchlist Screening** | World-Check hits, OFAC/UN/EU sanctions match |
| **Adverse Media** | Negative news flag + count of adverse media articles |
| **Documentation** | Incomplete KYC documents — missing UBO declaration, registration proof |
| **Director Risk** | Multi-directorship across 5+ entities, dormant company registration |
| **Financial Opacity** | Gap between declared income and annual turnover |

---

## 🤖 ML Model

**Primary:** Gradient Boosting Classifier (300 estimators, learning rate 0.05)  
**Baseline:** Random Forest Classifier (200 estimators)

### Engineered Features

| Feature | Description | Importance |
|---|---|---|
| UBO Opacity Score | Composite of non-disclosure + PEP + sanctions | 28.1% |
| World-Check Hit | Watchlist screening match | 19.4% |
| Alert Signal Count | Sum of all binary red flags | 15.2% |
| Structure Complexity | Shell + layering + subsidiaries composite | 12.0% |
| Jurisdiction Risk | FATF high-risk / offshore encoding | 8.9% |
| Sector Risk | High-risk industry encoding | 6.1% |
| Financial Opacity | Log of income vs. turnover gap | 3.9% |
| Adverse Media | Negative news indicator | 3.1% |
| Docs Complete | Document completeness flag | 2.0% |
| Registration Age | Company age in years | 1.1% |

### Performance Metrics

| Metric | Gradient Boosting | Random Forest |
|---|---|---|
| Accuracy | 1.00 | 1.00 |
| Precision | 1.00 | 1.00 |
| Recall | 1.00 | 1.00 |
| F1 Score | 1.00 | 1.00 |
| ROC-AUC | 1.00 | 1.00 |
| 5-Fold CV AUC | 1.00 ± 0.00 | — |

> ⚠️ Perfect scores are expected on synthetic data. In production, KYB models typically achieve AUC ~0.78–0.88 depending on data quality and label noise.

---

## 📊 Dashboard Features

- **Live IST clock** with active screening status
- **6 KPI cards** — Total entities, high-risk alerts, World-Check hits, PEP flags, shell companies, model AUC
- **Alerts by Sector** — horizontal bar chart distinguishing high-risk vs standard sectors
- **Jurisdiction Risk Distribution** — doughnut chart (Offshore / Medium / Low)
- **Entity Risk Tier Split** — High / Medium / Low count
- **KYB Red-Flag Summary** — 8 flag categories with entity counts
- **ML Model Performance** — 6 metrics + feature importance bars
- **KYB Alert Queue Table** — 205 high-risk entities, filterable by jurisdiction risk, sector, flag type, and search

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Data Generation | Python · Pandas · NumPy |
| ML Model | scikit-learn (GradientBoostingClassifier, RandomForestClassifier) |
| Feature Engineering | Composite scores, log transforms, label encoding |
| Cross-Validation | StratifiedKFold (5-fold) |
| Visualization | Chart.js · HTML/CSS · Vanilla JS |
| AML Domain | KYC/KYB · Sanctions Screening · World-Check logic · UBO due diligence |

---

## ▶️ How to Run

```bash
# 1. Clone the repo
git clone https://github.com/yourusername/kyc-kyb-risk-engine.git
cd kyc-kyb-risk-engine

# 2. Install dependencies
pip install pandas numpy scikit-learn

# 3. Generate synthetic entities
python generate_entities.py

# 4. Train the ML model
python train_model.py

# 5. Open the dashboard
open kyb_dashboard.html
```
##### [Live Demo](https://ukishore33.github.io/KYC-KYB-Entity-Risk-Scoring-Engine/sanctions_dashboard.html)
---

## 👤 Author

**Kishore U.**  
AML/KYC Compliance Analyst | Data Analytics  
📱 6303308133 | Belagavi, Karnataka | Immediate Joiner  
🔗 [LinkedIn] · [GitHub]

**Skills demonstrated:** KYC/KYB · UBO Due Diligence · Sanctions Screening · World-Check · Python · scikit-learn · Gradient Boosting · SQL · Data Visualization · Financial Crime Compliance

---

## 📜 Disclaimer

All data is **100% synthetic** — generated programmatically with no real entity, person, or financial data. Built purely for portfolio demonstration.
