# Explainable Deep Learning for Retail Demand Forecasting with External Indicators

Master's practicum project — Dublin City University, School of Computing.
**Authors:** Sahil Ichake, Swaraj Sonawane

---

## Overview

This project forecasts weekly retail demand for Nike's U.S. business and uses the
forecast to drive an inventory-stocking decision. A **Temporal Fusion Transformer (TFT)**
is trained on five years of sales data enriched with macroeconomic, financial, and trade
indicators from the U.S. **FRED** service (including a region-matched consumer price index).
The model is compared against a seasonal-naive benchmark and a SARIMAX baseline, its
predictions are made interpretable through the TFT's variable-selection mechanism, and its
**quantile (probabilistic) output** is used to size safety stock in a periodic-review
order-up-to inventory policy.

A central question is whether **external factors** — macroeconomic, financial, and trade
signals such as consumer prices, exchange rates, retail spending, and imports — improve
demand forecasts beyond a retailer's own sales history. The results show that these external
indicators add value when they are matched to the right granularity: a **region-matched CPI**
lifts accuracy where national aggregates cannot, while the TFT's variable-selection weights
reveal which external factors the model actually relies on.

**Headline results (weekly, region-wise test set):**

| Model | RMSE | MAE | WMAPE | R² |
|---|---|---|---|---|
| Seasonal-naive | 26,744 | 19,564 | 43.6% | −0.65 |
| SARIMAX (baseline) | 18,199 | 13,275 | 29.6% | 0.24 |
| **TFT (proposed)** | **12,281** | **7,539** | **18.1%** | **0.49** |

- The TFT roughly **halves** the seasonal-naive error and cuts SARIMAX error by **~11 WMAPE points**; it is the only model with a positive R².
- Adding **region-matched CPI** improved WMAPE from ~21.6% to **18.1%**.
- The **forecast-driven inventory policy** met a **95% service level** while using **~27% less safety stock** than a policy sized from historical variability.

---
