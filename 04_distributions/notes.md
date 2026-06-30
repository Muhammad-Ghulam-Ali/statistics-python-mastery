# Topic 04 — Distributions

## What Is a Distribution?

When you collect data, the values don't all come out the same. Some appear more, some less. A distribution is just the pattern of how your data is spread across possible values.

Think of it this way — you give 1000 loan applicants a credit score test. Some score low, most score somewhere in the middle, some score very high. If you plot how many people got each score, the shape you see is the distribution.

Today we cover three distributions that show up everywhere in data science and finance.

## Distribution 1 — Normal Distribution (The Bell Curve)

Imagine you measure the monthly income of 10,000 salaried bank employees in Pakistan. Most of them earn somewhere around 80,000 PKR. Very few earn 20,000. Very few earn 200,000. The majority cluster in the middle and it tapers off symmetrically on both sides.

That shape — the symmetric bell — is the normal distribution.

Three things define it completely:

Mean (μ) — where the center of the bell sits

Standard Deviation (σ) — how wide or narrow the bell is

The wider the bell, the more spread out your data. The narrower, the more everyone is clustered around the mean.

The 68-95-99.7 Rule — memorize this:

68% of data falls within 1 standard deviation of the mean

95% falls within 2 standard deviations

99.7% falls within 3 standard deviations

Real example: Bank employee salaries, mean = 80,000 PKR, std dev = 10,000 PKR.

68% of employees earn between 70,000 and 90,000

95% earn between 60,000 and 100,000

99.7% earn between 50,000 and 110,000

Anyone earning above 110,000 or below 50,000 is statistically rare — less than 0.3% of the workforce. This is exactly how you detect anomalies in salary data.

## Distribution 2 — Binomial Distribution

Normal distribution works when outcomes are continuous — income, height, loan amount. But what if your outcome is binary? Default or no default. Approved or rejected. Fraud or clean.

That's where binomial comes in.

Binomial answers this question: if I run an experiment n times, each with a probability p of success, how many successes do I expect?

Real example: From your portfolio, each loan applicant has a 10% chance of defaulting independently. You approve 20 loans this month. What's the probability that exactly 3 of them default?

That's a binomial problem. You have:

* n = 20 trials
* p = 0.10 probability of default on each
* You want P(exactly 3 defaults)

The distribution tells you the probability of every possible outcome — 0 defaults, 1 default, 2 defaults, all the way to 20 defaults. You can then answer questions like "what's the probability that more than 5 default this month?" which is directly useful for provisioning and risk management.

### Practical Example — Binomial Formula

P(X = k) = C(n,k) × p^k × (1-p)^(n-k)

Where:
- n = 20 (loans approved)
- p = 0.10 (default probability per loan)
- k = 3 (exact number of defaults we want)

**Step 1: Calculate the combination term**

C(20,3) = 20! / (3!(20-3)!) = (20 × 19 × 18) / (3 × 2 × 1) = 6840 / 6 = 1140

This tells you there are 1,140 different ways to choose which 3 of the 20 loans default.

**Step 2: Calculate the probability term**

p^k = (0.10)^3 = 0.001

(1-p)^(n-k) = (0.90)^17 ≈ 0.16677

**Step 3: Multiply everything together**

P(X = 3) = 1140 × 0.001 × 0.16677 ≈ 0.1901

**Answer:** There's approximately a 19% chance that exactly 3 out of 20 loans default this month, given a 10% independent default probability per loan.

## Distribution 3 — Poisson Distribution

Poisson answers a different question: how many times does a rare event occur in a fixed time period?

Not binary outcomes. Not continuous measurements. Events that happen at a known average rate.

Real example: Your bank's fraud detection team knows that on average 3 fraudulent transactions occur per day. What's the probability that exactly 7 fraud cases hit tomorrow?

That's Poisson. You only need one thing — λ (lambda), the average rate of occurrence.

Another example in microfinance: on average 2 loan applications get flagged for missing documents per week. What's the probability that next week you get 5 flags? Poisson tells you.

The key difference from binomial — in Poisson you don't have a fixed number of trials. You just have a rate and a time window.

### Practical Example — Poisson Formula

P(X = k) = (λ^k × e^(-λ)) / k!

Where:
- λ (lambda) = 3 (average fraud cases per day)
- k = 7 (exact number of fraud cases we want)
- e = Euler's number ≈ 2.71828
- k! = factorial of k

**Step 1 — Calculate λ^k**

3^7 = 3 × 3 × 3 × 3 × 3 × 3 × 3 = 2187

**Step 2 — Calculate e^-λ**

e^-3 ≈ 0.0498

**Step 3 — Calculate k!**

7! = 7 × 6 × 5 × 4 × 3 × 2 × 1 = 5040

**Step 4 — Put it together**

P(X = 7) = (2187 × 0.0498) / 5040 = 108.9 / 5040 ≈ 0.0216

**Answer:** There's about a 2.16% chance exactly 7 fraud cases hit tomorrow, given the average is 3 per day.

## How They Differ — One Clean Table

| | Normal | Binomial | Poisson |
|---|---|---|---|
| Data type | Continuous | Binary outcomes | Count of rare events |
| What it models | Measurements clustering around a mean | Number of successes in n trials | Number of events in a time period |
| Parameters | Mean, Std Dev | n trials, p probability | λ average rate |
| Finance example | Employee salaries, loan amounts | Number of defaults in a portfolio | Fraud cases per day |