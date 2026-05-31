---
layout: post
title: 第9章 半群与群
date: 2026-05-20 10:00:00+0800
description: 半群与群的基本概念，包括二元运算、半群、群、陪集、正规子群、环与域等内容
tags: algebra math
categories: mathematics
toc:
  beginning: true
---

# 第9章 半群与群

---

## 第1节 二元运算回顾

**二元运算（Binary Operation）** 的定义：集合 $A$ 上的二元运算是一个处处有定义的函数 $f: A \times A \rightarrow A$。二元运算必须满足以下性质：

1. 由于 $\text{Dom}(f) = A \times A$，$f$ 为 $A \times A$ 中的每个有序对 $(a, b)$ 指定 $A$ 中的一个元素 $f(a, b)$。即二元运算必须对 $A$ 中的每个有序对元素都有定义。
2. 由于二元运算是函数，每个有序对只对应 $A$ 中唯一的一个元素。

因此，二元运算是将 $A$ 中元素的每个有序对映射到 $A$ 中唯一元素的规则。若 $a$ 和 $b$ 是 $A$ 中的元素，则 $a * b \in A$，这一性质常被称为 $A$ 对运算 $*$ **封闭（Closed）**。

通常用 $*$ 等符号表示二元运算（代替 $f$），并将 $(a, b)$ 对应的元素记为 $a * b$（代替 $*(a, b)$）。

**二元运算的性质：**

- **交换律（Commutative）**：若对 $A$ 中所有元素 $a$ 和 $b$，$a * b = b * a$，则称二元运算 $*$ 是**交换的**。
- **结合律（Associative）**：若对 $A$ 中所有元素 $a, b, c$，$a * (b * c) = (a * b) * c$，则称二元运算 $*$ 是**结合的**。
- **幂等律（Idempotent）**：若 $a * a = a$，则称运算满足幂等性。

**典型例题：**

> **例：** 设 $A = \{a, b, c, d\}$，以下哪个二元运算是交换的？
>
> $$(a) \quad \begin{array}{c|cccc} * & a & b & c & d \\ \hline a & a & c & b & d \\ b & b & c & b & a \\ c & c & d & c & b \\ d & a & a & b & b \end{array}$$
>
> $$(b) \quad \begin{array}{c|cccc} * & a & b & c & d \\ \hline a & a & c & b & d \\ b & b & c & d & a \\ c & c & d & b & a \\ d & d & a & a & c \end{array}$$
>
> **解答：** 运算 $(a)$ 不是交换的，因为 $a * b = c$ 而 $b * a = b$。运算 $(b)$ 是交换的，因为表中元素关于主对角线对称。

---

## 第2节 半群

**半群（Semigroup）** 的定义：半群是非空集合 $S$ 连同定义在 $S$ 上的一个结合二元运算 $*$。记作 $(S, *)$。若 $*$ 是交换的，则称该半群是**交换半群（Commutative Semigroup）**。

**典型例题：**

> $(\mathbb{Z}, +)$ 是一个交换半群。集合 $P(S)$（$S$ 的幂集）在并运算下是交换半群。集合 $\mathbb{Z}$ 在减法运算下不是半群，因为减法不满足结合律。

**恒等元（Identity Element）** 的定义：半群 $(S, *)$ 中的元素 $e$ 称为**恒等元**，如果对所有 $a \in S$，$e * a = a * e = a$。恒等元必须是唯一的。

**幺半群（Monoid）** 的定义：具有恒等元的半群 $(S, *)$ 称为**幺半群**。

**典型例题：**

> $P(S)$ 在并运算下是幺半群，恒等元为 $\varnothing$。$A^*$（字母表 $A$ 上所有有限序列的集合）在连接运算下是幺半群，恒等元为空序列 $\Lambda$。

**子半群（Subsemigroup）** 和 **子幺半群（Submonoid）** 的定义：

