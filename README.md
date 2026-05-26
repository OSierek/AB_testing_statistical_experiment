# AB_testing_statistical_experiment
This repository contains the data analysis, experimental design, and statistical validation for ENIAC's homepage A/B/C/D test. The goal of this project was to optimize the primary banner button to increase user engagement and drive high-quality traffic deeper into the conversion funnel.

# 📊 ENIAC A/B Testing: Optimizing Homepage CTR with Experimental Design

---

## 🎯 Project Overview

ENIAC's original homepage featured a white **"SHOP NOW"** button that suffered from a low Click-Through Rate (CTR) of ~2%, despite being placed in the most prominent banner area. User research revealed that the phrase "SHOP NOW" felt like too immediate of a commitment to buying, while users preferred to research and look for deals first.

To solve this, the UX and design teams developed three new variants, combining text adjustments and color choices from successful past campaigns.

---

## 🧪 Experimental Design

A **2x2 Factorial A/B/C/D Test** was conducted over 14 days (November 2, 2021 – November 16, 2021) to capture two full business cycles. 

### Tested Variants
*   **Version A (Control):** White "SHOP NOW"
*   **Version B:** Red "SHOP NOW"
*   **Version C:** White "SEE DEALS"
*   **Version D:** Red "SEE DEALS"

### Metrics Framework
*   **Primary Metric:** Click-Through Rate (CTR) on the homepage element.
*   **Guardrail Metrics:** 
    *   *Drop-off Rate:* Percentage of users initiating but abandoning the conversion process on the linked page.
    *   *Homepage-Return Rate:* Frequency of users clicking back to the homepage from category pages (indicating mismatched expectations).

---

## 🔬 Statistical Methodology & Analysis

The evaluation was performed programmatically using Python and `scipy.stats`:

1.  **Omnibus Test (Chi-Square Test of Independence):** A contingency table (Clicks vs. No-Clicks) was built to check if interaction rates depended on the button version.
    *   *Result:* **p-value < 0.05**. The Null Hypothesis was rejected; the differences are statistically significant.
2.  **Post-Hoc Analysis (Pairwise Chi-Square Tests):** To pinpoint the true winner, individual pairs were compared.
    *   *Adjustment:* **Bonferroni Correction** was applied to mitigate Type I Error inflation. With 6 pairwise comparisons, the new significance threshold was set to **\(\alpha\) = 0.0083**.
    *   *Result:* Both white buttons outpaced the red variants significantly. However, the CTR difference between Version A (White "SHOP NOW") and Version C (White "SEE DEALS") was *not* statistically significant under the strict Bonferroni threshold.

---

## 🏆 Final Decision & Business Value

While Version A and Version C performed equally well regarding initial clicks, **Version C (White "SEE DEALS") was selected as the final winner** based on downstream behavioral metrics:

*   **Higher Engagement:** Version C achieved a significantly lower **Drop-off Rate** and **Homepage-Return Rate** compared to Version A.
*   **Psychological Alignment:** Changing the copy to "SEE DEALS" aligned perfectly with qualitative user feedback. It lowered the psychological buying barrier, attracting users who were ready to browse, leading to a cleaner and higher-converting funnel.

---

## 🛠️ Tech Stack & Requirements

*   **Language:** Python 3.x
*   **Libraries:** `pandas`, `scipy`, `numpy`

To replicate the statistical testing, install the dependencies and run the analysis script:

```bash
pip install pandas scipy
python ab_test_analysis.py
```

---

## 📂 Repository Structure

```text
├── data/                  # Raw and contingency table data
├── ab_test_analysis.py    # Python script containing Chi-Square and Post-Hoc tests
├── README.md              # Project documentation
```

---

## ⚡ Python Script Highlights & Features

The `ab_test_analysis.py` script is designed with modularity, automation, and statistical rigor in mind:

*   **Automated Contingency Matrix:** The script automatically calculates non-interaction frequencies (`No-click`) from the raw data to build a clean 2x4 matrix ready for execution.
*   **Dynamic Post-Hoc Combinations:** Utilizing a nested loop structure, the script algorithmically generates and tests all 6 possible pairwise variant combinations without requiring manual data splitting.
*   **Algorithmic Error Control:** It dynamically calculates and applies the **Bonferroni Adjustment** ($\alpha / 6$) to safeguard the experiment against Type I statistical errors (false positives).
*   **Visual Significance Matrix:** Instead of dumping raw statistical values, the script outputs an intuitive Boolean Cross-Table Matrix (`True` or `False`) for immediate stakeholder evaluation.


