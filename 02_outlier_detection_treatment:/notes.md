# Topic 02 — Outlier Detection & Treatment

## What Is an Outlier?
A data point that lies abnormally far from the rest of the observations.

Three types:
- **Global** — single point far from entire dataset
- **Contextual** — normal in one context, abnormal in another
- **Collective** — a group that is anomalous together

---

## Method 1: IQR (Interquartile Range)

Sort data → find Q1 (25th percentile) and Q3 (75th percentile).

IQR = Q3 - Q1
Lower Fence = Q1 - 1.5 × IQR
Upper Fence = Q3 + 1.5 × IQR

Anything outside the fences = outlier.

**Why IQR is robust:** based on rank order, not mean.
Outliers cannot influence Q1 or Q3 just by being extreme.

**Analogy:** Cricket ground boundary. IQR draws the fence based on 
where 95% of shots actually land — doesn't care about distribution shape.

---

## Method 2: Z-Score

Z = (value - mean) / std dev

If |Z| > 3 → outlier.

**The masking problem:** outliers inflate both mean and std dev.
So the outlier's own Z-score looks less extreme than it actually is.
Z-score can miss outliers in skewed data.

**Analogy:** Average Pakistani male height is 5'7", std dev 3 inches.
Someone at 7'2" has Z-score of ~7 — statistically almost impossible.

---

## IQR vs Z-Score

| | IQR | Z-Score |
|---|---|---|
| Based on | Median & quartiles | Mean & std dev |
| Affected by outliers? | No | Yes |
| Works best when | Skewed / unknown distribution | Roughly normal |
| Financial data | ✅ Preferred | ⚠️ Use carefully |

---

## Treatment Decision

> Is this outlier real, or is it an error?

| Treatment | When |
|---|---|
| **Remove** | Confirmed data error or impossible value |
| **Cap / Winsorize** | Real but extreme — clip to 95th or 99th percentile |
| **Impute** | Need to keep row count — replace with median |

---

## Key Result from Practice Problem

| | Mean | Std Dev | CV |
|---|---|---|---|
| Before treatment | 909,167 | 2,160,918 | 237% |
| After capping | 351,417 | 55,131 | 15.69% |

Two outliers (8.5M and 9.2M income) were destroying all descriptive stats.
After capping, CV dropped from 237% to 15.69% — mean became reliable.