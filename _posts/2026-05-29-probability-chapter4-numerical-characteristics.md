---
layout: post
title: "概率论与数理统计 第4章 随机变量的数字特征"
date: 2026-05-29 10:00:00
description: 概率论与数理统计第4章学习笔记，涵盖期望、方差、常见分布的数字特征、切比雪夫不等式、协方差与相关系数、矩与协方差矩阵等内容。
tags: probability statistics math
categories: mathematics
toc:
  beginning: true
---

## 章节概览

本章主要介绍随机变量的各种数字特征（Numerical Characteristics），包括：

- **4.1 随机变量的期望** (Expectation of a Random Variable)
- **4.2 方差** (Variance)
- **4.3 常见分布的数字特征** (Characteristics of Common Distributions)
- **4.4 切比雪夫不等式** (Chebyshev's Inequality)
- **4.5 协方差与相关系数** (Covariance and Correlation)
- **4.6 矩与协方差矩阵** (Moments and Covariance Matrices)

---

## 4.1 随机变量的期望 (Expectation of a Random Variable)

### 背景说明

随机变量的分布函数（CDF）完整地描述了其统计规律性，但有时我们需要了解随机变量的某些特征值，如平均值或期望值，这些特征值可以让我们在不描述整个分布的情况下了解变量的中心位置。

### 4.1.1 离散型随机变量的期望

**定义 4.1.1** (Definition 4.1.1)

设 $$X$$ 是离散型随机变量，其概率分布律（PF, Probability Function）为：

$$
P(X = x_k) = p_k, \quad k = 1, 2, \cdots
$$

若级数 $$\sum_{k=1}^{\infty} x_k p_k$$ 绝对收敛，则称 $$X$$ 的**期望**（Expectation/Mean/Expected Value）存在，定义为：

$$
E(X) = \sum_{k=1}^{\infty} x_k p_k
$$

> **注释** (Remark)：不仅要求级数收敛，还要求**绝对收敛**（absolutely convergent），因为非绝对收敛的无穷级数重排后可能得到不同的和。绝对收敛保证了期望的唯一性。

### 4.1.2 连续型随机变量的期望

**定义 4.1.2** (Definition 4.1.2)

设 $$X$$ 是连续型随机变量，其概率密度函数（PDF, Probability Density Function）为 $$f(x)$$，若积分 $$\int_{-\infty}^{\infty} x f(x) dx$$ 绝对收敛，则称 $$X$$ 的期望存在，定义为：

$$
E(X) = \int_{-\infty}^{\infty} x f(x) dx
$$

### 4.1.3 随机变量函数的期望

**定理 4.1.1** (Theorem 4.1.1)

设 $$X$$ 是随机变量，$$Y = r(X)$$ 是 $$X$$ 的函数：

**(1) 离散情形：** 若 $$X$$ 的分布律为 $$P(X = x_k) = p_k$$，且 $$\sum_{k=1}^{\infty} r(x_k) p_k$$ 绝对收敛，则：

$$
E(Y) = \sum_{k=1}^{\infty} r(x_k) p_k
$$

**(2) 连续情形：** 若 $$X$$ 的密度函数为 $$f(x)$$，且 $$\int_{-\infty}^{\infty} r(x) f(x) dx$$ 绝对收敛，则：

$$
E(Y) = \int_{-\infty}^{\infty} r(x) f(x) dx
$$

### 4.1.4 多维随机变量函数的期望

**定理 4.1.2** (Theorem 4.1.2)

设 $$X_1, \cdots, X_n$$ 是具有联合概率密度函数 $$f(x_1, \cdots, x_n)$$ 的随机变量，$$Y = r(X_1, \cdots, X_n)$$，则：

$$
E(Y) = \int_{-\infty}^{\infty} \cdots \int_{-\infty}^{\infty} r(x_1, \cdots, x_n) f(x_1, \cdots, x_n) dx_1 \cdots dx_n
$$

### 4.1.5 期望的性质

**定理 4.1.3** (Theorem 4.1.3) - 线性性质

若 $$Y = aX + b$$，其中 $$a, b$$ 为有限常数，则：

$$
E(Y) = aE(X) + b
$$

> **注释**：一般情况下，$$E(XY) \neq E(X)E(Y)$$。

**定理 4.1.4** (Theorem 4.1.4) - 保序性

- 若存在常数 $$a$$ 使得 $$P(X \geq a) = 1$$，则 $$E(X) \geq a$$
- 若存在常数 $$b$$ 使得 $$P(X \leq b) = 1$$，则 $$E(X) \leq b$$

**定理 4.1.5** (Theorem 4.1.5) - 和的期望

若 $$X_1, \cdots, X_n$$ 是 $$n$$ 个随机变量，且每个期望 $$E(X_i)$$ 都存在 $$(i = 1, \cdots, n)$$，则：

$$
E(X_1 + \cdots + X_n) = E(X_1) + \cdots + E(X_n)
$$

> **注释**：即使 $$X_1, \cdots, X_n$$ 不独立，此性质也成立。

**定理 4.1.6** (Theorem 4.1.6) - 独立随机变量积的期望

若 $$X_1, \cdots, X_n$$ 是 $$n$$ 个**相互独立**的随机变量，且每个期望 $$E(X_i)$$ 都存在 $$(i = 1, \cdots, n)$$，则：

$$
E(X_1 X_2 \cdots X_n) = E(X_1) \times E(X_2) \times \cdots \times E(X_n)
$$

---

## 4.2 方差 (Variance)

### 4.2.1 方差的定义

**定义 4.2.1** (Definition 4.2.1)

设 $$X$$ 是具有有限均值 $$\mu = E(X)$$ 的随机变量，$$X$$ 的**方差**（Variance）定义为：

$$
\sigma_X^2 = \text{Var}(X) = E[(X - \mu)^2]
$$

- 若 $$X$$ 的均值无穷大或不存在，则称 $$\text{Var}(X)$$ 不存在
- **标准差**（Standard Deviation）$$\sigma_X$$ 是方差的非负平方根

**方差的意义**：方差描述了随机变量取值与其期望之间的偏离程度。取值越集中，方差越小；取值越分散，方差越大。方差是衡量随机变量**离散程度**的指标。

### 4.2.2 方差的计算公式

**定理 4.2.1** (Theorem 4.2.1)

对任意随机变量 $$X$$：

$$
\text{Var}(X) = E(X^2) - [E(X)]^2
$$

### 4.2.3 方差的性质

**定理 4.2.2** (Theorem 4.2.2)

对每个随机变量 $$X$$，$$\text{Var}(X) \geq 0$$。若 $$X$$ 是有界随机变量，则 $$\text{Var}(X)$$ 必定存在且有限。

**定理 4.2.3** (Theorem 4.2.3)

$$\text{Var}(X) = 0$$ 当且仅当存在常数 $$c = E(X)$$ 使得 $$P(X = c) = 1$$。

**定理 4.2.4** (Theorem 4.2.4) - 方差的展开

若 $$X$$ 和 $$Y$$ 是满足 $$\text{Var}(X) < \infty$$ 和 $$\text{Var}(Y) < \infty$$ 的随机变量，$$a, b, c$$ 为常数，则：

$$
\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y) + 2[E(XY) - E(X)E(Y)]
$$

