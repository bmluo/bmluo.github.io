---
title: Exponential Distribution
description: An introduction to the exponential distribution, covering its PDF, CDF, mean, variance, and the memoryless property.
date: 2026-09-15 14:00:00
categories: [Notes]
tags: [Probablity Theory]
math: true
---
## Definition
An **exponential distribution** is a continuous probability distribution used to model **waiting time until an event happens**, when events occur randomly at a constant average rate.

For example, it can model:

* How long you wait until the next customer arrives.
* How long until a machine fails.
* How long until the next phone call comes in.

If a random variable $X$ follows an exponential distribution, we write

$$
X \sim \operatorname{Exp}(\lambda)
$$

where $\lambda>0$ is called the **rate parameter**.

## PDF

Its probability density function is

$$
f_X(x)=
\begin{cases}
\lambda e^{-\lambda x}, & x\ge 0\\
0, & x<0
\end{cases}
$$

Since $X$ represents a waiting time, negative values are impossible.
The density is largest near $x=0$ and decreases exponentially as $x$ increases.

## CDF

The cumulative distribution function is

$$
F_X(x)=P(X\le x).
$$

For $x\ge0$,

$$
F_X(x)
=
\int_0^x \lambda e^{-\lambda t}\,dt
=
1-e^{-\lambda x}.
$$

Therefore,

$$
F_X(x)=
\begin{cases}
0, & x<0\\
1-e^{-\lambda x}, & x\ge0.
\end{cases}
$$


## Survival probability

Sometimes it is even easier to calculate

$$
P(X>x).
$$

Since

$$
P(X>x)=1-F_X(x),
$$

we get

$$
\boxed{P(X>x)=e^{-\lambda x}}.
$$

This means the probability that you need to wait **more than $x$ units of time** decreases exponentially.

## Mean and variance

For

$$
X\sim \operatorname{Exp}(\lambda),
$$

the mean is

$$
E[X]=\frac{1}{\lambda},
$$

and the variance is

$$
\operatorname{Var}(X)=\frac{1}{\lambda^2}.
$$

So $\lambda$ means roughly **how frequently events occur**. A larger $\lambda$ means events happen more frequently, so the expected waiting time is shorter.

For example, if customers arrive at an average rate of

$$
\lambda=4\text{ customers/hour},
$$

then the expected waiting time until the next customer is

$$
E[X]=\frac14\text{ hour}=15\text{ minutes}.
$$

One particularly important property of the exponential distribution is its **memoryless property**:

$$
P(X>s+t\mid X>s)=P(X>t).
$$

In words: **if you have already waited $s$ minutes, that does not change the probability distribution of how much longer you need to wait.**