# Topic 05 — Hypothesis Testing

## What Even Is Hypothesis Testing?
Imagine you're a credit risk manager at a bank. Someone from the product team walks in and says: "I think our new loan applicants have a higher average income than our existing customers — we should offer them bigger loans."
Your job is to say: is that actually true, or did they just get lucky with a small sample?
Hypothesis testing is the formal way to answer that question using data. It forces you to prove something is real before you act on it.

## The Setup — Null vs Alternative Hypothesis
Every hypothesis test starts with two competing statements:
Null Hypothesis (H₀) — the boring, default assumption. Nothing interesting is happening. No difference exists. The status quo is true.
Alternative Hypothesis (H₁) — the claim you're trying to prove. Something has changed. A difference exists.
Real example: Your bank's historical average loan amount is PKR 250,000. A new branch manager claims his branch is giving out larger loans on average.
H₀: The new branch mean loan amount = PKR 250,000 (no difference)
H₁: The new branch mean loan amount > PKR 250,000 (it's higher)
Your job is not to prove H₁ is true. Your job is to check whether the data gives you enough evidence to reject H₀. That's a subtle but critical distinction — you never "prove" the alternative, you just decide whether the null is convincingly wrong.

## The P-Value — The Most Misunderstood Number in Statistics
Once you run the test, you get a p-value. Here's what it actually means:

"If the null hypothesis were true, what is the probability of seeing data this extreme purely by chance?"

So if p-value = 0.03, it means: if there really was no difference, there's only a 3% chance you'd see this result by random luck alone.
The threshold you compare it to is called alpha (α), usually set at 0.05 (5%).

p-value < 0.05 → reject H₀ → the result is statistically significant
p-value > 0.05 → fail to reject H₀ → not enough evidence

Critical point: "fail to reject H₀" does NOT mean H₀ is true. It just means your data wasn't convincing enough. This is a distinction most people get wrong.
Real world analogy: Think of hypothesis testing like a court case. H₀ is "innocent until proven guilty." The p-value is the strength of the evidence against the accused. If evidence is strong enough (p < 0.05), you convict (reject H₀). If not, you acquit — but acquitting doesn't mean they're innocent, it just means you couldn't prove guilt beyond reasonable doubt.

## The T-Test — Testing Means
The most common test in practice. Used when you want to compare means.
One-sample t-test: Is this group's mean different from a known value?
Example: Is the average credit score of our new applicants different from the industry benchmark of 650?
Two-sample t-test: Are the means of two groups different from each other?
Example: Do defaulters have a significantly lower income than non-defaulters?
The t-test produces a t-statistic and a p-value. You only need the p-value to make your decision.

## The Chi-Square Test — Testing Categories
When your data is categorical (not numbers), you can't compare means. You use chi-square instead.
It asks: are two categorical variables independent of each other, or is there a real relationship?
Example: Is there a relationship between employment type (full-time, self-employed, unemployed) and whether someone defaults? Or are they independent?
H₀: Employment type and default are independent — no relationship
H₁: They are related — employment type affects default probability
Chi-square gives you a test statistic and a p-value. Same rule — p < 0.05, reject H₀, the relationship is real.

## Confidence Intervals — The Range Version of a Test
Instead of just saying "reject or don't reject," a confidence interval gives you a range of plausible values for the true mean.
A 95% confidence interval means: if you repeated this experiment 100 times, 95 of those intervals would contain the true population mean.
Example: You calculate the average income of 500 loan applicants and get a 95% CI of [PKR 42,000 — PKR 58,000]. This means you're 95% confident the true average income of all applicants falls in that range.
If a competitor claims the average is PKR 70,000 and that value falls outside your CI — that's evidence their claim is wrong.

## One-Line Summaries

| Concept | What it does |
|---|---|
| H₀ | The default assumption — nothing interesting is happening |
| H₁ | The claim you're testing |
| P-value | Probability of seeing this data if H₀ were true |
| Alpha (0.05) | Your threshold for "convincing enough" |
| T-test | Compares means |
| Chi-square | Tests relationship between categorical variables |
| Confidence Interval | Range where the true value likely lives |

---

# Practice Questions

## Practice Question 1 — One-Sample T-Test

A bank claims that the average savings account balance of its customers is ₹85,000.

A random sample of 49 customers is taken. The sample gives:
- Sample mean (x̄) = ₹81,200
- Sample standard deviation (s) = ₹14,000

Test at 5% significance level whether the bank's claim is correct.

### Solution

**Hypotheses**
- H₀: μ = 85,000
- H₁: μ ≠ 85,000 (two-tailed)

**Test statistic**

$$
z = \frac{\bar{x} - \mu_0}{s/\sqrt{n}}
$$

Standard error:
√49 = 7
14000 ÷ 7 = 2000

Numerator:
81200 − 85000 = −3800

z:
−3800 ÷ 2000 = **−1.9**

**Critical value**
Two-tailed, α = 0.05 → ±1.96

**Decision**

|z| = 1.9 < 1.96 → **Fail to reject H₀**

**Conclusion:** We don't have enough evidence to say the average balance is significantly different from ₹85,000.

---

## Practice Question 2 — One-Sample T-Test (Loan Processing Time)

A financial analyst claims that the average processing time for a loan approval at a bank is 10 days. A sample of 16 loan applications is checked, giving:

- Sample mean (x̄) = 11.2 days
- Sample standard deviation (s) = 2.4 days

Test the claim at 5% significance level.

### Solution

**Hypotheses**
- H₀: μ = 10
- H₁: μ ≠ 10 (two-tailed)

**Which test?**
σ not known, n = 16 < 30 → t-test, df = n − 1 = 15

**Test statistic**

$$
t = \frac{\bar{x} - \mu_0}{s/\sqrt{n}}
$$

Standard error:
√16 = 4
2.4 / 4 = 0.6

Numerator:
11.2 − 10 = 1.2

t:
1.2 / 0.6 = **2.0**

**Critical value**
df = 15, two-tailed, α = 0.05 → t-critical = 2.131

**Decision**

|t| = 2.0 < 2.131 → **Fail to reject H₀**

**Conclusion:** There isn't enough statistical evidence at the 5% level to say the true average loan processing time is different from 10 days.

**p-value check:** p ≈ 0.064 > 0.05 → confirms fail to reject H₀

---

## Practice Question 3 — One-Sample T-Test (Credit Card Spending)

A credit card company claims the average monthly spend of its premium customers is ₹45,000.

A sample of 25 customers shows:
- Sample mean (x̄) = ₹47,800
- Sample standard deviation (s) = ₹6,000

Test the claim at 5% significance level. (t-critical at df=24, two-tailed, α=0.05 is 2.064)

### Solution

**Hypotheses**
- H₀: μ = 45,000
- H₁: μ ≠ 45,000

**Which test?**
No population SD, n = 25 < 30 → t-test, df = 24

**Test statistic**

Standard error:
√25 = 5
6000 / 5 = 1200

Numerator:
47,800 − 45,000 = 2,800

t:
2800 / 1200 = **2.33**

**Critical value**
df=24, two-tailed, α=0.05 → 2.064

**Decision**

|t| = 2.33 > 2.064 → **Reject H₀**

**Conclusion:** We have sufficient evidence to conclude that the average spending is not ₹45,000.

**p-value check:** p ≈ 0.028 < 0.05 → confirms reject H₀

---

## Practice Question 4 — F-Test (Comparing Two Variances)

A portfolio manager wants to compare the volatility (risk) of two stocks' monthly returns.

- Stock A: sample of 13 months, sample variance s₁² = 45
- Stock B: sample of 10 months, sample variance s₂² = 20

Test at 5% significance whether Stock A is significantly more volatile (higher variance) than Stock B.

### Solution

**Hypotheses**
- H₀: σ₁² = σ₂² (both stocks equally risky)
- H₁: σ₁² > σ₂² (Stock A is riskier) → one-tailed test

**Test statistic**

$$
F = \frac{s_1^2}{s_2^2} = \frac{45}{20} = 2.25
$$

**Degrees of freedom**
- df₁ = 13 − 1 = 12 (numerator)
- df₂ = 10 − 1 = 9 (denominator)

**Critical value**
At α = 0.05, df₁=12, df₂=9 → F-critical ≈ 3.07

**Decision**

F = 2.25 < F-critical = 3.07 → **Fail to reject H₀**

**Conclusion:** Even though Stock A's sample variance (45) looks over twice as large as Stock B's (20), this difference is not statistically significant at the 5% level.

---

## Practice Question 5 — Chi-Square Test of Independence

A bank wants to know if there's a relationship between customer type (Salaried vs Self-employed) and loan default status (Defaulted vs Not Defaulted).

They collect data from 200 customers:

| | Defaulted | Not Defaulted | Row Total |
|---|---|---|---|
| **Salaried** | 20 | 100 | 120 |
| **Self-employed** | 30 | 50 | 80 |
| **Column Total** | 50 | 150 | **200** |

Test at 5% significance whether default status is independent of customer type.

### Solution

**Hypotheses**
- H₀: Customer type and default status are independent
- H₁: Customer type and default status are dependent (related)

**Expected frequencies**

$$
E = \frac{\text{Row Total} \times \text{Column Total}}{\text{Grand Total}}
$$

- E(Salaried, Defaulted) = (120 × 50)/200 = 30
- E(Salaried, Not Defaulted) = (120 × 150)/200 = 90
- E(Self-employed, Defaulted) = (80 × 50)/200 = 20
- E(Self-employed, Not Defaulted) = (80 × 150)/200 = 60

**Test statistic**

$$
\chi^2 = \sum \frac{(O-E)^2}{E}
$$

- (20−30)²/30 = 3.33
- (100−90)²/90 = 1.11
- (30−20)²/20 = 5.00
- (50−60)²/60 = 1.67

Sum = **11.11**

**Degrees of freedom**
df = (rows−1)(columns−1) = (2−1)(2−1) = 1

**Critical value**
At α=0.05, df=1 → χ²-critical = 3.841

**Decision**

χ² = 11.11 > χ²-critical = 3.841 → **Reject H₀**

**Conclusion:** There is a statistically significant relationship between customer type and loan default status — defaults are not independent of whether a customer is salaried or self-employed.