---


markdown# 📊 ENIAC A/B Testing: Optimizing Homepage CTR with Experimental Design

This repository contains the data analysis, experimental design, and statistical validation for **ENIAC's** homepage A/B/C/D test. The goal of this project was to optimize the primary banner button to increase user engagement and drive high-quality traffic deeper into the conversion funnel.

---

## 🎯 Project Overview

ENIAC's original homepage featured a white **"SHOP NOW"** button that suffered from a low Click-Through Rate (CTR) of ~2%, despite being placed in the most prominent banner area. User research revealed that the phrase "SHOP NOW" felt like too immediate of a commitment to buying, while users preferred to research and look for deals first.

To solve this, the UX and design teams developed three new variants, combining text adjustments and color choices from successful past campaigns.

---

## 🧪 Experimental Design

A **2x2 Factorial A/B/C/D Test** was conducted over 14 days (November 2, 2021 – November 16, 2021) to capture two full business cycles. 

### Tested Variants
*   **Version A:** White "SHOP NOW" (Control) — *25,326 visits, 512 clicks (~2.02% CTR)*
*   **Version B:** Red "SHOP NOW" — *24,747 visits, 281 clicks (~1.14% CTR)*
*   **Version C:** White "SEE DEALS" — *24,876 visits, 527 clicks (~2.12% CTR)*
*   **Version D:** Red "SEE DEALS" — *25,233 visits, 193 clicks (~0.76% CTR)*

### Metrics Framework
*   **Primary Metric:** Click-Through Rate (CTR) on the homepage element.
*   **Guardrail Metrics:** 
    *   *Drop-off Rate:* Percentage of users initiating but abandoning the conversion process on the linked page.
    *   *Homepage-Return Rate:* Frequency of users clicking back to the homepage from category pages (indicating mismatched expectations).

---

## 🔬 Statistical Methodology & Analysis

The evaluation was performed programmatically using Python and `scipy.stats`:

1.  **Omnibus Test (Chi-Square Test of Independence):** A 2x4 contingency table (Clicks vs. No-Clicks) was built to check if interaction rates depended on the button version.
    *   *Result:* **p-value = $2.72 \times 10^{-48}$**. Since the p-value is drastically smaller than our significance level ($\alpha = 0.05$), the Null Hypothesis was rejected. The differences in performance are highly statistically significant.
2.  **Post-Hoc Analysis (Pairwise Chi-Square Tests):** To pinpoint the true winner, individual pairs were compared.
    *   *Adjustment:* **Bonferroni Correction** was applied to mitigate Type I Error inflation from running 6 pairwise tests. The adjusted significance threshold was set to **$\alpha_{\text{post-hoc}} = 0.00833$**.
    *   *Result:* Both white buttons (A and C) significantly outpaced the red variants (B and D). However, the CTR difference between Version A (White "SHOP NOW") and Version C (White "SEE DEALS") was *not* statistically significant under the strict Bonferroni threshold ($p > 0.00833$).

---

## 🏆 Final Decision & Business Value

While Version A and Version C performed equally well regarding the initial click-through rate, **Version C (White "SEE DEALS") was selected as the final winner** based on downstream behavioral metrics:

*   **Higher Engagement:** Version C achieved a significantly lower **Drop-off Rate** and **Homepage-Return Rate** compared to Version A.
*   **Psychological Alignment:** Changing the copy to "SEE DEALS" aligned perfectly with qualitative user feedback. It lowered the psychological buying barrier, attracting users who were ready to browse, leading to a cleaner and higher-converting funnel.

---

## 🛠️ Tech Stack & Requirements

*   **Language:** Python 3.x
*   **Libraries:** `pandas`, `scipy`, `numpy`

To replicate the statistical testing, install the dependencies and run the analysis script:

```bash
pip install pandas scipy numpy
python ab_test_analysis.py
```



