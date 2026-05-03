# Healthcare A/B Testing Framework
### Did a Clinical Intervention Improve Patient Outcomes?

![Python](https://img.shields.io/badge/Python-3.8+-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## Overview

This project implements a complete A/B testing framework applied to a real-world healthcare dataset. It simulates a randomised controlled trial evaluating whether a structured lifestyle intervention programme — combining diet counselling and exercise guidance — significantly reduces diabetes risk indicators in high-risk patients.

The project demonstrates end-to-end statistical thinking: from hypothesis formulation and power analysis through to effect size calculation, confidence intervals, and a structured clinical recommendation.

---

## Business Question

> *Does a structured lifestyle intervention programme significantly reduce glucose levels, BMI, and diabetes diagnosis rate compared to standard care?*

---

## Dataset

**Pima Indians Diabetes Dataset**
- Source: UCI Machine Learning Repository via Kaggle
- 768 female patients of Pima Indian heritage, aged 21+
- 9 features including Glucose, BMI, Insulin, Blood Pressure, and Diabetes Outcome
- Target variable: Outcome (1 = diabetic, 0 = non-diabetic)

---

---

## Methodology

### 1. Data Cleaning
- Identified and replaced biologically impossible zero values in Glucose, BMI, Blood Pressure, Skin Thickness, and Insulin with column medians

### 2. A/B Group Assignment
- Stratified random split: 384 patients per group
- Stratification on Outcome variable ensured identical diabetes rates (34.9%) in both groups

### 3. Hypothesis Formulation
- Three separate hypotheses defined before testing: Glucose, BMI, and Diabetes Outcome
- One-tailed tests at α = 0.05

### 4. Power Analysis
- Minimum sample size to detect a small effect (Cohen's d = 0.2): 310 per group
- Our sample (384 per group) exceeds this threshold
- We have 80% power to detect small, medium, and large effects

### 5. Statistical Testing
- **Independent T-test**: Parametric comparison of group means
- **Mann-Whitney U test**: Non-parametric alternative, robust to skewness
- **Chi-square test**: Binary outcome comparison

### 6. Confidence Intervals
- 95% CIs calculated for mean differences in Glucose and BMI
- 95% CI calculated for difference in diabetes diagnosis rate

### 7. Effect Size
- Cohen's d calculated for continuous variables
- Relative Risk and Absolute Risk Reduction calculated for binary outcome

---

## Results

| Metric | Test | P-value | Effect Size | Decision |
|---|---|---|---|---|
| Glucose | T-test | 0.1878 | d = -0.064 (Negligible) | Fail to reject H₀ |
| Glucose | Mann-Whitney | 0.1178 | d = -0.064 (Negligible) | Fail to reject H₀ |
| BMI | T-test | 0.3140 | d = -0.035 (Negligible) | Fail to reject H₀ |
| BMI | Mann-Whitney | 0.3701 | d = -0.035 (Negligible) | Fail to reject H₀ |
| Outcome | Chi-square | 0.5000 | RR = 1.00 | Fail to reject H₀ |

No statistically significant difference was detected between groups across all three metrics. All 95% confidence intervals contained zero. Effect sizes were negligible across all metrics.

These results are expected and correct — both groups were drawn from the same population via stratified random assignment. The value of this project lies in the framework, not in manufacturing a false positive.

---

## Key Findings

- Randomisation was successful: both groups had identical diabetes rates (34.9%) and negligible effect sizes
- Sample size was sufficient to detect even small effects, meaning the null results are meaningful
- All confidence intervals contained zero, confirming consistency with the null hypothesis
- A real intervention study would require longitudinal data with pre and post measurements to detect physiological change

---

## Limitations

1. **Simulated intervention** — groups were assigned post-hoc from cross-sectional data, not enrolled prospectively
2. **No temporal component** — lifestyle interventions typically require 3 to 6 months to show measurable physiological change
3. **No baseline measurements** — a proper RCT requires pre-intervention measurements for each patient

---

## Recommendation

Before scaling or defunding any intervention programme, a properly designed longitudinal RCT is required with:
- Baseline measurements before the intervention
- Follow-up at 3 and 6 months
- Prospective random assignment at enrolment
- Targeting of high-risk patients (Glucose > 140, BMI > 30)

This framework is validated and ready to apply to such a study.

---

## Tools and Libraries

| Tool | Purpose |
|---|---|
| Python | Core analysis language |
| Pandas | Data manipulation |
| NumPy | Numerical computing |
| SciPy | Statistical testing |
| Statsmodels | Power analysis |
| Matplotlib | Visualisation |
| Seaborn | Statistical plots |

---

## Author

**Mubarak Adesola Adedeji**
Data Analyst | Python · SQL · R · Power BI
[LinkedIn](https://linkedin.com/in/mubarak-adedeji-776804273) · [GitHub](https://github.com/Mubydeji)

---

## License

MIT License — free to use, adapt, and build on with attribution.