$$
\text{Var}(aX + bY + c) = a^2\text{Var}(X) + b^2\text{Var}(Y) + 2ab[E(XY) - E(X)E(Y)]
$$

**定理 4.2.5** (Theorem 4.2.5) - 独立随机变量线性组合的方差

若 $$X_1, \cdots, X_n$$ 是具有有限均值的独立随机变量，$$a_1, \cdots, a_n$$ 和 $$b$$ 是任意常数，则：

$$
\text{Var}(a_1 X_1 + \cdots + a_n X_n + b) = a_1^2 \text{Var}(X_1) + \cdots + a_n^2 \text{Var}(X_n)
$$

---

## 4.3 常见分布的数字特征 (Characteristics of Common Distributions)

### 4.3.1 伯努利分布 (Bernoulli Distribution)

**定理 4.3.1** (Theorem 4.3.1)

若随机变量 $$X$$ 服从参数为 $$p$$ $$(0 \leq p \leq 1)$$ 的伯努利分布，即 $$X$$ 只能取 0 和 1，且：

$$
P(X = 1) = p, \quad P(X = 0) = 1 - p
$$

则：

$$
E(X) = p, \quad \text{Var}(X) = p(1-p)
$$

**伯努利试验** (Bernoulli Trials)：若有限或无限序列 $$X_1, X_2, \cdots$$ 中的随机变量相互独立同分布（IID），且每个 $$X_i$$ 服从参数为 $$p$$ 的伯努利分布，则称 $$X_1, X_2, \cdots$$ 为参数为 $$p$$ 的伯努利试验。

