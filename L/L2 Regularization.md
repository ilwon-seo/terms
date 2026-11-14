---
title: L2 Regularization
excerpt: L2 regularization adds a penalty on squared parameter magnitudes to an objective, encouraging smaller coefficients.
category: [Terms, Machine Learning, Statistics]
tags: [L2 regularization, ridge regression, weight decay, machine learning]
author: ilwon-seo
date: 2026-11-14 00:00:00 +0000
render_with_liquid: true
toc: true
math: true
mermaid: true
---

## Definition

L2 regularization adds a penalty proportional to the squared L2 norm of a model's parameters to its training objective. For a parameter vector $\mathbf{w}$, the commonly used penalty is $\lambda\|\mathbf{w}\|_2^2$, where $\lambda \geq 0$ controls its strength and

$$
\|\mathbf{w}\|_2^2 = \sum_{j=1}^{d} w_j^2.
$$

In linear regression with squared-error loss, this method is called **ridge regression**. In other models, an L2 parameter penalty is also commonly called weight decay, though the precise relationship between a penalty and an optimizer's weight-decay implementation depends on the training setup [1, 2].

## Calculation

For an unregularized loss $L(\mathbf{w})$, a common L2-regularized objective is:

$$
J(\mathbf{w}) = L(\mathbf{w}) + \lambda\|\mathbf{w}\|_2^2.
$$

For ridge regression with design matrix $X$, response vector $\mathbf{y}$, and $n$ observations, one common convention is:

$$
\min_{\mathbf{w}} \left(\frac{1}{2n}\sum_{i=1}^{n}(\mathbf{x}_i^\top\mathbf{w}-y_i)^2 + \lambda\sum_{j=1}^{d}w_j^2\right).
$$

Here, $\mathbf{x}_i^\top$ is the $i$th row of $X$.

The intercept, when present, is commonly left unpenalized. Implementations differ in scaling constants and parameter names, so their regularization strengths are not always directly interchangeable. For example, if $\mathbf{w}=(2,-0.5,0)$, its squared L2 penalty before multiplying by $\lambda$ is $4.25$.

## Interpretation

The squared penalty grows quadratically with each parameter's magnitude. Optimization therefore balances fit against keeping parameters small: increasing $\lambda$ generally increases shrinkage. Unlike the L1 penalty, the standard squared L2 penalty generally does not drive fitted coefficients exactly to zero, so it does not usually perform feature selection by eliminating coefficients [1].

For linear regression, ridge regression can make coefficient estimates less sensitive to correlated predictors by shrinking them, but it does not resolve every modeling or data-quality problem [1, 2].

## Necessity

L2 regularization is useful when limiting large parameter values is desirable, including when a model has many parameters or a linear model has correlated predictors. It is a way to control model fit, not a guarantee of better performance; the strength should be selected using validation data or cross-validation.

## Limitations and Alternatives

- **Usually keeps all features:** Coefficients are generally reduced rather than set exactly to zero. If a sparse linear model is desired, consider [L1 regularization](./L1%20Regularization.md).
- **Scale matters:** Since the penalty acts on coefficient magnitudes, feature scaling can affect the result.
- **Can underfit:** Excessive regularization can make parameters too small to represent useful patterns.
- **Not the same mechanism as dropout:** L2 regularization penalizes parameter magnitudes in the objective; [Dropout](../D/Dropout.md) randomly masks activations during neural-network training. They can be used as distinct regularization choices, and their effects should be evaluated for the model and task.

## Derived Subsequent Concepts

- **Ridge Regression:** Linear least-squares regression with a squared L2 penalty on its coefficients [1, 2].
- **L1 Regularization:** A penalty on absolute parameter values that can produce sparse coefficient vectors.
- **Dropout:** A stochastic neural-network regularization technique that masks activations during training.

## References

1. Scikit-learn Developers. [Linear Models: Ridge regression and classification](https://scikit-learn.org/stable/modules/linear_model.html#ridge-regression-and-classification).
2. Hoerl, A. E., & Kennard, R. W. (1970). [Ridge regression: Biased estimation for nonorthogonal problems](https://doi.org/10.1080/00401706.1970.10488634). *Technometrics*, 12(1), 55–67.