- 设 $(S, *)$ 为半群，$T \subseteq S$。若 $T$ 对运算 $*$ 封闭（即当 $a, b \in T$ 时 $a * b \in T$），则 $(T, *)$ 称为 $(S, *)$ 的**子半群**。
- 设 $(S, *)$ 为幺半群（恒等元为 $e$），$T \subseteq S$。若 $T$ 对运算 $*$ 封闭且 $e \in T$，则 $(T, *)$ 称为 $(S, *)$ 的**子幺半群**。

**幂的递归定义：** 设 $(S, *)$ 为半群，$a \in S$，对 $n \in \mathbb{Z}^+$，递归定义 $a$ 的**幂（Power）**：

$$a^1 = a, \quad a^n = a^{n-1} * a, \quad n \geq 2$$

若 $(S, *)$ 是幺半群，还定义 $a^0 = e$。可以证明：若 $m, n$ 为非负整数，则 $a^m * a^n = a^{m+n}$。

**同构（Isomorphism）** 和 **同态（Homomorphism）** 的定义：

设 $(S, *)$ 和 $(T, *')$ 为两个半群。函数 $f: S \rightarrow T$ 称为从 $(S, *)$ 到 $(T, *')$ 的**同构**，如果 $f$ 是 $S$ 到 $T$ 的一一对应，且对所有 $a, b \in S$：

$$f(a * b) = f(a) *' f(b)$$