### 4.3.2 二项分布 (Binomial Distribution)

**定理 4.3.2** (Theorem 4.3.2)

若随机变量 $$X_1, \cdots, X_n$$ 构成 $$n$$ 次参数为 $$p$$ 的伯努利试验，且 $$X = X_1 + \cdots + X_n$$，则 $$X$$ 服从参数为 $$n$$ 和 $$p$$ 的二项分布 $$B(n, p)$$，其分布律为：

$$
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, \cdots, n
$$

则：

$$
E(X) = np, \quad \text{Var}(X) = np(1-p)
$$

### 4.3.3 泊松分布 (Poisson Distribution)

**定理 4.3.3** (Theorem 4.3.3)

若 $$X \sim \text{Poisson}(\lambda)$$，则：

$$
E(X) = \text{Var}(X) = \lambda
$$

分布律为：

$$
P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \cdots
$$

### 4.3.4 超几何分布 (Hypergeometric Distribution)

**定理 4.3.4** (Theorem 4.3.4)

设 $$X \sim H(N, m, n)$$，其中参数 $$N, m, n$$ 均为正数，则：

$$
E(X) = \frac{nm}{N}
$$

$$
\text{Var}(X) = \frac{nm(N-m)(N-n)}{N^2(N-1)}
$$

### 4.3.5 负二项分布 (Negative Binomial Distribution)

**定理 4.3.5** (Theorem 4.3.5)

若 $$X$$ 服从参数为 $$r$$ 和 $$p$$ 的负二项分布，则：

$$
E(X) = \frac{r}{p}, \quad \text{Var}(X) = \frac{r(1-p)}{p^2}
$$

### 4.3.6 均匀分布 (Uniform Distribution)

**定理 4.3.6** (Theorem 4.3.6)

设 $$X \sim U[a, b]$$，则：

$$
E(X) = \frac{a+b}{2}, \quad \text{Var}(X) = \frac{(b-a)^2}{12}
$$

概率密度函数为：

$$
f(x) = \begin{cases} \frac{1}{b-a}, & a \leq x \leq b \\ 0, & \text{其他} \end{cases}
$$

### 4.3.7 指数分布 (Exponential Distribution)

**定理 4.3.7** (Theorem 4.3.7)

设 $$X \sim \text{Exp}(\lambda)$$，则：

$$
E(X) = \frac{1}{\lambda}, \quad \text{Var}(X) = \frac{1}{\lambda^2}
$$

概率密度函数为：

$$
f(x) = \begin{cases} \lambda e^{-\lambda x}, & x > 0 \\ 0, & x \leq 0 \end{cases}
$$

### 4.3.8 正态分布 (Normal Distribution)

**定理 4.3.8** (Theorem 4.3.8)

设 $$X \sim N(\mu, \sigma^2)$$，则：

$$
E(X) = \mu, \quad \text{Var}(X) = \sigma^2
$$

概率密度函数为：

$$
f(x) = \frac{1}{\sqrt{2\pi}\sigma} e^{-\frac{(x-\mu)^2}{2\sigma^2}}, \quad -\infty < x < \infty
$$

其中 $$-\infty < \mu < \infty$$ 和 $$\sigma > 0$$ 是两个参数。

**标准化**：令 $$Y = \frac{X - \mu}{\sigma}$$，则 $$Y \sim N(0, 1)$$（标准正态分布）。

> **重要说明**：正态分布的两个参数恰好是其均值和方差，正态分布完全由其均值和方差确定。

### 4.3.9 Gamma分布 (Gamma Distribution)

**定理 4.3.9** (Theorem 4.3.9)

