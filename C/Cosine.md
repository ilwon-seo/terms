---
title: Cosine
excerpt: Cosine is a fundamental trigonometric function that relates an angle in a right triangle to the ratio of the adjacent side to the hypotenuse. It is widely used in mathematics, physics, and machine learning.
category: [Terms, Trigonometry, Mathematics]
tags: [cosine, trigonometry, angle, circular functions, vector similarity]
author: ilwon-seo
date: 2026-04-26 00:00:00 +0000
render_with_liquid: true
toc: true
math: true
mermaid: true
---

## Definition

Cosine is a fundamental trigonometric function that relates an angle in a right triangle to the ratio of the adjacent side to the hypotenuse. In a right triangle with angle $\theta$, the cosine of the angle is defined as:

$$\cos(\theta) = \frac{\text{adjacent side}}{\text{hypotenuse}}$$

Cosine is one of the primary circular functions and can be generalized to the unit circle, where for any angle $\theta$ measured from the positive x-axis, the cosine represents the x-coordinate of the point on the unit circle. This definition extends cosine to all real numbers, including negative angles and angles greater than 360°.

### Key Properties

Cosine exhibits several fundamental properties:

- **Range**: $-1 \leq \cos(\theta) \leq 1$ for all angles $\theta$.
- **Period**: $\cos(\theta + 2\pi) = \cos(\theta)$; cosine repeats every $2\pi$ radians or 360°.
- **Even Function**: $\cos(-\theta) = \cos(\theta)$; cosine is symmetric about the y-axis.
- **Unit Circle Definition**: For a point $(x, y)$ on the unit circle at angle $\theta$, $\cos(\theta) = x$.

## Calculation

Cosine values can be calculated using various methods depending on the angle:

### Values for Special Angles

For common angles, cosine values are well-known:

| Angle (degrees) | Angle (radians) | Cosine Value |
|-----------------|-----------------|--------------|
| 0°              | 0               | 1            |
| 30°             | π/6             | √3/2 ≈ 0.866 |
| 45°             | π/4             | √2/2 ≈ 0.707 |
| 60°             | π/3             | 1/2 = 0.5    |
| 90°             | π/2             | 0            |
| 180°            | π               | -1           |
| 270°            | 3π/2            | 0            |
| 360°            | 2π              | 1            |

### Taylor Series Expansion

Cosine can be computed using its Taylor series expansion around $\theta = 0$:

$$\cos(\theta) = 1 - \frac{\theta^2}{2!} + \frac{\theta^4}{4!} - \frac{\theta^6}{6!} + \cdots = \sum_{n=0}^{\infty} \frac{(-1)^n \theta^{2n}}{(2n)!}$$

This series converges for all real values of $\theta$ and is used in most computational implementations.

### Using the Unit Circle

For any angle $\theta$ on the unit circle, if a point has coordinates $(x, y)$ at angle $\theta$ from the center:

$$\cos(\theta) = x$$

* **Example**: At angle $\theta = 60°$ on the unit circle, the point is at $(1/2, \sqrt{3}/2)$, so $\cos(60°) = 1/2$.

### Cosine Similarity

In machine learning and data analysis, cosine similarity measures the similarity between two vectors $\mathbf{u}$ and $\mathbf{v}$ using the cosine of the angle between them:

$$\text{cosine similarity} = \frac{\mathbf{u} \cdot \mathbf{v}}{\|\mathbf{u}\| \|\mathbf{v}\|} = \cos(\theta)$$

Where:
- $\mathbf{u} \cdot \mathbf{v}$ is the dot product of the vectors.
- $\|\mathbf{u}\|$ and $\|\mathbf{v}\|$ are the Euclidean norms (L2 norms) of the vectors.
- $\theta$ is the angle between the vectors.

* **Example**: For vectors $\mathbf{u} = (1, 0)$ and $\mathbf{v} = (0.707, 0.707)$, cosine similarity is $\frac{1 \times 0.707 + 0 \times 0.707}{\sqrt{1} \times \sqrt{1}} = 0.707$, corresponding to a 45° angle.

## Interpretation

The value of cosine provides important information about angles and geometric relationships:

* **$\cos(\theta) = 1$**: $\theta = 0°$; the angle is zero, vectors are perfectly aligned.
* **$\cos(\theta) > 0$**: $0° < \theta < 90°$; the angle is acute, vectors point in similar directions.
* **$\cos(\theta) = 0$**: $\theta = 90°$; the angle is right, vectors are orthogonal (perpendicular).
* **$\cos(\theta) < 0$**: $90° < \theta < 180°$; the angle is obtuse, vectors point in opposite directions.
* **$\cos(\theta) = -1$**: $\theta = 180°$; the angle is flat, vectors are perfectly opposite.

