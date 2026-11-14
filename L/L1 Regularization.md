---
title: L1 Regularization
excerpt: L1 regularization adds the sum of absolute parameter values to an objective and can encourage sparse models.
category: [Terms, Machine Learning, Statistics]
tags: [L1 regularization, lasso, sparsity, feature selection, machine learning]
author: ilwon-seo
date: 2026-11-14 00:00:00 +0000
render_with_liquid: true
toc: true
math: true
mermaid: true
---

## Definition

[L1 regularization](../R/Regularization.md) adds a penalty proportional to the L1 norm of a model's parameters to its training objective. For a parameter vector $\mathbf{w}$, the penalty is $\lambda \|\mathbf{w}\|_1$, where $\lambda \geq 0$ controls its strength and

$$
\|\mathbf{w}\|_1 = \sum_{j=1}^{d} |w_j|.
$$

In linear regression with squared-error loss, this is the defining penalty in the **lasso** (least absolute shrinkage and selection operator). More generally, an L1 penalty can be added to other model objectives; those models are not necessarily called lasso [1, 2].

## Calculation

For an unregularized loss $L(\mathbf{w})$, the L1-regularized objective is:

$$
J(\mathbf{w}) = L(\mathbf{w}) + \lambda \sum_{j=1}^{d} |w_j|.
$$

For the lasso with a squared-error loss and design matrix $X$, response vector $\mathbf{y}$, and $n$ observations, one common convention is:

$$
\min_{\mathbf{w}} \left(\frac{1}{2n}\sum_{i=1}^{n}(\mathbf{x}_i^\top\mathbf{w}-y_i)^2 + \lambda\sum_{j=1}^{d}|w_j|\right).
$$

Here, $`\mathbf{x}_i^\top`$ is the $`i`$th row of $`X`$.

The intercept, when present, is commonly left unpenalized. Scaling constants and the name of the strength parameter vary between implementations. For example, if $\mathbf{w}=(2,-0.5,0)$, its L1 penalty before multiplying by $\lambda$ is $2.5$.

## Interpretation

The absolute-value penalty encourages a sparse parameter vector: for some values of $\lambda$, optimized coefficients can be exactly zero. In a linear model, a zero coefficient means the corresponding feature is omitted from that fitted prediction rule, so L1 regularization can perform feature selection [1].

This is an encouragement, not a guarantee that the selected features are the true or uniquely best explanatory set. When predictors are strongly correlated, the selected subset can depend on the data and modeling choices.

## Necessity

L1 regularization can be useful when a compact model is desired or when many candidate features may have little predictive value. It trades some fit to the training data for a preference toward smaller, sparser parameter vectors. The penalty strength should be selected with validation data or cross-validation rather than assumed to improve generalization automatically.

## Limitations and Alternatives

- **Selection can be unstable:** With correlated features, small changes in data can change which features receive nonzero coefficients.
- **Not all coefficients are guaranteed to be zero:** Sparsity depends on the objective, data, and chosen $\lambda$.
- **Feature scale matters:** Because the penalty acts on coefficient magnitudes, features with different scales can be penalized unevenly; scaling is often appropriate.
- **May over-shrink:** A large $\lambda$ can remove useful features and underfit the data.
- **Different regularization mechanism:** [L2 regularization](./L2%20Regularization.md) usually shrinks parameters without setting them exactly to zero, while [Dropout](../D/Dropout.md) randomly masks activations during neural-network training rather than penalizing parameter magnitudes.

## Derived Subsequent Concepts

- **Lasso:** Linear regression with an L1 penalty on its coefficients; it can produce sparse coefficient estimates [1, 2].
- **L2 Regularization:** A contrasting parameter penalty that typically shrinks coefficients without inducing exact zeros.
- **Dropout:** A stochastic neural-network regularization technique that masks activations during training instead of adding an L1 penalty.

## References

1. Scikit-learn Developers. [Linear Models: Lasso](https://scikit-learn.org/stable/modules/linear_model.html#lasso).
2. Tibshirani, R. (1996). [Regression Shrinkage and Selection Via the Lasso](https://doi.org/10.1111/j.2517-6161.1996.tb02080.x). *Journal of the Royal Statistical Society: Series B (Methodological)*, 58(1), 267–288.
