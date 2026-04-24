---
layout: post
title: "Odds Ratio"
date: 2026-04-24
categories: [Terms, Statistics]
math: true
---

## Definition

Odds Ratio (OR) is a statistical measure used to quantify the strength of association between two events or conditions, particularly in the context of binary outcomes. It represents the ratio of the odds of an event occurring in one group (e.g., exposed group) to the odds of the same event occurring in another group (e.g., unexposed group). The odds ratio helps determine whether a particular exposure or factor increases or decreases the likelihood of an outcome, making it a fundamental tool in epidemiology, clinical research, and logistic regression analysis.

To understand odds ratio, you must first clearly understand the concept of 'odds'.

### Concept of Odds
Odds is the value obtained by dividing the probability of an event occurring (p) by the probability of it not occurring (1-p). Unlike probability, which ranges from 0 to 1, odds ranges from 0 to infinity.

$$Odds = \frac{p}{1-p}$$

* **Example**: The probability of rolling a '1' on a die is p = 1/6. The probability of not rolling a '1' is 1 - p = 5/6. The odds at this time is (1/6) / (5/6) = 1/5 = 0.2. That is, it means the ratio of success to failure.

## Calculation

The odds ratio is calculated from a 2x2 contingency table that cross-tabulates the exposure (or predictor) and the outcome (or response). The table is structured as follows:

|                | Outcome Present | Outcome Absent | Total |
|----------------|-----------------|----------------|-------|
| Exposed        | a               | b              | a + b |
| Unexposed      | c               | d              | c + d |
| Total          | a + c           | b + d          | N     |

Assuming a 2x2 contingency table as above, odds ratio is calculated as follows.

* **Odds of occurrence in exposed group**: occurrence (a) / non-occurrence (b) = a/b
* **Odds of occurrence in unexposed group**: occurrence (c) / non-occurrence (d) = c/d

The odds ratio is then computed as:

$$
\text{OR} = \frac{Odds_{\text{exposed}}}{Odds_{\text{unexposed}}} = \frac{a/b}{c/d} = \frac{a \times d}{b \times c} \quad (1)
$$

Where:
- $a$ is the number of exposed individuals with the outcome.
- $b$ is the number of exposed individuals without the outcome.
- $c$ is the number of unexposed individuals with the outcome.
- $d$ is the number of unexposed individuals without the outcome.

## Interpretation

The calculated odds ratio value is interpreted based on the reference point of **1**.

* **OR = 1**: There is no association between exposure and event occurrence. (The odds of occurrence in the two groups are the same)
* **OR > 1**: Exposure increases the risk of event occurrence. (Risk factor)
    * Example: If the odds ratio of lung cancer occurrence in the smoker group compared to the non-smoker group is 5, it means smoking increases the odds of lung cancer occurrence by 5 times.
* **OR < 1**: Exposure decreases the risk of event occurrence. (Protective factor)
    * Example: If the odds ratio of infection in the vaccinated group compared to the unvaccinated group is 0.2, it means vaccination reduces the odds of infection by 80%.

## Necessity

Odds ratio is essential in various fields for several reasons:
- **Epidemiological Studies**: It quantifies the relationship between risk factors (e.g., smoking) and diseases (e.g., lung cancer), helping public health professionals assess intervention effectiveness.
- **Clinical Trials**: OR is used to evaluate treatment effects, such as comparing drug efficacy in randomized controlled trials.
- **Logistic Regression**: In machine learning and statistics, OR provides interpretable coefficients for binary classification models, allowing researchers to understand the impact of predictors on binary outcomes.
- **Decision Making**: It aids in risk assessment and policy-making by providing a clear metric for association strength, beyond simple proportions.

Without odds ratio, analyses would rely on less informative measures like raw counts, potentially leading to misleading conclusions about associations.

## Limitations and Alternatives

Despite its widespread use, odds ratio has several limitations:
- **Confounding**: OR can be biased if confounding variables (e.g., age, gender) are not controlled for, leading to spurious associations.
- **Rare Outcomes**: When outcomes are rare, OR approximates relative risk, but for common outcomes, it can overestimate the effect size.
- **Causality**: OR indicates association, not causation; additional evidence is needed to establish causal relationships.
- **Interpretation Challenges**: OR is not as intuitive as relative risk for some audiences, especially when outcomes are common.

### Alternatives
- **Relative Risk (RR)**: Measures the probability of an event in the exposed group relative to the unexposed group, preferred when incidence rates are available.
- **Risk Difference**: The absolute difference in risk between groups, useful for public health impact assessment.
- **Logistic Regression Models**: Provide OR as coefficients, but can incorporate multiple variables for better control of confounders.
- **Propensity Score Matching**: A method to balance covariates and estimate causal effects more accurately.

## Derived Subsequent Concepts

Odds ratio has influenced several advanced concepts in statistics and machine learning:
- **Logistic Regression**: Builds on OR by modeling the log-odds as a linear function of predictors, enabling prediction and inference. Logistic regression analysis, widely used in classification modeling, deals with data where the dependent variable is 0 or 1. Since the probability p is constrained between 0 and 1, making it difficult to model directly with linear regression, the **logit transformation** is used to convert the probability into logits, expanding the range to (-∞, ∞) for linear modeling. The logit function is the inverse of the logistic sigmoid function (commonly abbreviated as sigmoid function), which transforms probabilities into logits. The name "sigmoid" derives from the Greek words "sigma" (σ, meaning S) and "eidos" (εἶδος, meaning form or shape), referring to its S-shaped curve.

$$\ln\left(\frac{p}{1-p}\right) = \beta_0 + \beta_1 X_1 + \dots + \beta_n X_n$$

In this equation, the value obtained by taking the natural exponent of a specific regression coefficient β₁ ($e^{\beta_1}$) is the **odds ratio** of that variable X₁. That is, it is used as an indicator that intuitively explains "how many times the odds of event occurrence change when X₁ increases by 1 unit."
- **Cochran-Mantel-Haenszel Test**: Extends OR to stratified analyses, controlling for confounding in multiple strata.
- **Meta-Analysis**: Combines OR from multiple studies to estimate overall effects, using methods like Mantel-Haenszel pooling.
- **Bayesian Approaches**: Incorporate prior knowledge with OR to update probabilities in diagnostic testing and decision analysis.
- **Machine Learning Interpretability**: Concepts like feature importance in models often draw from OR-like metrics to explain model decisions.