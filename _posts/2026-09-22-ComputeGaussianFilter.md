---
title: Computing a Discrete Gaussian Kernel
description: Derive a 3×3 discrete Gaussian kernel by sampling the continuous 2D Gaussian and normalizing the weights.
date: 2026-09-22 11:00:00
categories: [Notes]
tags: [Computer Vision]
math: true
---

We get a discrete 3 * 3 Gaussian kernel by **sampling the continuous 2D Gaussian function at 9 pixel locations**, then normalizing the values so they sum to 1.

Start from

$$
G(x,y)=\frac{1}{2\pi\sigma^2}
\exp\left(-\frac{x^2+y^2}{2\sigma^2}\right)
$$

For a 3 * 3 kernel, we usually center it at $(0,0)$, so the sample coordinates are

$$
x,y\in\{-1,0,1\}.
$$

That gives these 9 locations:

$$
\begin{bmatrix}
(-1,-1)&(0,-1)&(1,-1)\\
(-1,0)&(0,0)&(1,0)\\
(-1,1)&(0,1)&(1,1)
\end{bmatrix}
$$

Suppose we choose $\sigma=1$. Then

$$
G(x,y)=\frac{1}{2\pi}
e^{-(x^2+y^2)/2}.
$$

Now evaluate it at the three types of positions.

At the center,

$$
G(0,0)=\frac{1}{2\pi}\approx0.1592.
$$

At a direct neighbor, such as $(1,0)$,

$$
G(1,0)=\frac{1}{2\pi}e^{-1/2}
\approx0.0965.
$$

At a corner, such as $(1,1)$,

$$
G(1,1)=\frac{1}{2\pi}e^{-1}
\approx0.0585.
$$

Because of symmetry, the sampled kernel is therefore approximately

$$
\begin{bmatrix}
0.0585&0.0965&0.0585\\
0.0965&0.1592&0.0965\\
0.0585&0.0965&0.0585
\end{bmatrix}.
$$

But these nine numbers do not sum exactly to 1, because we only kept a small 3 * 3 portion of an infinite Gaussian.

Their sum is approximately 0.7795.

So we normalize:

$$
K[i,j]
=
\frac{G[i,j]}
{\sum_{m,n}G[m,n]}.
$$

This gives approximately

$$
K\approx
\begin{bmatrix}
0.0751&0.1238&0.0751\\
0.1238&0.2042&0.1238\\
0.0751&0.1238&0.0751
\end{bmatrix}
$$

and now

$$
\sum_{i,j}K[i,j]=1.
$$

That is a true 3 * 3 discrete Gaussian kernel for approximately $\sigma=1$.

The familiar kernel

$$
\frac1{16}
\begin{bmatrix}
1&2&1\\
2&4&2\\
1&2&1
\end{bmatrix}
=
\begin{bmatrix}
0.0625&0.125&0.0625\\
0.125&0.25&0.125\\
0.0625&0.125&0.0625
\end{bmatrix}
$$

is a convenient **Gaussian-like approximation**, not exactly the result of sampling a Gaussian with $\sigma=1$.



It has the same basic Gaussian structure:

$$
\text{center largest}
>
\text{direct neighbors}
>
\text{corners}.
$$

So the full process is: continuous Gaussian → sample at pixel coordinates → normalize → discrete Gaussian kernel

An important point is that **the kernel depends on** $\sigma$. A different $\sigma$ gives different sampled weights even if the kernel remains 3 * 3.