- [[#Identity Matrix|Identity Matrix]]
- [[#Upper Triangular Matrix|Upper Triangular Matrix]]
- [[#Lower Triangular Matrix|Lower Triangular Matrix]]
- [[#Symmetric Matrix|Symmetric Matrix]] ^b69769
- [[#Diagonal Matrix|Diagonal Matrix]]
- [[#[[Skew Symmetric Matrix]]|[[Skew Symmetric Matrix]]]]
- [[#Square Matrix|Square Matrix]]
## Permutation Matrix
A permutation matrix  has rows of the identity in any order.

Every row and every column of a permutation matrix contain exactly one nonzero entry,
which is 1. There are two 2 × 2 permutation matrices: 
$$
\begin{bmatrix}
1&0 \\ 
0&1
\end{bmatrix} \&
\begin{bmatrix}
0&1 \\ 
1&0
\end{bmatrix}
$$
Every permutation matrix is a product of elementary **row-interchange** matrices.
$$
\begin{bmatrix}
0&1 \\ 
1&0
\end{bmatrix}
\begin{bmatrix}
x_1\\ 
x_2
\end{bmatrix}=
\begin{bmatrix}
x_2\\ 
x_1
\end{bmatrix}
$$
## Identity Matrix

$$
\begin{bmatrix}
1 & 0 & \ldots & 0 \\
0 & 1 & \ldots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \ldots & 1
\end{bmatrix}
$$
## Upper Triangular Matrix
$$
\begin{bmatrix}
a_{11} & a_{12} & a_{13} & \ldots & a_{1n} \\
0 & a_{22} & a_{23} & \ldots & a_{2n} \\
0 & 0 & a_{33} & \ldots & a_{3n} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \ldots & a_{nn}
\end{bmatrix}
$$
## Lower Triangular Matrix
$$
\begin{bmatrix}
a_{11} & 0 & 0 & \ldots & 0 \\
a_{21} & a_{22} & 0 & \ldots & 0 \\
a_{31} & a_{32} & a_{33} & \ldots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
a_{n1} & a_{n2} & a_{n3} & \ldots & a_{nn}
\end{bmatrix}
$$
## Symmetric Matrix
$A=A^T$
$$
\begin{bmatrix}
a_{11} & a_{12} & a_{13} \\
a_{12} & a_{22} & a_{23} \\
a_{13} & a_{23} & a_{33}
\end{bmatrix}
$$
## Diagonal Matrix
$$
\begin{bmatrix}
d_1 & 0 & \ldots & 0 \\
0 & d_2 & \ldots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \ldots & d_n
\end{bmatrix}
$$
## [[Skew Symmetric Matrix]]
$$
\begin{bmatrix}
0 & -a_{12} & a_{13} \\
a_{12} & 0 & -a_{23} \\
-a_{13} & a_{23} & 0
\end{bmatrix}
$$
## Square Matrix
Number of row = Number of column
$$
\begin{bmatrix}
a_{11} & a_{12} & \ldots & a_{1n} \\
a_{21} & a_{22} & \ldots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{n1} & a_{n2} & \ldots & a_{nn}
\end{bmatrix}
$$