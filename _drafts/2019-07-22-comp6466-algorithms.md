---
layout: post-mathjax
title: COMP6466 - Algorithms
---

# 1. asymptotic analysis

* asymoptotic notation.

| notation                        | $$\displaystyle\lim_{n \rightarrow \infty} \frac{f(n)}{g(n)} = $$ (L' Hopital Rule) | comparing algorithms |
| ------------------------------- | ----------------------------------------------------------------------------------- | -------------------- |
| big-oh, $$O(g(n))$$.            | 0 or c(positive and constant).                                                      | $$a \leq b$$.        |
| little-oh, $$o(g(n))$$.         | 0.                                                                                  | $$a < b$$.           |
| big-omega, $$\Omega(g(n))$$.    | $$\infty$$ or c.                                                                    | $$a \geq b$$.        |
| little-omega, $$\omega(g(n))$$. | $$\infty$$.                                                                         | $$a > b$$.           |
| theta, $$\theta(g(n))$$.        | c.                                                                                  | $$a = b$$.           |

* asymoptotic analysis of insertion sort.
  * best case: $$\theta(n)$$.
  * worst case: $$\theta(n^2)$$.

* some functions cannot be compared asymptotically.

# 2. recurrence analysis

* recurrence: describe a function in terms of value(s) of the function on smaller input(s).

* running time of merge sort.
  
  $$T(n) = T(\lceil \frac n 2 \rceil) + T(\lfloor \frac n 2 \rfloor) + \theta(n) =\begin{cases} \theta(1), & \text{n = 1} \\ 2T(\lfloor \frac n 2 \rfloor) + \theta(n), & \text{n > 1} \end{cases}$$.

* solving recurrence by substitution.
  * guessing the form of the solution.
  * mathemtiacal induction to find the constant.

​	// todo4