设 $$X \sim \text{Gamma}(\alpha, \beta)$$，则：

$$
E(X) = \alpha\beta, \quad \text{Var}(X) = \alpha\beta^2
$$

**备注 4.3.1** (Remark 4.3.1)

特别地，当 $$\alpha = \frac{n}{2}$$，$$\beta = 2$$ 时，Gamma分布退化为自由度为 $$n$$ 的 **卡方分布**（Chi-squared Distribution）$$\chi^2(n)$$：

- 若 $$X \sim \chi^2(n)$$，则 $$E(X) = n$$，$$\text{Var}(X) = 2n$$

---

## 4.4 切比雪夫不等式 (Chebyshev's Inequality)

### 4.4.1 切比雪夫不等式

**定理 4.4.1** (Theorem 4.4.1)

设 $$X$$ 是具有均值 $$E(X)$$ 和方差 $$\text{Var}(X) = \sigma^2$$ 的随机变量，则对任意 $$\varepsilon > 0$$：

$$
P(|X - E(X)| \geq \varepsilon) \leq \frac{\text{Var}(X)}{\varepsilon^2} = \frac{\sigma^2}{\varepsilon^2}
$$

**等价形式**：

$$
P(|X - E(X)| < \varepsilon) \geq 1 - \frac{\text{Var}(X)}{\varepsilon^2}
$$

或令 $$k = \frac{\varepsilon}{\sigma}$$：

$$
P(|X - E(X)| \geq k\sigma) \leq \frac{1}{k^2}
$$

### 4.4.2 证明思路

**注释 4.4.1** (Remark 4.4.1)

切比雪夫不等式提供了一种在不知道 $$X$$ 具体分布的情况下近似概率的方法。

**注释 4.4.2** (Remark 4.4.2)

由于切比雪夫不等式不对分布形状做任何假设，这是一个缺点。虽然不等式成立，但它过于一般化，实用性有限，因此主要用于理论研究。切比雪夫的结果虽然正确，但与实际值相比非常保守。

---

## 4.5 协方差与相关系数 (Covariance and Correlation)

### 4.5.1 协方差的定义

**定义 4.5.1** (Definition 4.5.1)

设 $$X$$ 和 $$Y$$ 是具有有限均值的随机变量，$$E(X) = \mu_X$$，$$E(Y) = \mu_Y$$。$$X$$ 和 $$Y$$ 的**协方差**（Covariance）定义为：

$$
\text{Cov}(X, Y) = E[(X - \mu_X)(Y - \mu_Y)] = E(XY) - E(X)E(Y)
$$

特别地，当 $$X = Y$$ 时，$$\text{Cov}(X, X) = \text{Var}(X)$$。

**协方差的意义**：协方差是衡量两个随机变量之间关联性质的指标，它只描述两个随机变量之间的**线性关系**。

### 4.5.2 协方差与方差的关系

**定理 4.5.1** (Theorem 4.5.1)

若 $$X$$ 和 $$Y$$ 是满足 $$\text{Var}(X) < \infty$$ 和 $$\text{Var}(Y) < \infty$$ 的随机变量，$$a, b, c$$ 为常数，则：

$$
\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y) + 2\text{Cov}(X, Y)
$$

$$
\text{Var}(aX + bY + c) = a^2\text{Var}(X) + b^2\text{Var}(Y) + 2ab\text{Cov}(X, Y)
$$

### 4.5.3 协方差的性质

**命题 4.5.1** (Proposition 4.5.1)

协方差具有以下性质：对随机变量 $$X, Y, Z$$ 和常数 $$a, b$$：

1. **对称性**：$$\text{Cov}(X, Y) = \text{Cov}(Y, X)$$
2. **齐次性**：$$\text{Cov}(aX, bY) = ab\text{Cov}(X, Y)$$
3. **可加性**：$$\text{Cov}(X + Y, Z) = \text{Cov}(X, Z) + \text{Cov}(Y, Z)$$

### 4.5.4 相关系数的定义

**定义 4.5.2** (Definition 4.5.2)

