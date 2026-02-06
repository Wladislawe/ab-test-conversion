# A/B Test: Landing Page Conversion

## Project Abstract

Conducted an A/B test to compare the conversion rates of the old and new versions of an online store's landing page.  Based on 290,000+ observations, assessed the difference in conversion rates between the control and treatment groups, verified statistical significance using a z-test, and visualised daily dynamics

---

## Business Objective

**Objective:** to understand whether the new version of the landing page increases conversion (registrations/purchases) compared to the current one

**Hypothesis (H1):** the new page leads to **higher** conversions than the old one
**Null hypothesis (H0):** conversions for both versions **do not differ**

**Success criterion:** statistically significant increase in conversion for the treatment group at a significance level of 5%

---

## Dataset

- **Source:** Kaggle A/B testing dataset (e-commerce service landing page)
- **Structure:**
  - `user_id` — unique user;
  - `timestamp` — page view time;
  - `group` — experimental group (`control` / `treatment`);
  - `landing_page` — actual page (`old_page` / `new_page`);
  - `converted` — conversion (1 — yes, 0 — no)

---

## Methods

1. **Data cleaning**
   - Rows with missing values in key fields (`group`, `landing_page`, `converted`) were removed
   - Only correct pairs were left:
     - `control → old_page`,
     - `treatment → new_page`
   - For users with multiple The first appearance is recorded

2. **Statistical test**
   - Z-test of differences in proportions
   - Calculation of z-statistics, p-value, and 95% confidence interval for the difference in conversions

3. **Visualisation**
   - Bar chart of conversions by group with 95% CI
   - Line graph of daily conversion with points and smoothed trends

---

## Key Findings

### 1. The average conversion for control and treatment is almost identical

![Conversion by group](results/ab_conversion_bar.png)

- Conversions for both versions are around **11.8–12.0%**
- Visually, there is no noticeable gap between the columns, and the 95% confidence intervals overlap significantly

### 2. Daily trends do not show a consistent advantage for treatment

![Daily conversion](results/ab_daily_conversion.png)

- On different days, one group or the other is slightly higher, but **there is no stable dominance** of the new page
- The smoothed lines (dotted) for control and treatment are almost identical across the entire interval

### 3. Z-test results

From the calculations:

- \(z = -1.31\)
- \(p = 0.19\)
- The difference in conversions (treatment − control) is close to zero, with a 95% confidence interval that includes 0

**Interpretation:** at a 5% significance level, there is **no statistically significant evidence** that the new version of the landing page converts better or worse than the current one

---

## Interpretation & Business Impact

1. **The hypothesis of conversion growth is not confirmed**  
   The experiment does not show that the new page provides a measurable improvement in key metrics

2. **The effect is either absent or too small.**  
   With the current data, the A/B test does not detect a difference sufficient for a confident business decision

3. **No risk of metric degradation has been detected**  
   There is also no statistically significant negative difference — the new version looks ‘no worse’, but no better

---

## Recommendations

### 1. What to do with the current page

- If the goal of the experiment is **specifically to increase conversion**, it is rational to:
  - **keep the control version** as the main one;
  - consider the hypothesis ‘the new design increases conversion’ **rejected**
- If the new page is important for other reasons (brand, visual consistency, product requirements), you can:
  - switch to the new version **with the understanding** that there is no conversion gain at this time

### 2. How to improve further experiments

1. **Refine hypotheses**  
   Instead of one big change test specific elements:
   - headline and subheading;
   - call-to-action wording;
   - form length and number of fields;
   - location of the trust block (reviews, customer logos)

2. **Plan the test (power analysis)**
Before launching the next A/B test, evaluate
   - the minimum effect of interest (e.g., +1 p.p. conversion);
   - the required traffic volume and duration of the experiment

3. **Check the effects by segments**  
   To study additionally:
   - new vs returning users;
   - mobile vs desktop devices;
   - traffic sources  
   Sometimes the overall effect is ‘0’, but in certain segments the new page performs better/worse

---

## Tools

- **Language:** R
- **Packages:** `tidyverse`, `lubridate`, `ggplot2`, `scales`, `shiny`
- **Approach:** classic A/B analysis (z-test of differences in proportions) + Shiny dashboard for interactive viewing of results

![Dashboard](results/dashboard.png)

---

## Repository Structure

- `ab_test_landing`
   - `data`
      - `Sales_Data.csv` raw dataset
   - `results`
      - `segment_summary.csv` aggregated segment data
      - visualisation graphs
   - `ab_test_script.Rmd` R coding file
   - `ab_test_script.html` html output of coding file
   - `README.md`
   - `README_RUS.md`

---

## How to reproduce
### 1. Clone repository
Git clone https://github.com/Wladislawe/ab-test-conversion

### 2. Install dependencies
install.packages(c("tidyverse", "shiny", "ggplot2", "scales"))

---

## 📧 Contact
#### Vladislav Ovcharenko
##### quantitative BI and survey analyst

[LinkedIn Profile](https://www.linkedin.com/in/vlad-ovcharenko-9aa5013aa/?locale=en-US)
Email: vladgrinov890@gmail.com
Telegram: @vlad1s_love