若存在从 $(S, *)$ 到 $(T, *')$ 的同构，则称这两个半群**同构（Isomorphic）**，记作 $S \cong T$。

**证明两个半群同构的步骤：**

1. 定义函数 $f: S \rightarrow T$
2. 证明 $f$ 是单射
3. 证明 $f$ 是满射
4. 证明 $f(a * b) = f(a) *' f(b)$

---

## 第3节 半群的积与商

**定理：** 若 $(S, *)$ 和 $(T, *')$ 是半群，则 $(S \times T, *'')$ 是半群，其中 $*''$ 定义为：

$$(s_1, t_1) *'' (s_2, t_2) = (s_1 * s_2, t_1 *' t_2)$$

**相容关系（Congruence Relation）** 的定义：半群 $(S, *)$ 上的等价关系 $R$ 称为**相容关系**，如果

$$aRa' \text{ 且 } bRb' \implies (a * b)R(a' * b')$$

**定理：** 设 $R$ 是半群 $(S, *)$ 上的相容关系。考虑从 $S/R \times S/R$ 到 $S/R$ 的关系 $\clubsuit$，将有序对 $([a], [b])$ 映射到 $[a * b]$。则：

(a) $\clubsuit$ 是从 $S/R \times S/R$ 到 $S/R$ 的函数，记 $([a], [b])$ 对应的元素为 $[a] \clubsuit [b] = [a * b]$。

(b) $(S/R, \clubsuit)$ 是一个半群。

我们称 $S/R$ 为**商半群（Quotient Semigroup）** 或**因子半群（Factor Semigroup）**。

---

## 第4节 群

**群（Group）** 的定义：群 $(G, *)$ 是具有恒等元 $e$ 的幺半群，并具有附加性质：对每个 $a \in G$，存在 $a' \in G$ 使得 $a * a' = a' * a = e$。

即群是一个集合 $G$ 连同二元运算 $*$，满足：

1. **结合律**：对任意 $a, b, c \in G$，$(a * b) * c = a * (b * c)$
2. **恒等元**：存在唯一元素 $e \in G$，使得对任意 $a \in G$，$a * e = e * a$
3. **逆元（Inverse）**：对每个 $a \in G$，存在 $a' \in G$，称为 $a$ 的**逆元**，使得 $a * a' = a' * a = e$

**阿贝尔群（Abelian Group）** 的定义：若群 $G$ 对所有元素 $a, b \in G$ 满足 $ab = ba$，则称 $G$ 为**阿贝尔群**（或交换群）。

**典型例题：**

> 设 $G$ 为所有非零实数的集合，定义 $a * b = \dfrac{ab}{2}$。证明 $(G, *)$ 是一个阿贝尔群。
>
> **解答：**
>
> - 封闭性：若 $a, b \in G$，则 $ab/2$ 是非零实数，属于 $G$。
> - 结合律：$(a * b) * c = \dfrac{(ab)c}{4}$，$a * (b * c) = \dfrac{a(bc)}{4} = \dfrac{(ab)c}{4}$。
> - 恒等元：$2$ 是恒等元，因为 $a * 2 = \dfrac{(a)(2)}{2} = a$。
> - 逆元：$a$ 的逆元为 $a' = 4/a$，因为 $a * \dfrac{4}{a} = \dfrac{a(4/a)}{2} = 2 = e$。
> - 交换律：$a * b = \dfrac{ab}{2} = \dfrac{ba}{2} = b * a$。
>
> 因此 $(G, *)$ 是阿贝尔群。

**群的重要定理：**

> **定理 1：** 群 $G$ 中每个元素 $a$ 有唯一的逆元。
>
> **推论：** 从现在起，将 $a$ 的逆元记为 $a^{-1}$。即 $aa^{-1} = a^{-1}a = e$。

> **定理 2：** 设 $G$ 为群，$a, b, c \in G$。则：
>
> - (a) $ab = ac \implies b = c$（**左消去律（Left Cancellation Property）**）
> - (b) $ba = ca \implies b = c$（**右消去律（Right Cancellation Property）**）

> **定理 3：** 设 $G$ 为群，$a, b \in G$。则：
>
> - (a) $(a^{-1})^{-1} = a$
> - (b) $(ab)^{-1} = b^{-1}a^{-1}$

> **定理 4：** 设 $G$ 为群，$a, b \in G$。则：
>
> - (a) 方程 $ax = b$ 在 $G$ 中有唯一解
> - (b) 方程 $ya = b$ 在 $G$ 中有唯一解

**有限群（Finite Group）**：若群 $G$ 有有限个元素，则称 $G$ 为有限群，$G$ 的**阶（Order）** 是 $G$ 中元素的个数 $|G|$。

**典型例题——三角形的对称群：**

> 考虑顶点为 $1, 2, 3$ 的等边三角形。三角形的**对称（Symmetry）** 是保持相邻点间距离的顶点的一一对应。
>
> 三种旋转：
>
> - $f_1 = \begin{pmatrix} 1 & 2 & 3 \\ 1 & 2 & 3 \end{pmatrix}$（旋转 $0°$）
> - $f_2 = \begin{pmatrix} 1 & 2 & 3 \\ 2 & 3 & 1 \end{pmatrix}$（逆时针旋转 $120°$）
> - $f_3 = \begin{pmatrix} 1 & 2 & 3 \\ 3 & 1 & 2 \end{pmatrix}$（逆时针旋转 $240°$）
>
> 三种反射：
>
> - $g_1 = \begin{pmatrix} 1 & 2 & 3 \\ 1 & 3 & 2 \end{pmatrix}$，$g_2 = \begin{pmatrix} 1 & 2 & 3 \\ 3 & 2 & 1 \end{pmatrix}$，$g_3 = \begin{pmatrix} 1 & 2 & 3 \\ 2 & 1 & 3 \end{pmatrix}$
>
> 所有对称的集合 $S_3 = \{f_1, f_2, f_3, g_1, g_2, g_3\}$ 在复合运算下构成群，称为**三角形的对称群（Group of Symmetries of the Triangle）**。这是第一个非阿贝尔群的例子。

**对称群（Symmetric Group）** 的定义：$n$ 个元素的所有排列在复合运算下构成阶为 $n!$ 的群，称为 $n$ 个字母上的**对称群**，记为 $S_n$。

**子群（Subgroup）** 的定义：设 $H$ 是群 $G$ 的子集，若满足：

- (a) $G$ 的恒等元 $e$ 属于 $H$
- (b) 若 $a, b \in H$，则 $ab \in H$
- (c) 若 $a \in H$，则 $a^{-1} \in H$

则称 $H$ 为 $G$ 的**子群**。

**典型例题：**

> - $G$ 本身和 $H = \{e\}$ 是 $G$ 的子群，称为**平凡子群（Trivial Subgroups）**。
> - 设 $G$ 为群，$a \in G$。$H = \{a^i \mid i \in \mathbb{Z}\}$ 是 $G$ 的子群。

**群同态定理：**

> **定理 5：** 设 $(G, *)$ 和 $(G', *')$ 为两个群，$f: G \rightarrow G'$ 为群同态。
>
> - (a) 若 $e$ 为 $G$ 的恒等元，$e'$ 为 $G'$ 的恒等元，则 $f(e) = e'$。
> - (b) 若 $a \in G$，则 $f(a^{-1}) = (f(a))^{-1}$。
> - (c) 若 $H$ 是 $G$ 的子群，则 $f(H) = \{f(h) \mid h \in H\}$ 是 $G'$ 的子群。

---

## 第5节 群的积与商

**定理 1（群的直积）：** 若 $G_1$ 和 $G_2$ 是群，则 $G = G_1 \times G_2$ 是群，其中二元运算定义为：

$$(a_1, b_1)(a_2, b_2) = (a_1 a_2, b_1 b_2)$$

**典型例题：**

> 令 $G_1 = G_2 = \mathbb{Z}_2$，则 $G = \mathbb{Z}_2 \times \mathbb{Z}_2$ 的乘法表如下：
>
> | $\cdot$ | $(0,0)$ | $(1,0)$ | $(0,1)$ | $(1,1)$ |
> | ------- | ------- | ------- | ------- | ------- |
> | $(0,0)$ | $(0,0)$ | $(1,0)$ | $(0,1)$ | $(1,1)$ |
> | $(1,0)$ | $(1,0)$ | $(0,0)$ | $(1,1)$ | $(0,1)$ |
> | $(0,1)$ | $(0,1)$ | $(1,1)$ | $(0,0)$ | $(1,0)$ |
> | $(1,1)$ | $(1,1)$ | $(0,1)$ | $(1,0)$ | $(0,0)$ |
>
> 该群同构于 Klein 四元群 $V$。

**一般结论：** $\mathbb{Z}_m \times \mathbb{Z}_n \cong \mathbb{Z}_{mn}$ 当且仅当 $\gcd(m, n) = 1$（即 $m$ 和 $n$ 互素）。

**陪集（Coset）** 的定义：

- 设 $H$ 为群 $G$ 的子群，$a \in G$。$H$ 在 $G$ 中由 $a$ 确定的**左陪集（Left Coset）** 为 $aH = \{ah \mid h \in H\}$。
- $H$ 在 $G$ 中由 $a$ 确定的**右陪集（Right Coset）** 为 $Ha = \{ha \mid h \in H\}$。

**正规子群（Normal Subgroup）** 的定义：若对所有 $a \in G$，$aH = Ha$，则称子群 $H$ 为 $G$ 的**正规子群**。

**定理 2：** 设 $R$ 是群 $(G, *)$ 上的相容关系，则商结构 $(G/R, \clubsuit)$ 是群，其中运算定义为 $[a] \clubsuit [b] = [a * b]$。

**定理 3：** 设 $R$ 是群 $G$ 上的相容关系，$H = [e]$ 为包含恒等元的等价类。则 $H$ 是 $G$ 的正规子群，且对每个 $a \in G$，$[a] = aH = Ha$。

**定理 4：** 设 $N$ 是群 $G$ 的正规子群，在 $G$ 上定义关系 $R$：

$$aRb \iff a^{-1}b \in N$$

则：

- (a) $R$ 是 $G$ 上的相容关系。
- (b) $N$ 是相对于 $R$ 的等价类 $[e]$。

**核心推论——群同态基本定理（First Isomorphism Theorem）：** 设 $f$ 是从群 $(G, *)$ 到群 $(G', *')$ 的满同态，定义 **核（Kernel）** $\ker(f) = \{a \in G \mid f(a) = e'\}$。则：

- (a) $\ker(f)$ 是 $G$ 的正规子群。
- (b) 商群 $G/\ker(f)$ 同构于 $G'$。

**典型例题：**

> 考虑从 $\mathbb{Z}$ 到 $\mathbb{Z}_n$ 的满同态 $f(m) = [r]$，其中 $r$ 为 $m$ 除以 $n$ 的余数。求 $\ker(f)$。
>
> **解答：** 整数 $m$ 属于 $\ker(f)$ 当且仅当 $f(m) = [0]$，即 $m$ 是 $n$ 的倍数。因此 $\ker(f) = n\mathbb{Z}$。

---

## 第6节 其他数学结构

### 环

**环（Ring）** 的定义：设 $S$ 为非空集合，具有两个二元运算 $+$ 和 $*$，使得 $(S, +)$ 是阿贝尔群，$*$ 对 $+$ 满足**分配律（Distributive）**。若 $*$ 是结合的，则 $(S, +, *)$ 称为**环**。

若 $*$ 还是交换的，则称 $(S, +, *)$ 为**交换环（Commutative Ring）**。

若 $(S, *)$ 是幺半群，则称 $(S, +, *)$ 为**含幺环（Ring with Identity）**。$*$ 的恒等元通常记为 $1$；$+$ 的恒等元通常记为 $0$。

**典型例题：**

> - $\mathbb{Z}$（整数集）在普通加法和乘法下是含幺交换环。
> - 所有 $2 \times 2$ 矩阵在矩阵加法和乘法下是非交换环。单位矩阵 $I$ 是乘法恒等元。
> - $\mathbb{Z}_n$ 在模 $n$ 加法和乘法下是含幺交换环。

**定理 1：** 设 $R$ 为含幺交换环（加法恒等元为 $0$，乘法恒等元为 $1$）。则：

- (a) 对任意 $x \in R$，$0 * x = 0$。
- (b) 对任意 $x \in R$，$-x = (-1) * x$。

**乘法逆元（Multiplicative Inverse）**：若环 $R$ 中的非零元素 $x$ 满足 $x * y = y * x = 1$，则称 $y$ 为 $x$ 的**乘法逆元**，记为 $x^{-1}$ 或 $1/x$。

**典型例题——求 $\mathbb{Z}_{384}$ 中 $\overline{25}$ 的乘法逆元：**

> 因为 $\gcd(25, 384) = 1$，所以 $\overline{25}$ 在 $\mathbb{Z}_{384}$ 中有乘法逆元。使用辗转相除法（Euclidean Algorithm）：
>
> $$384 = 15 \times 25 + 9$$
> $$25 = 2 \times 9 + 7$$
> $$9 = 1 \times 7 + 2$$
> $$7 = 3 \times 2 + 1$$
>
> 逆向回代得：$1 = 169 \times 25 - 11 \times 384$。因此 $169 \cdot 25 \equiv 1 \pmod{384}$，即 $\overline{25}$ 在 $\mathbb{Z}_{384}$ 中的乘法逆元为 $169$。

### 域

**域（Field）** 的定义：若 $F$ 是含幺交换环，且每个非零元素 $x \in F$ 都有乘法逆元，则称 $F$ 为**域**。

**域的性质总结：**

$F$ 有两个二元运算（加法 $+$ 和乘法 $*$）和两个特殊元素（$0$ 和 $1$），对所有 $x, y, z \in F$：

| 编号 | 性质                              | 编号 | 性质                                                 |
| ---- | --------------------------------- | ---- | ---------------------------------------------------- |
| (1)  | $x + y = y + x$                   | (2)  | $x * y = y * x$                                      |
| (3)  | $(x + y) + z = x + (y + z)$       | (4)  | $(x * y) * z = x * (y * z)$                          |
| (5)  | $x + 0 = x$                       | (6)  | $x * 1 = x$                                          |
| (7)  | $x * (y + z) = (x * y) + (x * z)$ | (8)  | $(y + z) * x = (y * x) + (z * x)$                    |
| (9)  | $\exists!(-x): x + (-x) = 0$      | (10) | $\forall x \neq 0, \exists!(x^{-1}): x * x^{-1} = 1$ |

**典型例题：**

> $\mathbb{R}$（实数集）、$\mathbb{Q}$（有理数集）在普通加法和乘法下都是域。

**定理 2：** 当 $n$ 为**素数（Prime）** 时，$\mathbb{Z}_n$ 是域。

**费马小定理（Fermat's Little Theorem）：**

> **定理 3：**
>
> - (a) 若 $G = \{g_1, g_2, \ldots, g_n\}$ 是有限阿贝尔群（恒等元为 $e$），$a$ 为 $G$ 中任意元素，则 $a^n = e$。
> - (b)（**费马小定理**）若 $p$ 为素数且 $\gcd(a, p) = 1$，则 $a^{p-1} \equiv 1 \pmod{p}$。
> - (c) 若 $p$ 为素数，$a$ 为任意整数，则 $a^p \equiv a \pmod{p}$。

**典型例题——利用费马小定理求余数：**

> 求 $4^{900}$ 除以 $53$ 的余数。
>
> **解答：** 由费马小定理知 $4^{52} \equiv 1 \pmod{53}$。由于
> $$900 = 17 \times 52 + 16$$
> 故
> $$4^{900} = (4^{52})^{17} \cdot 4^{16} \equiv 4^{16} \pmod{53}$$
>
> 计算：
>
> - $4^3 = 64 \equiv 11 \pmod{53}$
> - $4^6 \equiv 11^2 = 121 \equiv 15 \pmod{53}$
> - $4^{12} \equiv 15^2 = 225 \equiv 13 \pmod{53}$
> - $4^{16} = 4^{12} \cdot 4^4 \equiv 13 \cdot 256 \equiv 13 \cdot 44 \equiv 572 \equiv 21 \pmod{53}$
>
> 因此 $4^{900}$ 除以 $53$ 的余数为 $21$。

---

## 关键词对照表

| 中文术语                       | 英文术语                              |
| ------------------------------ | ------------------------------------- |
| 二元运算                       | Binary Operation                      |
| 封闭                           | Closed                                |
| 交换律                         | Commutative                           |
| 结合律                         | Associative                           |
| 幂等律                         | Idempotent                            |
| 半群                           | Semigroup                             |
| 交换半群                       | Commutative Semigroup                 |
| 恒等元                         | Identity Element                      |
| 幺半群                         | Monoid                                |
| 子半群                         | Subsemigroup                          |
| 子幺半群                       | Submonoid                             |
| 幂                             | Power                                 |
| 同构                           | Isomorphism                           |
| 同态                           | Homomorphism                          |
| 相容关系                       | Congruence Relation                   |
| 商半群（因子半群）             | Quotient Semigroup (Factor Semigroup) |
| 群                             | Group                                 |
| 阿贝尔群（交换群）             | Abelian Group                         |
| 逆元                           | Inverse                               |
| 左消去律                       | Left Cancellation Property            |
| 右消去律                       | Right Cancellation Property           |
| 有限群                         | Finite Group                          |
| 阶                             | Order                                 |
| 对称                           | Symmetry                              |
| 对称群                         | Symmetric Group                       |
| 子群                           | Subgroup                              |
| 平凡子群                       | Trivial Subgroups                     |
| 左陪集                         | Left Coset                            |
| 右陪集                         | Right Coset                           |
| 正规子群                       | Normal Subgroup                       |
| 核                             | Kernel                                |
| 群同态基本定理（第一同构定理） | First Isomorphism Theorem             |
| 环                             | Ring                                  |
| 交换环                         | Commutative Ring                      |
| 含幺环                         | Ring with Identity                    |
| 分配律                         | Distributive                          |
| 乘法逆元                       | Multiplicative Inverse                |
| 域                             | Field                                 |
| 素数                           | Prime                                 |
| 费马小定理                     | Fermat's Little Theorem               |
| 辗转相除法（欧几里得算法）     | Euclidean Algorithm                   |
| Klein 四元群                   | Klein 4-group                         |
| 交替群                         | Alternating Group                     |
