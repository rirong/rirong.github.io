---
layout: post-mathjax
title: Machine Learning
---

# 1.introduction

* machine learning: a branch of artificial intelligence, concerned with the design and development of algorithms that allow computers to evolve behaviours based on empirical data.
* training and testing. universal set (unobserved), training set (obeserved) $$\subseteq$$ universal set, testing set $$\subseteq$$ universal set.
* types of machine learning.
	* supervised learning: regression, classification.
	
	* unsupervised learning: clustering, dimensionality reduction.
	
	* seme-supervised learning.

* applications: image classification and generative models.

# 2.linear algebra

* vector, elements of $$R^n$$ (tuples of n real numbers).

* systems of linear equations. $$a_{ij}$$ known coefficient, $$(x_1, \cdots, x_n)$$ unknown, $$\displaystyle\sum_{j=1}^n a_{ij}x_j = b_i (i = 1, \cdots, m).$$

* matrix $$A = \begin {bmatrix}{a_{11}}&{a_{12}}&{\cdots}&{a_{1n}}\\ {a_{21}}&{a_{22}}&{\cdots}&{a_{2n}}\\ {\vdots}&{\vdots}&{\ddots}&{\vdots}\\ {a_{m1}}&{a_{m2}}&{\cdots}&{a_{mn}}\\ \end{bmatrix} \begin {bmatrix} {x_1}\\ {x_2}\\ {\vdots}\\ {x_n} \end{bmatrix}= \begin {bmatrix} {b_1}\\ {b_2}\\ {\vdots}\\ {x_n}\\ \end{bmatrix}, a_{ij} \in R.$$

* (m, n) matrix with m rows and n columns, or with m (1, n) row vectors and n (m, 1) column vectors.

* matrix addition and multiplication. associativity and distributivity. multiplication by a scalar.

* indentity matrix and inverse.
  * multiplication with identity matrix. $$\forall A \in R^{m \times n}: I_m A = A I_n = A,\ I_m \not= I_n \ for\ m \not= n.$$
  * inverse for square matrix $$A \in R^{n \times m}.$$ $$AB = I_n = BA.$$ $$B = A^{-1}$$
  * $$AA^{-1}=I=A^{-1}A.$$
  * $$(AB)^{-1}=B^{-1}A^{-1}.$$
  
* transpose. for $$A \in R^{m \times n}, \ B \in R^{n \times m}$$ with $$ b_{ij} = a_{ji}$$ is the transpose of A. $$B = A^T.$$
  * $$(A^T)^T = A.$$
  * $$(A + B)^T = A^T + B^T.$$
  * $$(AB)^T = B^T A^T.$$
  * symmetric. for $$A \in R^{m \times n}$$ is symmetric if $$A = A^T.$$
  
* Gaussian elimination: perform elementary transformations to bring a system of linear equation into reduced row echelon form. 
  * augmented matrix $$[A \mid b].$$
  * elementary transformation: exchange, multiplication and addition of equation(s).
  * pivots (first non-zero element in each row) and staircase structure.
  * basic variables (at the column of pivots) and free variables.
  * row echelon form.
    * all rows with 0s only are at the bottom.
    * all rows with at least one non-zeroes are at the top.
    * a pivot is always strictly to the right of the pivor of the row above.
  * reduced row echelon form.
    * every pivot is 1.
    * the pivot is the only non-zero entry in its column.
  
* solving systems of linear equations.
  1. find the particular solution to Ax = b. $$\Rightarrow augmented\ matrix\ [A \mid b] \Rightarrow reduced\ row\ echelon\ form\ [A \mid b],$$ set all free variables as 0.
  2. find all solutions to Ax = 0. minus-1 trick, add $$[0, \cdots 0, -1, 0, \cdots, 0 ]$$ at the places where pivots on the diagonal are missing or 0.
  3. combine to general solutions.
  
* to culculate the inverse $$A^{-1}$$ of $$A \in R^{n \times n}$$, set $$AX = I_n$$ where $$X = A^{-1}$$. use Gaussian elimination, $$[A \mid I_n] \Rightarrow [I_n \mid A^{-1}].$$

* Moore-Penrose pseudo-inverse. $$Ax = b \Leftrightarrow A^T A x = A^T b \Leftrightarrow x = (A^T A) ^{-1} A^T b.$$ $$(A^T A) ^{-1} A^T $$ is the Moore-Penrose pseudo-inverse of A.

* group, set and operation.
  1. closure.
  2. associativity.
  3. neutral element.
  4. inverse element.

* Abelian group: commutative. (v, +) is an Abelian group.

* vector spaces. $$V = (v, +, ·)$$.
  * distributivity.
  * associativity.
  * neutral element.

* vector $$x \in V$$.

* vector subspaces. $$U = (u, +, ·)$$ is vector subspace of V if:
  1. $$u \subseteq v$$.
  2. $$u \subseteq \emptyset$$.
  3. closure of U.

* linear independence. vector $$v = \displaystyle\sum_{i = 1}^k \lambda_i x_i \in V$$. linear combination $$\lambda_1, \cdots, \lambda_k \in R$$.

  non-trival linear combination $$for\ 0=\displaystyle\sum_{i = 1}^k \lambda_i x_i, \exists \lambda_i \not= 0 \Leftrightarrow$$ linearly dependent.

  only the tribal solution exist $$\lambda_i = \cdots = \lambda_k = 0 \Leftrightarrow$$ linearly independent.

