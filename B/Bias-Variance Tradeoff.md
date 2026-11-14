---
title: Bias-Variance Tradeoff
excerpt: The bias-variance tradeoff describes how a model's systematic error and sensitivity to training data contribute to prediction error.
category: [Terms, Machine Learning, Statistics]
tags: [bias-variance tradeoff, bias, variance, model selection, generalization]
author: ilwon-seo
date: 2026-11-14 00:00:00 +0000
render_with_liquid: true
toc: true
math: true
mermaid: true
---

## Definition

The bias-variance tradeoff describes how systematic prediction error and sensitivity to the training data contribute to a model's expected prediction error. In regression under squared-error loss, this error can be decomposed into squared bias, variance, and irreducible noise [1].

For a fixed input $x$, let $f(x)$ be the true conditional mean response, and let $D$ be a random training dataset. A model fitted on $D$ predicts $\hat{f}_D(x)$. **Bias** is the difference between the average prediction over possible training datasets and $f(x)$; **variance** measures how much those predictions vary across such datasets.

## Calculation

Assume a new response is $y=f(x)+\epsilon$, where the noise has conditional mean zero and variance $\sigma^2(x)$. At a fixed input, the expected squared prediction error is:

$$
\mathbb{E}_{D,\epsilon}\left[(y-\hat{f}_D(x))^2\mid x\right] = \left(\mathbb{E}_D[\hat{f}_D(x)]-f(x)\right)^2 + \text{Var}_D(\hat{f}_D(x)) + \sigma^2(x).
$$

The first term is squared bias, the second is variance across training datasets, and the last is noise in the response that the model cannot eliminate [1].

## Interpretation

A model that is too restrictive may fail to represent important patterns, producing high bias; this is commonly associated with **underfitting**. A highly flexible model may fit details specific to its training sample, producing high variance; this is commonly associated with **overfitting**. These are useful patterns, not definitions that every underfit model must have high bias or every overfit model must have high variance.

Increasing model flexibility often reduces bias while increasing variance, but the relationship depends on the data and learning procedure. The practical aim is low prediction error on new data, not minimizing bias and variance independently. For example, averaging models with bagging can reduce variance while slightly increasing bias, and still lower total expected error [1].

## Necessity

The decomposition helps explain why training error alone is not enough to choose a model: a flexible model can fit its training data well yet make less stable predictions on new samples. Comparing performance on held-out data or using cross-validation helps select model complexity and regularization for generalization.

## Limitations and Alternatives

- **Loss-specific result:** The displayed decomposition is for regression with squared-error loss. Other losses, including classification losses, require different analyses.
- **Not a fixed law of model complexity:** More flexibility does not always cause a simple, monotonic exchange between bias and variance; data size and the learning algorithm also matter.
- **Components are hard to estimate from one sample:** Bias and variance are defined over repeated training datasets. A single train/validation split estimates predictive performance but does not directly isolate both components.
- **Regularization changes the balance:** [L1 regularization](../L/L1%20Regularization.md) and [L2 regularization](../L/L2%20Regularization.md) can constrain fitted parameters and affect bias and variance; their effects depend on the model, data, and penalty strength.

## Derived Subsequent Concepts

- **Underfitting:** A model fails to capture relevant structure in the data; high bias is a common explanation.
- **Overfitting:** A model captures sample-specific patterns that do not generalize; high variance is a common explanation.
- **Generalization:** The ability of a fitted model to make useful predictions on data not used for fitting.
- **Regularization:** A family of techniques that constrain model fitting to help control generalization error.

## References

1. Scikit-learn Developers. [Single estimator versus bagging: bias-variance decomposition](https://scikit-learn.org/stable/auto_examples/ensemble/plot_bias_variance.html).
2. Hastie, T., Tibshirani, R., & Friedman, J. (2009). *The Elements of Statistical Learning: Data Mining, Inference, and Prediction* (2nd ed.), Section 7.3. [Springer](https://doi.org/10.1007/978-0-387-84858-7).