设 $$X$$ 和 $$Y$$ 是具有有限方差 $$\sigma_X^2$$ 和 $$\sigma_Y^2$$ 的随机变量，则 $$X$$ 和 $$Y$$ 的**相关系数**（Correlation Coefficient）定义为：

$$
\rho_{X,Y} = \frac{\text{Cov}(X, Y)}{\sigma_X \sigma_Y} = \frac{\text{Cov}(X, Y)}{\sqrt{\text{Var}(X)}\sqrt{\text{Var}(Y)}}
$$

**备注 4.5.1** (Remark 4.5.1)

令 $$X^* = \frac{X - \mu_X}{\sigma_X}$$，$$Y^* = \frac{Y - \mu_Y}{\sigma_Y}$$，则 $$E(X^*) = E(Y^*) = 0$$，$$\text{Var}(X^*) = \text{Var}(Y^*) = 1$$，$$X^*$$ 和 $$Y^*$$ 分别称为 $$X$$ 和 $$Y$$ 的**标准化变量**（Standardized Variables）。

$$
\rho_{X,Y} = \text{Cov}(X^*, Y^*)
$$

$$\rho_{X,Y}$$ 是无量纲的（free of units）。

### 4.5.5 相关系数的性质

**定理 4.5.2** (Theorem 4.5.2)

相关系数具有以下性质：

1. $$-1 \leq \rho_{X,Y} \leq 1$$
2. $$|\rho_{X,Y}| = 1$$ 当且仅当存在常数 $$a, b$$ 使得 $$P(Y = a + bX) = 1$$，且：
   - 当 $$b > 0$$ 时，$$\rho_{X,Y} = 1$$
   - 当 $$b < 0$$ 时，$$\rho_{X,Y} = -1$$

**解释**：

- 相关系数接近 1 表示 $$X$$ 和 $$Y$$ 通常同时取大值或小值
- 相关系数接近 -1 表示 $$X$$ 取大值时 $$Y$$ 取小值（反之亦然）

### 4.5.6 相关性的分类

**定义 4.5.3** (Definition 4.5.3)

- 若 $$\text{Cov}(X, Y) > 0$$，称 $$X$$ 和 $$Y$$ **正相关**（Positive Correlated）
- 若 $$\text{Cov}(X, Y) < 0$$，称 $$X$$ 和 $$Y$$ **负相关**（Negative Correlated）
- 若 $$\text{Cov}(X, Y) = 0$$，称 $$X$$ 和 $$Y$$ **不相关**（Uncorrelated）

### 4.5.7 独立性与相关性的关系

**备注 4.5.2** (Remark 4.5.2)

- 若 $$X$$ 和 $$Y$$ 不相关，意味着 $$X$$ 和 $$Y$$ 之间没有线性关系，但可能存在其他关系
- 由定理 4.1.6，若 $$X$$ 和 $$Y$$ 独立，则 $$E(XY) = E(X)E(Y)$$，$$\text{Cov}(X, Y) = 0$$
- 即：**独立性蕴含不相关性**
- 等价地，若 $$\text{Cov}(X, Y) \neq 0$$ 或 $$\rho_{X,Y} \neq 0$$，则 $$X$$ 和 $$Y$$ 不独立
- 然而，若 $$X$$ 和 $$Y$$ 不相关，它们可能是依赖的也可能是独立的
- **不相关的随机变量不一定独立！**

### 4.5.8 二元正态分布的相关性

**命题 4.5.3** (Proposition 4.5.3)

设 $$(X, Y)$$ 服从二元正态分布 $$N(\mu_1, \mu_2, \sigma_1^2, \sigma_2^2, \rho)$$，则参数 $$\rho$$ 恰好是 $$X$$ 和 $$Y$$ 的相关系数。

**重要性质**：设 $$(X, Y)$$ 服从二元正态分布，则 $$X$$ 和 $$Y$$ 独立当且仅当它们不相关（即 $$\rho = 0$$）。

---

## 4.6 矩与协方差矩阵 (Moments and Covariance Matrices)

### 4.6.1 矩的定义

**定义 4.6.1** (Definition 4.6.1)

设 $$X$$ 是随机变量，且 $$E(X^k)$$ 存在，$$k = 1, 2, \cdots$$：