* determine linear independence. in row echelon form, all column vectors are linearly independent $$\Leftrightarrow$$ all columns are pivot columns.

* generating set. set of vectors $$A = {x_1, \cdots, x_k} \subseteq V$$. if $\forall v \in V$ can be expresseed as a linear combination of $$x_1, \cdots, x_k$$, A is a generating set of V.

* linear combination. the set of all linear combinations of vectors in A.

* basis. every linearly independent generating set of V is minimal and it is a basis of V.

* B is a basis of V $$\equiv$$ minimal generating set $$\equiv$$ maximal linearly independent set.

* basis vectors: all bases possess the same number of elements.

* dimension of V, dim(V) is number of basis vectors.

  if $$U \subseteq V$$ then $$dim(U) \leq dim(V)$$.

  $$dim(U) = dim(V) \Leftrightarrow U = V$$.

* determine a basis $$\equiv$$ linearly independent vectors.

* rank. the number of linearly independent columns for $$A \in R^{m \times n}$$, rank of A, rk(A).
  * $$rk(A) = rk(A^T)$$.
  * for all $$A \in R^{m \times n}$$, A is invertible $$\Leftrightarrow rk(A) = n$$.
  * $$Ax = b$$ can be solved $$\Leftrightarrow rk(A) = rk(A \mid b)$$.
  * full rank, $$rk(A) = min(m, n)$$. without full rank, rank deficient.

* linear mapping. vector spaces V, W, a mapping $$\phi: V \rightarrow W$$. linear mapping if $$\forall x, y \in V, \forall \lambda, \psi \in R, \phi(\lambda x + \psi y) = \lambda \phi(x) + \psi \phi(y)$$. 

*  isomorphism: $$\phi: V \rightarrow W$$. linear and bijective. $$\Leftrightarrow dim(V) = dim(W)$$.
  
*  if linear mappings: $$\phi: V \rightarrow W$$ and $$\psi: W \rightarrow X$$, then mapping $$\phi \circ \psi: V \rightarrow X$$ is also linear.
  
*  if linear mappings: $$\phi: V \rightarrow W$$ and $$\psi: V \rightarrow W$$, then mappings $$\phi + \psi$$ and $$\lambda \phi, \lambda \in R$$ are also linear.
  
* matrix representation of linear mappings.

  * vector spaces: V, W.
  * ordered based: $$B = {b_i}$$, $$C = c_j$$.
  * coordinates: $$\forall x \in V, x = \displaystyle\sum_{i = 1}^n a_i b_i$$. $$a_i$$ are the coordinates of x.
  * $$a = [a_1, \cdots, a_n] \in k^n$$ is the coordinate vector of x with respect to B.

* transformation matrix.
  * linear mapping: $$\phi: V \rightarrow W$$.
  * $$\phi(b_j) = \displaystyle\sum_{i = 1}^m a_{ij} c_i$$.
  * $$m \times n$$ matrix $$A_{\phi}$$ whose elements are $$A_{\phi}(i, j) = a_{ij}$$ is the transformation matrix.
  * $$\hat y = A_{\phi} \hat x$$.  $$\hat x$$ and $$\hat y$$ are the coordinates vectors.
  
* basis change.
  * linear mapping: $$\phi: V \rightarrow W$$, change the bases in V, W.
  * ordered based of V: $$B = {b_i}$$, $$\hat B = \hat b_i$$.
  * ordered based of W: $$C = {c_j}$$, $$\hat C = \hat c_j$$.
  * $$\hat A_{\phi} = T^{-1}A_{\phi}S$$. A and $$\hat A$$ are equivalent.
  * $$\hat A_{\phi} = S^{-1}A_{\phi}S$$. A and $$\hat A$$ are similar.
  ![basis change](/assets/images/2019-07-22-comp6670-introduction-to-machine-learning-basis-change.png)
  
* kernel space. $$ker(\phi) := \phi^{-1}(0_W) = \{v \in V : \phi(v) = 0_W\}$$.

* image. $$Im(\phi) := \phi(V) = {w \in W \mid \exists v \in V : \phi(v) = w}$$.
  ![basis change](/assets/images/2019-07-22-comp6670-introduction-to-machine-learning-image-and-kernel.png)
  
* $$\phi$$ injective $$\Leftrightarrow ker(\phi) = {0}$$.

* rank nullity theorem: for vector spaces V, W and a linear mapping $$\phi: V \rightarrow W$$ it holds that

  $$dim(ker(\phi)) + dim(Im(\phi)) = dim(V)$$. 


* affine spaces. vector spaces V. $$x_0 \in V, U \in V.$$

  $$L = x_0 + U := \{x_0 + u: u \in U\}$$.

  L affine subspace, $$x_0$$ support point, U direction.

* $$\{b_i\}$$ are bases of U. $$x \in L$$.

  $$X = x_0 + \lambda_1 b_1 + \cdots + \lambda_k b_k$$.

* 1-dimensional affine subspace, line. 2-dimensional, plane. n-dimensional, hyperplane.

* affine mapping. $$\phi: V \rightarrow W$$.
  $$x \mapsto a + \phi(x), a \in W$$,

// todo

