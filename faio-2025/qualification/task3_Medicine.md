## Problem Statement

**The correct answer to this problem is worth 10 points.**

There is a rare disease that affects **1%** of the population.

To diagnose this disease, a new test has been developed that works as follows:
- If a person is **actually sick**, the test will show a positive result in **99%** of cases.
- If a person is **healthy**, the test will show a negative result in **98%** of cases.

## Theory

### Probability

*Intuitively*  
Probability is a number from 0 to 1 that shows how "expected" an event is:  
0 — impossible, 1 — will definitely happen, the middle — "maybe" with a certain chance.

*Formally*  
The probability of an event \(A\) is the value of the probability measure \(P(A)\) (a function that assigns a number from 0 to 1 to events), where:

$$
0 \le P(A) \le 1,\quad P(\Omega)=1,\quad P(\varnothing)=0
$$

where \(\Omega\) is the entire sample space, and \(\varnothing\) is the impossible event.  
For equally likely outcomes:

$$
P(A) = \frac{\text{number of favorable outcomes}}{\text{total number of outcomes}}.
$$

*Application*
- Data analysis: the proportion of users who made a purchase is interpreted as an estimate of \(P(\text{purchase})\).
- ML: the output of a classifier model (e.g., 0.83) is treated as an estimate of \(P(\text{class}=1 \mid \text{features})\).

### Conditional Probability

*Intuitively*  
This is "probability within a filter": it is already known that \(B\) has occurred, and we are interested in the chance of \(A\) among those cases, not among all cases.

*Formally*  
The conditional probability of \(A\) given \(B\) is defined as:

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}, \quad P(B) > 0,
$$

where \(A \cap B\) means "both events occurring simultaneously".

*Application*
- Data analysis: segment conversion rate \(= P(\text{conversion} \mid \text{channel}=\text{social media})\).
- ML: sensitivity for class \(k = P(\text{correct prediction} \mid \text{class}=k)\).

### Bayes' Theorem

*Intuitively*  
It helps "flip" a conditional probability: from "how often \(B\) happens if cause \(A\) is true," we get "how likely cause \(A\) is after observing \(B\)," taking into account our initial belief (prior).

*Formally*  
Bayes' formula:

$$
P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)},
$$

where \(P(A)\) is the prior probability (initial estimate of \(A\)),  
\(P(B \mid A)\) is the likelihood (how typical \(B\) is given \(A\)),  
\(P(A \mid B)\) is the posterior probability (updated estimate of \(A\) after observing \(B\)).

*Application*
- Data analysis: correctly interpreting a positive test for a rare event (taking into account the base prevalence \(P(A)\)).
- ML: Naive Bayes—calculating \(P(\text{class} \mid \text{features})\) via \(P(\text{features} \mid \text{class}) \cdot P(\text{class})\) and normalizing by \(P(\text{features})\).

## Answer Format

A randomly selected person from the population took the test, and their result was **positive**.

What is the probability that this person is **actually sick**? Round your answer to four decimal places.

The answer must be presented as a decimal fraction with four digits after the decimal point, for example, `0.3147`.