- $$E(X^k)$$ 称为 $$X$$ 的 **$$k$$ 阶原点矩**（$$k$$-th Moment about the Origin）
- $$E\{[X - E(X)]^k\}$$（$$k = 2, 3, \cdots$$）若存在，称为 $$X$$ 的 **$$k$$ 阶中心矩**（$$k$$-th Central Moment）
- $$E\{[X - E(X)]^k [Y - E(Y)]^l\}$$（$$k, l = 1, 2, \cdots$$）若存在，称为 $$X$$ 和 $$Y$$ 的 **$$k+l$$ 阶混合中心矩**（Mixed Central Moment of Order $$k+l$$）

**重要说明**：

- 均值 $$E(X)$$ 是 $$X$$ 的一阶原点矩
- 方差 $$\text{Var}(X)$$ 是 $$X$$ 的二阶中心矩
- 协方差 $$\text{Cov}(X, Y)$$ 是 $$X$$ 和 $$Y$$ 的二元二阶混合中心矩

### 4.6.2 协方差矩阵的定义

**定义 4.6.2** (Definition 4.6.2)

设 $$(X_1, X_2)$$ 的二阶中心矩存在，记为：

$$
c_{11} = \text{Var}(X_1), \quad c_{22} = \text{Var}(X_2), \quad c_{12} = c_{21} = \text{Cov}(X_1, X_2)
$$

则矩阵：

$$
C = \begin{pmatrix} c_{11} & c_{12} \\ c_{21} & c_{22} \end{pmatrix}
$$

定义为 $$(X_1, X_2)$$ 的**协方差矩阵**（Covariance Matrix）。

**推广到 $$n$$ 维**：

$$(X_1, X_2, \cdots, X_n)$$ 的协方差矩阵定义为：

$$
C = \begin{pmatrix} c_{11} & c_{12} & \cdots & c_{1n} \\ c_{21} & c_{22} & \cdots & c_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ c_{n1} & c_{n2} & \cdots & c_{nn} \end{pmatrix}
$$

其中 $$c_{ij} = \text{Cov}(X_i, X_j)$$，$$i, j = 1, 2, \cdots, n$$。

由于 $$c_{ij} = c_{ji}$$（$$i \neq j$$），协方差矩阵是**对称矩阵**（Symmetric Matrix）。

### 4.6.3 二元正态分布的协方差矩阵表示

设 $$(X_1, X_2) \sim N(\mu_1, \mu_2, \sigma_1^2, \sigma_2^2, \rho)$$，则协方差矩阵为：

$$
C = \begin{pmatrix} \sigma_1^2 & \rho\sigma_1\sigma_2 \\ \rho\sigma_1\sigma_2 & \sigma_2^2 \end{pmatrix}
$$

### 4.6.4 非退化情况的概率密度函数

若 $$|C| \neq 0$$，则 $$C$$ 的逆矩阵存在，$$(X, Y)$$ 称为**非退化的**（Non-degenerate）。若 $$|C| = 0$$，$$(X, Y)$$ 是**退化的**（Degenerate），没有密度函数。

对于非退化情况，$$(X_1, X_2)$$ 的概率密度函数为：

$$
f(x_1, x_2) = \frac{1}{2\pi|C|^{1/2}} \exp\left\{-\frac{1}{2}(X - \mu)^T C^{-1} (X - \mu)\right\}
$$

其中 $$X = \begin{pmatrix} x_1 \\ x_2 \end{pmatrix}$$，$$\mu = \begin{pmatrix} \mu_1 \\ \mu_2 \end{pmatrix}$$，$$|C|$$ 和 $$C^{-1}$$ 分别是 $$C$$ 的行列式和逆矩阵，$$(X - \mu)^T$$ 是 $$(X - \mu)$$ 的转置。

### 4.6.5 $$n$$ 维正态分布

上述结果可推广到 $$n$$ 维正态随机向量 $$(X_1, X_2, \cdots, X_n)$$，概率密度函数为：

$$
f(x_1, \cdots, x_n) = \frac{1}{(2\pi)^{n/2}|C|^{1/2}} \exp\left\{-\frac{1}{2}(X - \mu)^T C^{-1} (X - \mu)\right\}
$$

