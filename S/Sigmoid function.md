---
title: Sigmoid Function
excerpt: The sigmoid function is a mathematical function that maps real numbers to a value between 0 and 1, commonly used in machine learning for binary classification.
category: [Terms, Machine Learning]
tags: [sigmoid, activation function, logistic function, machine learning]
author: ilwon-seo
date: 2026-04-24 00:00:00 +0000
render_with_liquid: true
toc: true
math: true
mermaid: true
---

## Definition

The sigmoid function, also known as the logistic function, is a mathematical function that takes any real-valued number and maps it to a value between 0 and 1. It is S-shaped and is widely used in machine learning and statistics, particularly for binary classification problems. The sigmoid function is the inverse of the logit function, transforming logits back into probabilities.

## Mathematical Definition

The standard sigmoid function is defined as:

$$\sigma(x) = \frac{1}{1 + e^{-x}}$$

Where:
- $x$ is the input (any real number).
- $e$ is the base of the natural logarithm (approximately 2.718).
- The output $\sigma(x)$ ranges from 0 to 1.

This function is also known as the logistic sigmoid or simply the sigmoid activation function in neural networks.

### Input as Linear Combination

In machine learning contexts, particularly in logistic regression and neural networks, the input $x$ is not just a single value but typically a **linear combination of weights and input features**:

$$x = \beta_0 + \beta_1 X_1 + \beta_2 X_2 + \dots + \beta_n X_n$$

Or in vector form:

$$x = \beta^T X$$

Where:
- $\beta_0$ is the bias (intercept) term.
- $\beta_1, \beta_2, \ldots, \beta_n$ are the regression coefficients (weights).
- $X_1, X_2, \ldots, X_n$ are the input features.

Thus, the complete sigmoid function in the context of logistic regression becomes:

$$\sigma(z) = \frac{1}{1 + e^{-(\beta_0 + \beta_1 X_1 + \beta_2 X_2 + \dots + \beta_n X_n)}}$$

This means the sigmoid function outputs a probability by first computing a weighted sum of inputs and then applying the sigmoid transformation. This is the fundamental mechanism that allows logistic regression and neural networks to model non-linear relationships between inputs and binary outputs.

## Properties

The sigmoid function has several important properties:
- **Range**: Outputs values strictly between 0 and 1, making it suitable for probability estimation.
- **S-shape**: The curve is S-shaped (sigmoid), starting at 0 as $x \to -\infty$ and approaching 1 as $x \to \infty$.
- **Derivative**: The derivative of the sigmoid function is $\sigma'(x) = \sigma(x) (1 - \sigma(x))$, which is useful in backpropagation for training neural networks.
- **Symmetry**: Not symmetric around zero; it is centered at 0.5 when x=0.
- **Monotonic**: Strictly increasing, meaning higher inputs lead to higher outputs.

## Applications

The sigmoid function is essential in various domains:
- **Logistic Regression**: Used to model the probability of a binary outcome, where the logit (log-odds) is transformed back to probability.
- **Neural Networks**: Serves as an activation function in the output layer for binary classification tasks.
- **Binary Classification**: Converts raw scores into probabilities, enabling threshold-based decisions (e.g., if $\sigma(x) > 0.5$, classify as positive).
- **Signal Processing**: Used in smoothing and thresholding applications.

Without the sigmoid function, binary classification models would lack a natural way to output probabilities.

## Limitations and Alternatives

Despite its usefulness, the sigmoid function has limitations:
- **Vanishing Gradient**: For large positive or negative inputs, the gradient approaches zero, slowing down training in deep networks.
- **Not Zero-Centered**: Outputs are always positive, which can cause issues in optimization algorithms.
- **Computational Cost**: Involves exponential computation, which can be slower than simpler functions.
- **Saturation**: Extreme inputs lead to saturation, reducing sensitivity to changes.

### Alternatives
- **Tanh (Hyperbolic Tangent)**: Similar S-shape but ranges from -1 to 1, zero-centered, often preferred in hidden layers.
- **ReLU (Rectified Linear Unit)**: $\max(0, x)$, computationally efficient and avoids vanishing gradients for positive inputs.
- **Leaky ReLU**: Variant of ReLU that allows small negative values to prevent dead neurons.
- **Softmax**: For multi-class problems, normalizes outputs to probabilities summing to 1.

## Related Concepts

The sigmoid function has influenced several concepts in mathematics and machine learning:
- **Logit Function**: The inverse of the sigmoid, used in logistic regression to transform probabilities into unbounded logits.
- **Softmax Function**: Generalizes sigmoid for multi-class classification.
- **Activation Functions**: Sigmoid is one of the earliest activation functions; modern ones like ReLU build on its principles.
- **Logistic Regression**: Directly incorporates sigmoid for probability estimation.
- **Neural Network Architectures**: Foundational in early perceptrons and recurrent networks, though less common in modern deep learning.

## Example Code

Here's a simple Python code using NumPy and Matplotlib to visualize the sigmoid function:

```python
import numpy as np
import matplotlib.pyplot as plt

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

x = np.linspace(-10, 10, 100)
y = sigmoid(x)

plt.plot(x, y)
plt.title('Sigmoid Function')
plt.axvline(0, color='k')
plt.yticks(np.arange(0, 1.1, 0.1))
plt.xlabel('x')
plt.ylabel('sigmoid(x)')
plt.grid(True)
plt.show()
```

This code generates a plot of the sigmoid function over the range from -10 to 10.