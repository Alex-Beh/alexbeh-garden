We have an example $A\boldsymbol{x} = \boldsymbol{b}$,

$A = \begin{bmatrix}1 & 2 & 1 \\ 3 & 8 & 1 \\ 0 & 4 & 1\end{bmatrix}$ and $\boldsymbol{b} = \begin{bmatrix}2 \\ 12 \\2\end{bmatrix}$.

Steps of Elimination:

- Step 1: subtract $3$ times row 1 from row 2;
- Step 2: subtract $2$ times row 2 from row 3.

$$
A = \begin{bmatrix}1 & 2 & 1 \\ 3 & 8 & 1 \\ 0 & 4 & 1\end{bmatrix}
\rightarrow \begin{bmatrix}1 & 2 & 1 \\ 0 & 2 & -2 \\ 0 & 4 & 1\end{bmatrix}
\rightarrow U = \begin{bmatrix}1 & 2 & 1 \\ 0 & 1 & -2 \\ 0 & 0 & 5\end{bmatrix}
$$

$$
\boldsymbol{b} = \begin{bmatrix}2 \\ 12 \\ 2\end{bmatrix}
\rightarrow \cdots \rightarrow \begin{bmatrix}2 \\ 6 \\ -10\end{bmatrix}
$$

> From row3, $5z=-10$, so $z=-2$

Thus, we can easily solve the systems of equations, $\begin{bmatrix}x \\ y  \\ z\end{bmatrix} = \begin{bmatrix}2 \\ 1  \\ -2\end{bmatrix}$.

### Elimination Matrices

The product of a matrix (3x3) and a column vector (3x1) is a column vector (3x1) that is a linear combination of the columns of the matrix.

The product of a row vector (1x3) and a matrix (3x3) is a row vector (1x3) that is a linear combination of the rows of the matrix.

For example,

$$
\begin{bmatrix}1 & 0 & 0 \\ -3 & 1 & 0 \\ 0 & 0 & 1\end{bmatrix}
\begin{bmatrix}1 & 2 & 1 \\ 3 & 8 & 1 \\ 0 & 4 & 1\end{bmatrix}
= \begin{bmatrix}1 & 2 & 1 \\ 0 & 2 & -2 \\ 0 & 4 & 1\end{bmatrix}.
$$

Multiplying on the left by a permutation matrix exchanges the rows of a matrix, while multiplying on the right exchanges the columns. For example,

$$
P = \begin{bmatrix}0 & 1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 1\end{bmatrix}.
$$

$P$ is a *permutation matrix* and the first and second rows of the matrix $PA$ are the second and first rows of the matrix $A$.

Note, matrix multiplication is *associative* but *not commutative*.