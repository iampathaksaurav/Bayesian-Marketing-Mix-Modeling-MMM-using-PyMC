# Bayesian-Marketing-Mix-Modeling-MMM-using-PyMC
End-to-end Bayesian Marketing Mix Modeling (MMM) using PyMC with ROI analysis, response curves, scenario simulation, and forecasting.

## Overview

This project implements an end-to-end **Bayesian Marketing Mix Model (MMM)** using PyMC to measure the impact of marketing channels on sales. The model combines statistical rigor with business interpretability to estimate channel performance, optimize budgets, and forecast future sales.

The framework integrates key marketing concepts such as **adstock (carryover effects)** and **saturation (diminishing returns)**, enabling realistic modeling of marketing impact.

---

## Objective

The goal of this project is to answer key business questions:

- Which marketing channels drive sales?
- What is the ROI of each channel?
- Where should marketing spend be increased or reduced?
- What is the expected impact of budget changes?

---

## Data

The dataset consists of weekly records including:

- Sales / Revenue (`Value`)
- Media impressions across channels (Google, Meta, TikTok)
- Marketing spend
- Non-paid channels (Direct, Organic, Email, Referral)
- Pricing and promotions (`Avg Price`, `Discount`)
- Time variable (`WEEK`)

---

## Methodology

### 1. Data Preprocessing
- Standardized all variables using scaling
- Maintained time order (no random splitting)
- Train-test split for validation

---

### 2. Feature Engineering

**Adstock Transformation**
Captures lagged effect of advertising: Adstock_t = x_t + θ * Adstock_{t-1}

**Saturation (Hill Function)**
Models diminishing returns of media exposure: f(x) = x^α / (x^α + γ^α)

### 3. Bayesian Model (PyMC)

Sales are modeled as a function of:
- Media variables (transformed impressions)
- Control variables (price, discount, organic traffic)
- Noise

Key aspects:
- Media effects constrained to be positive
- Parameters estimated via MCMC (NUTS sampler)
- Outputs are probabilistic (uncertainty-aware)

---

## Model Validation

Model performance evaluated using:
- **R²** (goodness of fit)
- **MAPE** (accuracy)
- **Durbin–Watson** (autocorrelation)
- Actual vs predicted visualization

---

## Key Outputs

- **Channel Contribution**: Revenue driven by each channel
- **Incremental Value**: Absolute impact in monetary terms
- **ROI**: Efficiency of each channel
- **Effectiveness**: Share of total contribution
- **Response Curves**: Identify saturation and diminishing returns


## Business Insights

The model enables:
- Identification of high-performing channels
- Recognition of saturated investments
- Data-driven budget allocation
- Understanding of promotion and pricing effects

---

## Tech Stack

- Python
- PyMC (Bayesian modeling)
- NumPy, Pandas
- Matplotlib, ArviZ
- Scikit-learn

---

## Conclusion

This project demonstrates a complete **Bayesian MMM pipeline**, transforming marketing data into actionable insights for optimizing spend, improving ROI, and supporting strategic decision-making.

