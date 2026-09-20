---
title: Gaussian Distribution
description: The formulas of different dimensions of Gaussian distribution
date: 2026-09-19 18:00:00
categories: [Notes]
tags: [Probablity Theory]
math: true
---
### 1D Gaussian

For a scalar random variable $ X \sim \mathcal N(\mu,\sigma^2) $, its probability density function is

$$
p(x)
=
\frac{1}{\sqrt{2\pi\sigma^2}}
e^{
-\frac{(x-\mu)^2}{2\sigma^2}
}
=
\frac{1}{\sqrt{2\pi\sigma^2}}
\exp\left(
-\frac{(x-\mu)^2}{2\sigma^2}
\right).
$$

Here, \(\mu\) is the mean and \(\sigma^2\) is the variance.

### 2D Gaussian

Let

$$
\mathbf x=
\begin{bmatrix}
x_1\\
x_2
\end{bmatrix},
\qquad
\boldsymbol\mu=
\begin{bmatrix}
\mu_1\\
\mu_2
\end{bmatrix},
$$

and let the covariance matrix be

$$
\Sigma=
\begin{bmatrix}
\sigma_1^2 & \sigma_{12}\\
\sigma_{12} & \sigma_2^2
\end{bmatrix}.
$$

Then

$$
\mathbf X\sim\mathcal N(\boldsymbol\mu,\Sigma)
$$

with density

$$
p(\mathbf x)
=
\frac{1}{2\pi |\Sigma|^{1/2}}
\exp\left[
-\frac12
(\mathbf x-\boldsymbol\mu)^T
\Sigma^{-1}
(\mathbf x-\boldsymbol\mu)
\right].
$$

Here, \(|\Sigma|\) is the determinant of the covariance matrix.

If the two dimensions are independent and have the same variance,

$$
\Sigma=\sigma^2 I,
$$

then it simplifies to

$$
p(x,y)
=
\frac{1}{2\pi\sigma^2}
\exp\left[
-\frac{(x-\mu_x)^2+(y-\mu_y)^2}{2\sigma^2}
\right].
$$

This simplified form is commonly used for Gaussian smoothing in image processing.

### \(d\)-dimensional Gaussian

For

$$
\mathbf x\in\mathbb R^d,
\qquad
\boldsymbol\mu\in\mathbb R^d,
\qquad
\Sigma\in\mathbb R^{d\times d},
$$

the multivariate Gaussian distribution is

$$
p(\mathbf x)
=
\frac{1}
{(2\pi)^{d/2}|\Sigma|^{1/2}}
\exp\left[
-\frac12
(\mathbf x-\boldsymbol\mu)^T
\Sigma^{-1}
(\mathbf x-\boldsymbol\mu)
\right]
$$

If the \(d\) variables are **independent** and all have the **same variance** \(\sigma^2\), then the covariance matrix becomes

$$
\Sigma=\sigma^2 I,
$$

where \(I\) is the \(d\times d\) identity matrix.

So

$$
\Sigma^{-1}=\frac{1}{\sigma^2}I
$$

and

$$
|\Sigma|=(\sigma^2)^d.
$$

Substituting these into the general \(d\)-dimensional Gaussian formula gives

$$
\boxed{
p(\mathbf x)
=
\frac{1}{(2\pi\sigma^2)^{d/2}}
\exp\left[
-\frac{\|\mathbf x-\boldsymbol\mu\|^2}{2\sigma^2}
\right]
}
$$

because

$$
(\mathbf x-\boldsymbol\mu)^T
\Sigma^{-1}
(\mathbf x-\boldsymbol\mu)
=
\frac{1}{\sigma^2}
\|\mathbf x-\boldsymbol\mu\|^2.
$$

And

$$
\|\mathbf x-\boldsymbol\mu\|^2
=
\sum_{i=1}^d (x_i-\mu_i)^2.
$$

So you can also write it as

$$
\boxed{
p(\mathbf x)
=
\frac{1}{(2\pi\sigma^2)^{d/2}}
\exp\left[
-\frac{1}{2\sigma^2}
\sum_{i=1}^d (x_i-\mu_i)^2
\right]
}
$$

This is called an **isotropic Gaussian** because the variance is the same in every direction.



Also, because the variables are independent, the joint density can be written as a product of \(d\) one-dimensional Gaussians:

$$
p(\mathbf x)
=
\prod_{i=1}^d
\frac{1}{\sqrt{2\pi\sigma^2}}
\exp\left(
-\frac{(x_i-\mu_i)^2}{2\sigma^2}
\right).
$$

Multiplying them together gives exactly the same formula above.
