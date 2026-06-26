# Topic 01 — Descriptive Statistics

## What Are Descriptive Statistics?
Tools to summarize and understand a dataset before doing anything else.
Two families: central tendency and dispersion.

---

## Measures of Central Tendency

**Mean** — sum of all values divided by count. Sensitive to outliers.

**Median** — middle value when sorted. Robust to outliers.

**Mode** — most frequent value. Useful for categorical or heavily skewed data.

---

## Measures of Dispersion

**Variance** — average of squared deviations from the mean.
- Population: divide by n
- Sample: divide by n-1 (Bessel's correction)

**Standard Deviation** — square root of variance. Same unit as original data.

**Coefficient of Variation (CV):**

CV = (std dev / mean) × 100

- CV < 30% → data is homogeneous, mean is reliable
- CV 30–100% → moderate variation, use mean carefully  
- CV > 100% → mean is misleading, segment before analyzing

---

## Real World Intuition — Microfinance

10 borrowers, monthly repayments (PKR):
5000, 5000, 6000, 7000, 8000, 9000, 10000, 11000, 12000, 95000

- Mean = ~16,800 → distorted by the 95,000 outlier
- Median = 8,500 → representative of the actual group
- Mode = 5,000 → most common repayment

A risk analyst relying on mean would overestimate typical repayment capacity.
Always check median vs mean gap — large gap signals outliers.

---

## Key Principle
> Always clean before you describe.
> Descriptive stats on dirty data give you confident wrong answers.