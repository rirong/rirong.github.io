---
layout: post-mathjax
title: ENGN8534 - Information Theory
---

<!-- \mid, \parallel or \vert represents | or || -->

# 1. entropy

* entropy: a measure of uncertainty of a random variable. $$H(X) = \displaystyle\sum_{x \in X} p(x) log{\frac{1}{p(x)}}$$.

* depends on the probabilities. $$H(X) = H(p)$$.

* expectation of function g(x) over distribution p(x). $$E_p g(X) = \displaystyle\sum_{x \in X} p(x) g(x)$$.  

  $$\Rightarrow H(X) = E_p log{\frac{1}{p(x)}}$$.

* information is non-negative. $$H(X) \geq 0$$.

* change the base of entropy. $$H_b(X) = (log_ba) H_a(X)$$.

* joint entropy: joint average amount of information in two random variables X and Y with joint distribution p(x, y). $$H(X, Y) = \displaystyle\sum_{x \in X} \displaystyle\sum_{y \in Y} p(x, y) log{\frac{1}{p(x, y)}} = E_p log{\frac{1}{p(x, y)}}$$.

* conditional entropy: the average additional information in Y with known X when (X, Y) ~ p(x,y). $$H(Y \mid X) = \displaystyle\sum_{x \in X} p(x) H(Y \mid X = x)  = \displaystyle\sum_{x \in X} p(x) \displaystyle\sum_{x \in X} p(y \mid x) log{\frac{1}{p(y \mid x)}}$$
  
  $$= \displaystyle\sum_{x \in X} \displaystyle\sum_{x \in X} p(x, y) log{\frac{1}{p(y \mid x)}} = E_{p(x, y)} log{\frac{1}{p(y \mid x)}}$$.

* entropy of function $$Y = f(X)$$.  
  $$H(Y \mid X) = \displaystyle\sum_{x \in X} p(x) H(Y \mid X = x) = \displaystyle\sum_{x \in X} p(y \mid x) \log{\frac 1 {p(y \mid x)}}$$.
  $$p(y \mid x) = 1$$, so $$H(Y \mid X) = 0$$.

* chain rule for entropy. $$H(X, Y) = H(X) + H(Y \mid X)$$.

  $$H(X, Y, Z) = H(X) + H(Y \mid X) + H(Z \mid X, Y)$$.

  $$H(X_1, \cdots, X_n) = \displaystyle\sum_{i = 1}^n H(X_i \mid X_1, \cdots, X_{i - 1})$$.

* chain rule for conditional entropy. $$H(X, Y \mid Z) = H(X \mid Z) + H(Y \mid X, Z)$$.

  $$H(X_1, \cdots, X_n \mid Z) = \displaystyle\sum_{i = 1}^n H(X_i \mid X_1, \cdots, X_{i - 1}, Z)$$.

# 2. mutual Information

* mutual information: the amount of information revealed about X after knowing Y. $$I(X; Y) = H(X) - H(X \mid Y)$$.

  $$I(X; Y) = H(X) - H(X \mid Y) = H(X) - (H(X, Y) - H(Y))$$

  $$= H(X) + H(Y) - H(X, Y) = H(Y) - (H(X, Y) - H(X)) = H(Y) + H(X) - H(X, Y)$$

  $$= H(Y) - H(Y \mid X) = I(Y; X)$$.

* chain rule for mutual information. $$I(X_1, X_2; Y) = I(X_1; Y) + I(X_2; Y \mid X_1)$$.

  $$I(X_1, \cdots, X_n ; Y) = \displaystyle\sum_{i = 1}^n I(X_i; Y \mid X_1, \cdots, X_{i - 1})$$.

* if X and Y are independent, $$H(Y) = H(Y \mid X)$$. $$I(X; Y) = 0$$.

* if $$H(Y \mid X) = 0$$, full information about Y is resolved after observing X, $$I(X; Y) = H(Y)$$.

