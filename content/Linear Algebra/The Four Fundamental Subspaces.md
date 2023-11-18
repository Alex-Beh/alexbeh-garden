- [[#Four subspaces and their basis and dimension|Four subspaces and their basis and dimension]]
- [[#Column space $C(A)$|Column space $C(A)$]]
- [[#Nullspace $N(A)$|Nullspace $N(A)$]]
- [[#Row space $C(A^\mathrm{T})$|Row space $C(A^\mathrm{T})$]]
- [[#Left Nullspace $N(A^\mathrm{T})$|Left Nullspace $N(A^\mathrm{T})$]]
			- [[#how to find a basis for $N(A^\mathrm{T})$|how to find a basis for $N(A^\mathrm{T})$]]
- [[#New vector space|New vector space]]

## Four subspaces and their basis and dimension

Any $m$ by $n$ matrix $A$ determines four [[Subspaces]] (possibly containing only the zero vector):
## Column space $C(A)$

All combinations of the columns of $A$

A subspace of $\mathbb{R}^m$

The $r$ pivot columns form a basis

$\text{dim }C(A) = r$

## Nullspace $N(A)$

All solutions $\boldsymbol{x}$ of the equation $A\boldsymbol{x} = \boldsymbol{0}$

A subspace of $\mathbb{R}^n$

The $n - r$ special solutions from a basis

$\text{dim }N(A) = n - r$

## Row space $C(A^\mathrm{T})$

All combinations of the rows of  $A$

A subspace of $\mathbb{R}^n$

The  first $r$ rows of  $R$ (the reduced row echelon form of $A$) form a basis

$\text{dim }C(A^\mathrm{T}) = r$

## Left Nullspace $N(A^\mathrm{T})$

All solutions $\boldsymbol{y}$ of the equation $\boldsymbol{y}^\mathrm{T}A = \boldsymbol{0}$

A subspace of $\mathbb{R}^m$

The bottom $m - r$ of $E$ form a basis

$\text{dim }N(A^\mathrm{T}) = m - r$

##### how to find a basis for $N(A^\mathrm{T})$

First we get $E$ through Gauss-Jordan elimination:
$$
E_{m \times n} \left[
\begin{array}{c|c}A_{m \times n} & I_{m \times n}\end{array}
\right]
=\left[
\begin{array}{c|c}R_{m \times n} & E_{m \times n}\end{array}
\right]
$$
Then the bottom $m - r$ rows of $E$ describe linear dependencies of rows of $A$ since the bottom $m - r$ rows of $R$ are zero. For example:
$$
EA = \begin{bmatrix}
-1 & 2 & 0 \\
1 & -1 & 0 \\
1 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
1 & 2 & 3 & 1 \\
1 & 1 & 2 & 1 \\
1 & 2 &3 & 1
\end{bmatrix}
= \begin{bmatrix}
1 & 0 & 1 & 1 \\
0 & 1 & 1 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix} = R
$$
In this example, The last row of $E$ satisfy the equation $\boldsymbol{y}^\mathrm{T}A = \boldsymbol{0}$ and thus form a basis for the left Nullspace of $A$.

## New vector space

We put all $3$ by $3$ matrices together and see the  collection as a new vector space; we call it M.

Some subspace of $M$ include:

- all upper triangular matrices
- all symmetric matrices
- $D$, all diagonal matrices

$D$ is the intersection of the first two space. It also has a dimension of $3$ and a basis for $D$ is:
$$
\begin{bmatrix}
1 & 0 & 0 \\
0 & 0 & 0 \\
0 & 0 & 0
\end{bmatrix},
\begin{bmatrix}
1 & 0 & 0 \\
0 & 3 & 0 \\
0 & 0 & 0
\end{bmatrix},
\begin{bmatrix}
0 & 0 & 0 \\
0 & 0 & 0 \\
0 & 0 & 7
\end{bmatrix}.
$$