# DATA 566 - Final Exam Analysis

**Author:** Sharath Chandra Shankar - 2576017  
**Date:** 2025-12-07

---

## Project Overview

This project analyzes a study on the longitudinal progression of fatigue and weakness in people living with HIV (PLHIV). Data come from a three-month randomized controlled trial with 609 participants. The focus is on:

- **Fatigue (SSC-F):** 4 levels (0 = absent, 1 = mild, 2 = moderate, 3 = severe)  
- **Weakness (SSC-W):** 4 levels (0 = absent, 1 = mild, 2 = moderate, 3 = severe)  
- **Treatment (IC):** 2 levels (0 = control, 1 = intervention)  
- **Time (TIME):** 3 levels (0 = start, 1 = one month, 2 = three months) — disregarded in this analysis

After cleaning, the dataset contains 1343 records, each representing one participant at one time point with corresponding fatigue, weakness, and treatment values.

---

## Objectives

1. Explore the distribution of fatigue and weakness by treatment group.
2. Model fatigue and weakness using:
   - **Ordinal (Proportional Odds) Regression**
   - **Multinomial Logistic Regression**
3. Fit **loglinear models** to investigate associations among fatigue, weakness, and treatment.
4. Compare models using **AIC, BIC, and likelihood ratio tests (G²)**.
5. Identify the best-fitting model for each outcome and interpret results clinically and statistically.

---

## Methods

### Data Preparation
- Data were reshaped into long format with counts per fatigue × weakness × treatment combination.
- Fatigue and weakness variables treated as **ordered factors** for ordinal models.
- Treatment is treated as a categorical factor.

### Exploratory Data Analysis (EDA)
- Bar plots for fatigue and weakness distributions by treatment.
- Heatmaps for joint distributions of fatigue and weakness across treatment groups.

### Regression Modeling
- **Ordinal Regression (POLR)** for ordered outcomes to estimate cumulative odds.
- **Multinomial Regression** for comparison, treating outcomes as unordered categories.
- **Model comparisons** via AIC/BIC and likelihood ratio tests to assess significance of treatment and interactions.

### Weakness Prediction
- Modeled Weakness as a function of Fatigue and Treatment using both ordinal and multinomial models.
- Compared additive and interaction effects.

### Loglinear Modeling
- Poisson regression equivalent to loglinear models for contingency tables.
- Fitted:
  1. **Independence model** (no interactions)
  2. **Two-way interactions** (all pairwise)
  3. **Saturated model** (all main + two-way + three-way interactions)
- Evaluated model fit using **G²**, AIC, and BIC.

---

## Key Findings

1. **Fatigue strongly predicts weakness** across all models.
2. **Treatment alone has minimal effect**; adding treatment to fatigue slightly improves model fit but is not clinically significant.
3. **Interactions between fatigue and treatment are not significant**, suggesting the effect of fatigue on weakness is consistent across treatment groups.
4. **Ordinal regression is preferred** over multinomial due to ordered nature of outcomes and simpler, interpretable odds ratios.
5. **Loglinear models confirm regression results**, with strong associations between fatigue and weakness, but minimal independent treatment effect.

---

## Conclusion

The analysis demonstrates that:

- Fatigue is the primary driver of weakness in PLHIV.
- Intervention has a limited effect on these symptoms in the short-term three-month period.
- Ordinal regression provides a robust, interpretable approach consistent with loglinear modeling, supporting the choice of **ordinal models with fatigue as the main predictor**.

---