* relative entropy: a measure of distance between two probability distributions p and q. $$D(p \parallel q) = \displaystyle\sum_{x \in X} p(x) log{\frac{p(x)}{q(x)}} = \displaystyle\sum_{x \in X} p(x) log p(x) + \displaystyle\sum_{x \in X} p(x) log{\frac{1}{q(x)}}$$

  $$ = -H(p) + \displaystyle\sum_{x \in X} p(x) log{\frac{1}{q(x)}}$$.

* in general, $$D(p \parallel q) \not= D(q \parallel p)$$.

* if p(x) = q(x), $$D(p \parallel q) = 0$$.

* $$\exists x \in X; p(x) > 0, q(x) = 0 \Rightarrow p(x) log{\frac{p(x)}{0}} = \infty$$.

* mutual information is a measure of dependence of two random variables. $$D(p(x,y) \parallel p(x)p(y))  = \displaystyle\sum_{x \in X} \displaystyle\sum_{y \in Y} p(x, y) log{\frac{p(x, y)}{p(x)p(y)}} = -H(X, Y) + H(X) + H(Y)$$

  $$= I(X; Y)$$.

* convex function. $$\frac{d^2f(x)}{dx^2} \geq 0$$.

* Jensen's inequality. f is a convex function, $$E[f(x)] \geq f(E[X])$$, or $$\displaystyle\sum_{i = 1}^m p(x_i) f(x_i) \geq f(\displaystyle\sum_{i = 1}^m p(x_i) x_i) $$, or $$\overline{f(X)} \geq f(\overline X)$$.

* let $$f(x) = log{\frac{q(x)}{p(x)}}$$,

  $$D(p \parallel q) = \displaystyle\sum_{x \in X} p(x) log{\frac{p(x)}{q(x)}} = -\displaystyle\sum_{x \in X} p(x) log{\frac{q(x)}{p(x)}}$$

  $$= -\overline{f(X)} \geq -f(\overline X) = -log\displaystyle\sum_{x \in X} p(x) \frac{q(x)}{p(x)} = -log\displaystyle\sum_{x \in X} q(x)$$

  $$= -log1 = 0$$.

* mutual information is non-negative. $$I(X; Y) = D(p(x,y) \parallel p(x)p(y)) \geq 0$$.

  $$I(X; Y) = 0 \Leftrightarrow p(x, y) = p(x) p(y)$$.

* conditioning reduces entropy. information cannot hurt. $$H(X \mid Y) \leq H(X)$$.

* uniform distribution over X achieves the maximum entropy of $$\log \vert X \vert$$ among all distributions over X. $$H(X) \leq \log \vert X \vert.$$

# 3. source code

* codeword corresponding to x, C(x). length of C(x), l(x). 

  the expected length $$L(C) = \displaystyle\sum_{x \in X} p(x) l(x) = Ep\{l(x)\}$$.

*   Classes of source codes.

  * singular codes. $$x_1 \not= x_2$$, but $$C(x_1) = C(x_2)$$.
  * non-sigular codes. $$x_1 \not= x_2  \Rightarrow C(x_1) = C(x_2)$$.
    * non-uniquely decodable. some extension codes are singular.
    * uniquely decodable: the extension code is non-sigular.
      * non-prefix.
      * prefix, self-punctuating code.  no codeword is a prefix of any other code.

* code tree of prefix codes. 
  * branch. D-ary, D-branches.
  * leaf: last node of a branch.
  * code: reach along the root node to the leaf.

* Kraft inequality. $$X = \{1, 2, \cdots, m\}$$, corresponding codeword lengths are $$l_1, l_2, \cdots, l_m$$, an alphabet of size D. 

  prefix codes $$\Leftrightarrow \displaystyle\sum_{i = 1}^m D^{-l_i} \leq 1$$.

* visual proof of forward. prefix code $$\Rightarrow$$ tree $$\Rightarrow$$ weight $$2^{-l}$$ at depth l $$\Rightarrow$$ total sum of weights is 1. Equality is achieved if all leaves are used as codewords.

* extension of countably infinite set of codewords. prefix codes $$\Leftrightarrow \displaystyle\sum_{i = 1}^{\infty} D^{-l_i} \leq 1$$.