In the context of cosine similarity, these interpretations help measure how similar two entities are:
- Values close to 1 indicate high similarity.
- Values close to 0 indicate no correlation or orthogonality.
- Values close to -1 indicate high dissimilarity or opposition.

## Necessity

Cosine is essential in numerous fields for fundamental reasons:

- **Trigonometry and Geometry**: Cosine is one of the foundational tools for solving triangles, calculating distances, and understanding angular relationships.
- **Physics and Engineering**: Cosine is used in mechanics (force components), optics (angle of incidence), wave analysis, and countless other applications where periodic functions are needed.
- **Signal Processing**: Cosine is the basis of the Fourier transform and cosine transform, which decompose signals into frequency components.
- **Machine Learning and NLP**: Cosine similarity measures the semantic similarity between documents, word embeddings, and other high-dimensional vectors, making it indispensable for text analysis, recommendation systems, and clustering.
- **Computer Graphics**: Cosine is used in lighting calculations (Lambert's cosine law), texture mapping, and 3D transformations.
- **Harmonics and Oscillations**: Any periodic phenomenon (sound waves, electrical current, light) is fundamentally described using cosine and sine functions.

Without cosine, modern science, engineering, and machine learning would lack crucial tools for mathematical analysis and practical applications.

## Limitations and Alternatives

Despite its widespread utility, cosine has certain limitations:

- **Magnitude Insensitivity**: Cosine similarity only considers direction, ignoring the magnitude of vectors. Two vectors with the same direction but different lengths have identical cosine similarity (1).
- **Limited to Angles**: Cosine measures the angle between vectors but doesn't directly indicate distance. Two vectors at a 90° angle could still be close in Euclidean distance if they are short.
- **Computational Cost for High Dimensions**: Computing cosine similarity requires calculating dot products and norms, which can be computationally expensive for very high-dimensional data.
- **Negative Values**: Cosine can produce negative values, which some applications may find counterintuitive compared to other similarity measures.

### Alternatives

- **Euclidean Distance**: Measures the straight-line distance between points, considering both direction and magnitude. More intuitive in spatial contexts but sensitive to scale differences.
- **Manhattan Distance**: Uses absolute differences along each dimension. Computationally simpler but less geometrically intuitive.
- **Pearson Correlation Coefficient**: Measures linear correlation between two variables, accounting for mean differences and standard deviations.
- **Jaccard Similarity**: For set-based data, measures the intersection divided by the union of sets.
- **KL Divergence**: For probability distributions, measures how one distribution differs from another.
- **Dot Product**: Combine direction and magnitude; emphasizes both aspects but lacks normalization.

## Derived Subsequent Concepts

Cosine has led to numerous advanced concepts in mathematics and its applications:

- **Fourier Transform**: The Fourier transform decomposes a signal into a sum of cosine and sine functions, revealing frequency components. This is fundamental to signal processing, image compression, and audio analysis.

$$f(x) = a_0 + \sum_{n=1}^{\infty} \left(a_n \cos\left(\frac{2\pi nx}{L}\right) + b_n \sin\left(\frac{2\pi nx}{L}\right)\right)$$

- **Cosine Annealing**: A learning rate scheduling technique in machine learning that uses a cosine function to gradually reduce the learning rate during training, improving model convergence and generalization.

$$\text{learning rate} = \eta_{\min} + \frac{1}{2}(\eta_{\max} - \eta_{\min})\left(1 + \cos\left(\pi \frac{t}{T}\right)\right)$$

where $t$ is the current iteration and $T$ is the total number of iterations.

- **Cosine Distance**: Defined as $1 - \text{cosine similarity}$, providing a bounded distance measure between 0 and 2. This transforms cosine similarity into a useful distance measure(or pseudo-distance metric).
- **Spectral Analysis**: In signal processing, the Discrete Cosine Transform (DCT) uses cosine functions to represent signals with fewer coefficients than the original signal, enabling efficient compression (used in JPEG compression).
- **Law of Cosines**: Extends cosine to arbitrary triangles (not just right triangles), allowing calculation of side lengths and angles from other measurements:

$$c^2 = a^2 + b^2 - 2ab\cos(C)$$

where $C$ is the angle opposite side $c$.

- **Vector Spaces and Inner Products**: Cosine is intimately related to inner products in linear algebra. For unit vectors, the dot product equals the cosine of the angle between them, forming the foundation of geometric analysis in vector spaces.
- **Dimensionality Reduction**: Techniques like PCA (Principal Component Analysis) use cosine-like concepts (eigenvectors and angles) to identify directions of maximum variance in high-dimensional data.
- **Semantic Search and Information Retrieval**: Modern search engines and recommendation systems use cosine similarity between query embeddings and document embeddings to rank relevance, enabling efficient semantic search without keyword matching.
