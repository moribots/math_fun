# linear_algebra_fun
A  place to brush up on practical applications of linear algebra.

# Project - Linear Regression

```
linear_regression.py
```

## Derivation of the Normal Equation

The **Normal Equation** is a closed-form solution that minimizes the MSE cost function to find the coefficients $\boldsymbol{\beta}$.

---

## Problem Setup

Linear regression will find $\boldsymbol{\beta}$ to fit a line to:

$$
\mathbf{y} = \mathbf{X} \boldsymbol{\beta} + \epsilon
$$

Where:
- $\mathbf{y} \in \mathbb{R}^m$: observations.
- $\mathbf{X} \in \mathbb{R}^{m \times n}$: inputs, where each row is a data point and each column is a feature. The first column is all ones to account for the intercept.
- $\boldsymbol{\beta} \in \mathbb{R}^n$: vector of coefficients to learn.
- $\epsilon \in \mathbb{R}^m$: noise vector injected into the model.
- $m$: number of observations.

Find $\boldsymbol{\beta}$ that minimizes the sum of squared errors (SSE) across data points.

---

## 1. Cost Function

Cost function:

$$
C(\boldsymbol{\beta}) = \frac{1}{2m} \|\mathbf{y} - \mathbf{X}\boldsymbol{\beta}\|^2
$$

Where:

$$
\|\mathbf{y} - \mathbf{X}\boldsymbol{\beta}\|^2 = (\mathbf{y} - \mathbf{X}\boldsymbol{\beta})^T (\mathbf{y} - \mathbf{X}\boldsymbol{\beta})
$$

---

## 2. Expand

Expand the squared term:

$$
\|\mathbf{y} - \mathbf{X}\boldsymbol{\beta}\|^2 = \mathbf{y}^T\mathbf{y} - 2\mathbf{y}^T\mathbf{X}\boldsymbol{\beta} + \boldsymbol{\beta}^T\mathbf{X}^T\mathbf{X}\boldsymbol{\beta}
$$

The cost function becomes:

$$
C(\boldsymbol{\beta}) = \frac{1}{2m} \left( \mathbf{y}^T\mathbf{y} - 2\mathbf{y}^T\mathbf{X}\boldsymbol{\beta} + \boldsymbol{\beta}^T\mathbf{X}^T\mathbf{X}\boldsymbol{\beta} \right)
$$

---

## 3. Cost Gradient

To minimize $C(\boldsymbol{\beta})$, take the gradient wrt $\boldsymbol{\beta}$ and set it to zero:

$$
\frac{\partial C(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}} = \frac{\partial}{\partial \boldsymbol{\beta}} \left( \frac{1}{2m} \|\mathbf{y} - \mathbf{X}\boldsymbol{\beta}\|^2 \right)
$$

Using the expanded form:

$$
\frac{\partial C(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}} = \frac{1}{m} \left( -\mathbf{X}^T\mathbf{y} + \mathbf{X}^T\mathbf{X}\boldsymbol{\beta} \right)
$$

Set the gradient to zero for minimization:

$$
\mathbf{X}^T\mathbf{X}\boldsymbol{\beta} = \mathbf{X}^T\mathbf{y}
$$

---

## 4. Solve for $ \boldsymbol{\beta} $

Assume $\mathbf{X}^T\mathbf{X}$ is invertible (nonsingular):

$$
\boldsymbol{\beta} = (\mathbf{X}^T\mathbf{X})^{-1} \mathbf{X}^T\mathbf{y}
$$

This is the **Normal Equation**, which provides the optimal $ \boldsymbol{\beta} $ to minimize the cost function.

---

## Assumptions

1. **Invertibility**: The matrix $\mathbf{X}^T\mathbf{X}$ must be invertible. If it’s not, we can just use SVD.
2. **Linearity**: The relationship between the features and target is assumed to be linear.

Regardless, ultimately we perform linear regression to find the coefficients. This derivation is just so we can check our work.

---

## Outcome

Plot:

![Gradient Descent Animation](gradient_descent.gif)


