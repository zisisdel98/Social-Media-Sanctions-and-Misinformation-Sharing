# Social Media Sanctions and Misinformation Sharing

This project investigates whether social media sanctions are politically biased or reflect differences in misinformation sharing across political groups.  
The analysis is inspired by [Mosleh et al. (2024)](https://www.nature.com/articles/s41586-024-07942-8), who found that higher sanction rates among conservative users are explained by increased sharing of low-quality content—not by platform bias.

Using their dataset ([`mosleh_et_al_data.csv`](mosleh_et_al_data.csv)), we replicate and extend some of their findings through descriptive statistics, hypothesis testing, and effect size analysis.

---

## Context

After the 2020 U.S. Presidential Election, many accounts using `#Trump2020` were suspended from Twitter at significantly higher rates than accounts using `#VoteBidenHarris2020`.  
This raised debates about **political bias** in moderation.

Our analysis tests whether these differences are due to **biased enforcement** or **different sharing behaviors** (e.g., misinformation prevalence).

---

## Analyses

### 1. **Twitter Suspensions After the 2020 Election**
- Use **crosstabulation** to compare suspension rates of accounts using:
  - `#Trump2020`
  - `#VoteBidenHarris2020`
- Perform a **Chi-square test** to determine whether the observed difference is statistically significant.
- Finding: `#Trump2020` users were **4.4× more likely** to be suspended.

---

### 2. **Low-Quality News Sharing**
- Examine the distribution of `lowqual_pr2019_fc` (fact-checker ratings) standardized via **z-scores** and grouped by political hashtag.
- Conduct **t-tests** between the two political groups across multiple quality rating sources:
  - `lowqual_pr2019_fc` — professional fact-checkers
  - `lowqual_afm` — Ad Fontes Media
  - `lowqual_mbfc` — Media Bias/Fact Check
  - `lowqual_lasser2019` — Lasser et al. ratings
  - `lowqual_pr2019_crowd` — balanced crowdsourced ratings
  - `lowqual_pr2019_crowdrep` — Republican crowdsourced ratings

#### Effect Size
- Compute **Cohen's d** and **Hedges' g** for each variable.
- Results show **very large** or **huge** effect sizes, indicating significantly higher low-quality content sharing by `#Trump2020` users.

| Metric                     | t-statistic | p-value | Cohen's d | Hedges' g | Effect Size      |
|----------------------------|------------:|--------:|----------:|----------:|------------------|
| lowqual_pr2019_fc          | 119.22      | 0.0     | 2.52      | 2.52      | Huge             |
| lowqual_afm                | 102.68      | 0.0     | 2.16      | 2.16      | Very Large       |
| lowqual_mbfc               | 97.59       | 0.0     | 2.06      | 2.06      | Very Large       |
| lowqual_lasser2019         | 102.63      | 0.0     | 2.16      | 2.16      | Very Large       |
| lowqual_pr2019_crowd       | 102.46      | 0.0     | 2.17      | 2.17      | Very Large       |
| lowqual_pr2019_crowdrep    | 61.07       | 0.0     | 1.29      | 1.29      | Large            |

---

### 3. **Correlations with Political Ideology**
- Examine correlations between **low-quality news sharing** and measures of political orientation:
  - `politics_followed`
  - `politics_hashtag`
  - `politics_sites1`
  - `politics_sites2`
- Visualize pairwise correlations in a **heatmap** to highlight patterns of association.

---

## Tools & Libraries

- Python 3  
- Pandas, NumPy, SciPy  
- Matplotlib, Seaborn  
- Statsmodels  
- Scikit-learn (for z-score standardization)

---
