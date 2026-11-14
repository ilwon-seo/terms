---
title: Regression Metrics
excerpt: Regression metrics summarize the errors and relative fit of models that predict quantitative targets.
category: [Terms, Machine Learning, Statistics]
tags: [regression metrics, model evaluation, MSE, RMSE, MAE, R-squared]
author: ilwon-seo
date: 2026-11-14 00:00:00 +0000
render_with_liquid: true
toc: true
math: true
mermaid: true
---

## Definition

Regression metrics quantify different aspects of the agreement between observed numeric targets and model predictions. No single metric is best for every task: the appropriate choice depends on what prediction errors matter, the target scale, and whether the goal is to compare fit or prediction performance [1].

For observed values $y_i$ and predictions $\hat{y}_i$, define the residual as $e_i=y_i-\hat{y}_i$. Common regression metrics include [1]:

- **Mean Squared Error (MSE):** The average squared residual; large errors receive disproportionately more weight.
- **Root Mean Squared Error (RMSE):** The square root of MSE, expressed in the target's units.
- **Mean Absolute Error (MAE):** The average absolute residual; errors grow linearly rather than quadratically.
- **R-squared ($R^2$):** Compares the residual sum of squares with the variation around the observed mean.
- **Adjusted R-squared:** Modifies $R^2$ to account for the number of predictors in a fitted regression model.

## Calculation

For $n$ observations, the common unweighted forms are:

$$
\text{MSE} = \frac{1}{n}\sum_{i=1}^{n} e_i^2,
\qquad
\text{RMSE} = \sqrt{\frac{1}{n}\sum_{i=1}^{n} e_i^2},
\qquad
\text{MAE} = \frac{1}{n}\sum_{i=1}^{n}|e_i|.
$$

For nonconstant observed targets, the coefficient of determination is commonly calculated as:

$$
R^2 = 1 -
\frac{\sum_{i=1}^{n}(y_i-\hat{y}_i)^2}
{\sum_{i=1}^{n}(y_i-\bar{y})^2}.
$$

For an ordinary least-squares model with an intercept, one common adjusted form is:

$$
R^2_{\text{adj}} =
1-(1-R^2)\frac{n-1}{n-p-1},
$$

where $p$ is the number of predictors, excluding the intercept. Conventions depend on the fitted model; for example, statistical software may use a different degrees-of-freedom expression when the model has no intercept [2].

## Interpretation

- MSE and RMSE emphasize large residuals because they square them. RMSE is often easier to interpret than MSE because it uses the target's units; on the same observations, the two metrics rank models identically because RMSE is the square root of MSE.
- MAE also increases with error size, but linearly. A large residual therefore has less influence on MAE than on squared-error metrics, though MAE is not unaffected by outliers.
- Lower MSE, RMSE, and MAE values indicate smaller errors; higher $R^2$ and adjusted $R^2$ values generally indicate a better relative fit within the relevant model setting.
- $R^2$ compares a model's residual error with the variation around the observed mean. A score of $1$ indicates a perfect fit; $0$ corresponds to the mean-prediction baseline in the standard nonconstant-target setting. On held-out data, $R^2$ can be negative when predictions are worse than that baseline [1].
- Adjusted $R^2$ accounts for the number of predictors under a particular regression-model convention. Adding predictors does not guarantee that adjusted $R^2$ increases.

## Necessity

Regression metrics make model comparisons more concrete, but they answer different questions. Select a metric before comparing models, use the same evaluation examples and target scale, and measure performance on data not used to fit the model when estimating generalization [1].

The distinction between fitting loss and evaluation metric is useful: a metric may also be used as a training loss, but a model can be trained with one objective and evaluated with another. The selected measure should match the prediction target and the costs of errors in the application [1].

## Limitations and Alternatives

- **Scale matters:** MSE, RMSE, and MAE depend on the target's units and scale, so their raw values are generally not directly comparable across targets with different units or scales.
- **Different error penalties can change model rankings:** MSE/RMSE and MAE may favor different models when their residual patterns differ.
- **$R^2$ is not always between zero and one:** On held-out observations, it can be negative. Its value alone does not state whether errors are practically acceptable.
- **Constant targets need special handling:** The usual $R^2$ formula has a zero denominator when all observed target values are identical; software may handle this case differently [1].
- **Adjusted $R^2$ is not a universal predictive score:** Its adjustment assumes a particular regression setting. It does not replace held-out evaluation, and it should not be used to compare models fitted to different response samples without care.
- **Averages can hide structure:** Inspect residuals and relevant subgroups; a single aggregate score can conceal systematic errors or unusual observations, as illustrated by [Anscombe's quartet](./Regression.md).
- **These are not classification measures:** For classification-specific measures, see [Classification Metrics](../C/Classification%20Metrics.md).

## Derived Subsequent Concepts

- **Mean Squared Error (MSE):** The average squared prediction error.
- **Root Mean Squared Error (RMSE):** The square root of MSE, in the target's units.
- **Mean Absolute Error (MAE):** The average absolute prediction error.
- **R-squared ($R^2$):** A relative fit measure based on residual and total sums of squares.
- **Adjusted R-squared:** An $R^2$ variant that accounts for the number of predictors in a regression model.
- [**Regression**](./Regression.md): The supervised prediction task these metrics evaluate.
- [**Classification Metrics**](../C/Classification%20Metrics.md): Measures for evaluating categorical predictions and classification scores.

## References

1. Scikit-learn Developers. [Regression metrics](https://scikit-learn.org/stable/modules/model_evaluation.html#regression-metrics).
2. Statsmodels Developers. [RegressionResults.rsquared_adj](https://www.statsmodels.org/stable/generated/statsmodels.regression.linear_model.RegressionResults.rsquared_adj.html).