### 4.6.6 $$n$$ 维正态分布的性质

$$n$$ 维正态随机向量 $$(X_1, \cdots, X_n)$$ 具有以下性质：

1. **边缘分布**：给定 $$n$$ 维正态随机向量 $$(X_1, \cdots, X_n)$$，其所有分量 $$X_i$$（$$i = 1, \cdots, n$$）都是正态随机变量；反之，若 $$X_i$$（$$i = 1, \cdots, n$$）是相互独立的正态随机变量，则 $$(X_1, \cdots, X_n)$$ 是 $$n$$ 维正态随机向量。

2. **线性组合**：$$(X_1, \cdots, X_n)$$ 服从 $$n$$ 维正态分布当且仅当其任意线性组合 $$a_1 X_1 + \cdots + a_n X_n$$ 服从正态分布（$$a_1, \cdots, a_n$$ 不全为零）。

3. **线性变换的不变性**：若 $$(X_1, \cdots, X_n)$$ 服从 $$n$$ 维正态分布，$$Y_1, Y_2, \cdots, Y_m$$ 是 $$X_i$$（$$i = 1, \cdots, n$$）的线性函数（系数不全为零），则 $$(Y_1, Y_2, \cdots, Y_m)$$ 服从 $$m$$ 维正态分布。

   > **注释**：这表明正态分布在线性变换下保持不变。上述 $$m$$ 维正态分布可能是退化的，没有密度函数。

4. **独立性与不相关性等价**：若 $$(X_1, \cdots, X_n)$$ 服从 $$n$$ 维正态分布，则 $$X_1, \cdots, X_n$$ 相互独立当且仅当它们两两不相关。

### 4.6.7 正态随机向量的线性变换

**定理 4.6.2** (Theorem 4.6.2)

若 $$(X_1, X_2) \sim N(\mu_1, \mu_2, \sigma_1^2, \sigma_2^2, \rho)$$，则：

$$
aX_1 + bX_2 \sim N(a\mu_1 + b\mu_2, a^2\sigma_1^2 + b^2\sigma_2^2 + 2ab\rho\sigma_1\sigma_2)
$$

---

## 关键术语中英对照表

| 中文              | 英文                                          |
| ----------------- | --------------------------------------------- |
| 期望/均值         | Expectation/Mean/Expected Value               |
| 方差              | Variance                                      |
| 标准差            | Standard Deviation                            |
| 概率分布律        | Probability Function (PF)                     |
| 概率密度函数      | Probability Density Function (PDF)            |
| 累积分布函数      | Cumulative Distribution Function (CDF)        |
| 伯努利分布        | Bernoulli Distribution                        |
| 二项分布          | Binomial Distribution                         |
| 泊松分布          | Poisson Distribution                          |
| 超几何分布        | Hypergeometric Distribution                   |
| 负二项分布        | Negative Binomial Distribution                |
| 均匀分布          | Uniform Distribution                          |
| 指数分布          | Exponential Distribution                      |
| 正态分布/高斯分布 | Normal/Gaussian Distribution                  |
| Gamma分布         | Gamma Distribution                            |
| 卡方分布          | Chi-squared Distribution                      |
| 切比雪夫不等式    | Chebyshev's Inequality                        |
| 协方差            | Covariance                                    |
| 相关系数          | Correlation Coefficient                       |
| 正相关            | Positive Correlated                           |
| 负相关            | Negative Correlated                           |
| 不相关            | Uncorrelated                                  |
| 独立              | Independent                                   |
| 矩                | Moment                                        |
| 原点矩            | Moment about the Origin                       |
| 中心矩            | Central Moment                                |
| 混合矩            | Mixed Moment                                  |
| 协方差矩阵        | Covariance Matrix                             |
| 对称矩阵          | Symmetric Matrix                              |
| 退化/非退化       | Degenerate/Non-degenerate                     |
| 标准化变量        | Standardized Variables                        |
| 二元正态分布      | Bivariate Normal Distribution                 |
| $$n$$ 维正态分布  | $$n$$-dimensional Normal Distribution         |
| 线性变换          | Linear Transformation                         |
| 独立同分布        | Independent and Identically Distributed (IID) |
