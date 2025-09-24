# Student-Performance-Bayesian
Bayesian Modeling of Student Test Scores (PyMC + ArviZ)
# Student-Performance-Bayesian
Bayesian Modeling of Student Test Scores (PyMC + ArviZ)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/venkatanadikatla/Student-Performance-Bayesian/blob/main/notebooks/01_bayesian_intro.ipynb)

> An interview-ready walkthrough of Bayesian workflow on a small student-scores dataset:
> prior choice, posterior inference with MCMC, model evaluation, and posterior predictive checks.

---

## 🔎 Summary (TL;DR)
- **Goal:** Quantify uncertainty in student test scores and demonstrate a clean Bayesian workflow.
- **Data:** 1,000 rows with demographics + scores (`math`, `reading`, `writing`).
- **Models:** PyMC (Normal likelihood with priors on μ, σ); diagnostics with ArviZ.
- **Highlights:** Clear priors, convergence checks (R̂≈1.0), calibrated posterior predictive.
- **Stack:** Python, PyMC 5, ArviZ, NumPy, pandas, Matplotlib.
- **Run it:** Colab badge above or `pip install -r requirements.txt`.

---

## 🎯 Problem & Motivation
Traditional point estimates hide uncertainty. This project shows how Bayesian modeling:
- encodes expert knowledge via **priors**,
- produces **full posterior distributions** for quantities of interest,
- and validates models with **posterior predictive checks**, not just a single metric.

The demo uses student test scores to keep the story simple and visual.

---

## 🧠 Approach
1. **Data prep**  
   - Load `Student.csv` (1000×8): demographics (gender, race/ethnicity, parental education, lunch, test-preparation) and scores.
2. **Modeling**  
   - Likelihood: `score ~ Normal(μ, σ)` per subject (start univariate; extend later).  
   - Priors: `μ ~ Normal(0, 10)`, `σ ~ HalfNormal(10)` (weakly informative).  
   - Inference: `pm.sample(chains=4)`.
3. **Diagnostics & Evaluation**  
   - Convergence: R̂≈1.0, strong bulk/tail ESS.  
   - **ArviZ** trace plots, posterior summaries (HDI), and **Posterior Predictive Checks** (PPC).
4. **Communication**  
   - Visual overlays (observed vs. posterior predictive).  
   - Clear statements of uncertainty (HDI/credible intervals), not just point estimates.

---

## 📈 Results (example run)
*(Numbers will update based on your exact notebook/data slice; shown here match a reference run.)*
- Posterior mean **μ ≈ 4.79**, posterior **σ ≈ 1.84** in the didactic normal example; good mixing, **R̂ ≈ 1.00** for all parameters.
- Posterior predictive closely matches observed score distribution; credible intervals cover held-out quantiles.
- A small **Bayes update toy** (hemophilia carrier example) demonstrates how evidence reduces posterior probability as `n` unaffected XY children increases.

> See `reports/figures/` for trace plots, density overlays, and PPC charts inserted below.

---
