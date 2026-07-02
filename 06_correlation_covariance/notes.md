# Topic 06 — Correlation & Covariance

## What Problem Are We Solving?

You have two variables. You want to know — do they move together? When one goes up, does the other go up too? Or down? Or is there no pattern at all?

That's what correlation and covariance measure.

## Covariance — The Raw Relationship

Covariance tells you the direction of the relationship between two variables.

**Cov(X,Y) = Σ(xi − x̄)(yi − ȳ) / (n−1)**

In plain English: for each data point, how far is X from its mean, and how far is Y from its mean? Multiply those two distances together. Average the result across all points.

- **Positive covariance** — when X is above its mean, Y tends to be above its mean too. They move together.
- **Negative covariance** — when X is above its mean, Y tends to be below its mean. They move opposite.
- **Zero covariance** — no consistent pattern.

The problem with covariance: the number itself is hard to interpret. If Cov(Income, LoanAmount) = 150,000,000 — is that a strong relationship or weak? You can't tell because the units are mixed (PKR × PKR). You need something standardized.

## Correlation — The Standardized Version

Correlation fixes covariance's interpretation problem by dividing by the standard deviations of both variables:

**r = Cov(X,Y) / (σX × σY)**

This gives you a number always between -1 and +1.

- **+1** — perfect positive relationship. X goes up, Y always goes up by a proportional amount.
- **-1** — perfect negative relationship. X goes up, Y always goes down.
- **0** — no linear relationship at all.

**Real world analogy:** Think of covariance as the raw distance between two cities in some weird unit you've never heard of. Correlation is that same distance converted to kilometers — now you can actually judge whether it's close or far.

## What Counts as Strong?

| Correlation | Interpretation |
|---|---|
| 0.9 to 1.0 | Very strong positive |
| 0.7 to 0.9 | Strong positive |
| 0.5 to 0.7 | Moderate positive |
| 0.3 to 0.5 | Weak positive |
| 0 to 0.3 | Very weak or none |
| Negative values | Same scale, opposite direction |

In finance and credit risk, even a correlation of 0.3-0.4 between a feature and default can be meaningful — don't dismiss moderate correlations just because they're not 0.9.

## The Critical Warning — Correlation ≠ Causation

This is the most abused concept in data analysis.

Ice cream sales and drowning deaths are highly correlated — both peak in summer. Does eating ice cream cause drowning? Obviously not. A third variable (hot weather) drives both.

**In banking context:** Credit score and loan amount might be positively correlated — higher score borrowers get bigger loans. Does a higher credit score cause bigger loans? Not directly — it just makes the bank comfortable offering more. The causation runs through bank policy, not directly between those two numbers.

Always ask: is there a third variable (confounder) that could explain this correlation?

## Pearson vs Spearman

Two types of correlation you'll encounter:

- **Pearson** — measures linear relationship. Assumes both variables are roughly normally distributed. Standard choice for continuous numeric data.
- **Spearman** — measures monotonic relationship (does one consistently go up when the other goes up, even if not in a straight line). Better for skewed data, ordinal data, or when outliers are present.

In your Loan_default dataset — income is uniformly distributed (we found this in Topic 04), so Spearman would actually be more appropriate than Pearson for any correlation involving income.

## One-Line Summaries

| Concept | What it tells you |
|---|---|
| Covariance | Direction of relationship, but hard to interpret |
| Correlation | Direction AND strength, scaled between -1 and +1 |
| Pearson | Linear relationship, for normal continuous data |
| Spearman | Monotonic relationship, robust to skew and outliers |
| Correlation ≠ Causation | Always ask what third variable could explain this |