* proof of forward, also work for finite set.
  * the i-th codeword $$y_1 y_2 \cdots y_{l_i}$$ of $$l_i$$ of a prefix code.
  * real number given by its D-ary expansion $$y = 0. y_1  y_2 \cdots y_{l_i} = \displaystyle\sum_{k = 1}^{l_i} y_k D^{-k} \in \{0, 1\}$$.
  * $$y' = 0. y_1  y_2 \cdots y_{l_i} y_{l_{i + 1}} \cdots$$ In D-ary format, the max is $$y' = y + \displaystyle\sum_{k = l_{i + 1}}^{\infty} (D - 1) D^{-k} = y + D^{-l_i}$$.
  * the code is a prefix code so the interval $$[y, y + D^{-l_i})$$ of length $$D^{-l_i}$$ cannot contain any other codewords.
  * the interval $$[y, y + D^{-l_i})$$ is uniquely and disjointly corresponds to codeword $$y_1  y_2 \cdots y_{l_i}$$ on the unit interval $$[0, 1)$$.

* Shannon code construction.
  * first codeword $$c_1$$. $$[0,  D^{-l_1})$$.
  * second codewrod $$c_2$$. $$[D^{-l_1},  D^{-l_1} + D^{-l_2})$$.
  * j-th codeword $$c_j$$. $$[\displaystyle\sum_{k = 1}^{j - 1} D^{-l_k}, \displaystyle\sum_{k = 1}^{j} D^{-l_k})$$.
  * proof of converse: codeword $$c_k$$ cannot be prefix of $$c_j$$ for $$k < j$$, they differ in the first $$l_k$$ digits.

* minimum / optimal code length $$L(C) \geq H_D(X)$$.

  equality achieved $$\Leftrightarrow D^{-l_1} = p_i$$ or $$\log_D{\frac{1}{p_i}} = l_i$$ is an integer for all i $$\Leftrightarrow L(C) = H(X)$$.

* achievable code length, $$l_i = \log_D{\frac{1}{p_i}}$$ is not an integer, round it up $$l_i = \lceil \log_D{\frac{1}{p_i}} \rceil$$.

  $$\Rightarrow H(X) \leq L(C) < H(X) + 1$$.

* Shannon code with wrong distribution

* the expected length under p(x) of the code length assignment $$l_i = \lceil \log_D{\frac{1}{p_i}} \rceil$$.

  $$\Rightarrow H(p) + D(p \parallel q) \leq EpI(X) < H(p) + D(p \parallel q) + 1$$.

  relative entropy is cost of misscoding.

* Shannon-Fano-Elias code.
  * cumulative distribution function(CDF). $$F(x) = \displaystyle\sum_{i = 1}^{x} p(i)$$.
  * modified CDF is midway between jumps in the CDF. $$\overline F(x) = \displaystyle\sum_{i = 1}^{x - 1} p(i) + \frac{1}{2} p(x) = F(x - 1) + \frac{1}{2} p(x) $$.

* Huffman code is an optimal source code.
  * codeword lengths are inversely ordered with probabilities. $$p_j > p_k \Rightarrow l_j \leq l_k$$.
  * no unused leaves in a tree corresponding to an optimal code. $$\Rightarrow$$ Two least probable codewords are of the same length, the code tree can be constructed such that these codewords differ only in the last bit.

* Huffman code construction.
  1. sort the symbolds according to their decreasing probablities.
  2. let $$x_j$$ and $$x_{j'}$$ be the least two probable symbols in the list with probabilities $$p_j$$ and $$p_{j'}$$ respectively.
  3. remove $$x_j$$ and $$x_{j'}$$ from the list and connect them in a binary tree.
  4. add the root node $$\{x_j, x_{j'}\}$$ as one symbol with probability $$p_j + p_{j'}$$.
  5. if there is only on symbol in the list, stop, otherwise go to step 2.

* Huffman code vs Shannon code.
  * Shannon code can assign unnecessarily long codes to some symbols.
  * the length for a particular Shannon codeword $$\lceil \log{\frac{1}{p}} \rceil$$ could less than the length of Huffman code.

  



// todo maybe not all the proof should be added into the note!!!!!!