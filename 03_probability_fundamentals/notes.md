# Topic 03 — Probability Fundamentals

## What Even Is Probability?

Probability is just answering one question: how likely is something to happen?

We express it as a number between 0 and 1.

- 0 means impossible
- 1 means certain
- 0.7 means it happens 70% of the time

That's it. Everything else is built on top of this.

## The Basic Rules

### Rule 1 — Complement

If the probability of something happening is P, then the probability of it NOT happening is 1 - P.

Example: A microfinance borrower has a 30% chance of defaulting. That means there's a 70% chance they don't default.

```
P(default) = 0.30
P(no default) = 1 - 0.30 = 0.70
```

Simple. Whatever doesn't happen is the complement.

### Rule 2 — Addition Rule

What's the probability of A or B happening?

If A and B cannot happen at the same time (mutually exclusive):

```
P(A or B) = P(A) + P(B)
```

Example: A borrower is either in the "high risk" or "low risk" bucket — never both. P(high risk) = 0.4, P(low risk) = 0.4.

```
P(high risk or low risk) = 0.4 + 0.4 = 0.8
```

If A and B CAN happen at the same time:

```
P(A or B) = P(A) + P(B) - P(A and B)
```

Why subtract? Because if you just add, you count the overlap twice.

Example: P(borrower is female) = 0.5, P(borrower is from Lahore) = 0.3, P(both) = 0.15

```
P(female or from Lahore) = 0.5 + 0.3 - 0.15 = 0.65
```

### Rule 3 — Multiplication Rule

What's the probability of A AND B both happening?

If A and B are independent (one doesn't affect the other):

```
P(A and B) = P(A) × P(B)
```

Example: You have two loan applicants. Each has a 20% chance of defaulting independently.

```
P(both default) = 0.20 × 0.20 = 0.04 → only 4% chance both default together.
```

## Conditional Probability — The Important One

This is where it gets real.

Conditional probability asks: given that something already happened, what's the probability of something else?

```
P(A | B) = P(A and B) / P(B)
```

Read it as: "Probability of A, given B."

Real example: You're a credit analyst. You know:

- 5% of all borrowers default → P(default) = 0.05
- 20% of all borrowers have missed a payment before → P(missed payment) = 0.20
- 4% of borrowers have both missed a payment AND defaulted → P(both) = 0.04

Question: If a borrower has already missed a payment, what's the probability they default?

```
P(default | missed payment) = P(both) / P(missed payment) = 0.04 / 0.20 = 0.20
```

So the default rate jumps from 5% to 20% the moment you know they've missed a payment before. That's conditional probability doing real work — it updates your belief based on new information.

## Bayes' Theorem — Conditional Probability's Powerful Sibling

Bayes flips the question. Instead of "given B, what's P(A)?", it asks: given new evidence, how should I update my belief?

```
P(A | B) = [ P(B | A) × P(A) ] / P(B)
```

We will go deep on Bayesian Thinking as a dedicated topic later. For now just know — Bayes is built entirely on conditional probability. Master that, and Bayes comes naturally.

## One-Line Summaries

RuleWhat it answersComplementWhat's the chance this does NOT happen?AdditionWhat's the chance of A or B?MultiplicationWhat's the chance of A and B together?ConditionalGiven something already happened, now what?
