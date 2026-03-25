# A/B Testing Experiment Analysis

### Evaluating New Landing Page Impact on Conversion Rate

---

## Project Overview

This project analyzes an A/B test conducted on a website to determine whether a **new landing page (treatment)** performs better than the **existing landing page (control)** in terms of user conversion.

The analysis combines **Frequentist statistical testing** and **Bayesian inference** to provide a data-driven business recommendation.

---

## Objective

* Compare conversion rates between control and treatment groups
* Determine whether the new page improves performance
* Provide a clear business decision: **Ship / Iterate / Do not launch**

---

## Dataset Description

The dataset contains user-level experiment data from an e-commerce A/B test:

* `id` → Unique user identifier
* `time` → Timestamp of visit
* `group` → Control or Treatment
* `page` → Old or New landing page
* `converted` → Conversion outcome (0 = No, 1 = Yes)
* `country` → User location

**Data Source:** [Kaggle - E-commerce A/B Testing Dataset](https://www.kaggle.com/datasets/ahmedmohameddawoud/ecommerce-ab-testing?select=countries_ab.csv)

---

## Project Structure

```
ab-testing-project/
├── notebook/
│   ├── eda.ipynb                           # Exploratory Data Analysis & Data Cleaning
│   ├── ab_testing_conversion_analysis.ipynb  # Frequentist Statistical Testing
│   └── bayesian_testing.ipynb              # Bayesian Analysis
├── data/
│   ├── ab_test.csv                         # Original dataset
│   ├── ab_test_updated.csv                 # Cleaned dataset (output from EDA)
│   ├── countries_ab.csv                    # Country mapping data
│   └── data_link.txt                       # Link to original data source
├── README.md                                # This file
└── .gitignore                              # Git ignore configuration
```

---

## Technologies Used

* **Python 3.11**
* **pandas** - Data manipulation and analysis
* **numpy** - Numerical computing
* **matplotlib** - Data visualization
* **seaborn** - Statistical data visualization
* **statsmodels** - Statistical testing (Z-test for proportions)
* **scipy** - Scientific computing (Beta distribution)

---

## Installation & Setup

### Prerequisites
- Python 3.11+
- Virtual environment (venv, conda, etc.)

---

## Analysis Workflow

### 1. **Exploratory Data Analysis (eda.ipynb)**
* Load and merge datasets (ab_test.csv + countries_ab.csv)
* Data cleaning: Remove duplicates, validate data consistency
* Descriptive statistics and distribution analysis
* Visualization: Conversion rates by group, country, and time
* **Output:** Cleaned dataset saved as `ab_test_updated.csv`

### 2. **Frequentist Statistical Testing (ab_testing_conversion_analysis.ipynb)**
* Perform Z-test for proportions (one-sided test)
* Calculate conversion rates and confidence intervals
* Determine statistical significance at α = 0.05

### 3. **Bayesian Analysis (bayesian_testing.ipynb)**
* Beta-Binomial conjugate prior analysis
* Monte Carlo simulation (100,000 samples)
* Calculate probability that Treatment > Control

---

## Key Findings

### Conversion Rates
* **Control Group:** 12.04%
* **Treatment Group:** 11.89%
* **Difference:** -0.15% (Treatment underperforms)

### Frequentist Results
* **Method:** Z-test for proportions
* **Z-statistic:** -1.23
* **P-value:** 0.89
* **95% Confidence Interval:** [-0.38%, +0.08%]
* **Conclusion:** No statistically significant difference (p > 0.05)

### Bayesian Results
* **Method:** Beta-Binomial analysis with 100,000 Monte Carlo samples
* **Result:** P(Treatment > Control) = 10.9%
* **Conclusion:** Very low probability that treatment is better

---

## Final Recommendation

> **Do Not Launch** the new landing page
>
> The new page does **not** improve conversion rate and shows a slight negative impact.
> Both Frequentist and Bayesian analyses confirm the lack of improvement.
>
> **Next Steps:**
> - Iterate on design and messaging
> - Conduct user research to understand why performance declined
> - Consider running another test with design improvements

---

## Notes

* All statistical tests use a significance level of α = 0.05
* Bayesian analysis uses weakly informative priors (Beta(1,1))
* Analysis assumes the experiment was properly randomized
* Results are based on the complete dataset after cleaning

---

## Author

Data Analysis Portfolio Project - A/B Testing Analysis

---

## License

This project is part of a data analysis portfolio.
