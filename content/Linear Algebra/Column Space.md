Given a matrix $A$, all the linear combinations of the columns of $A$ form a [[Subspaces]]. This is the *column space* $C(A)$.

For example, if $A = \begin{bmatrix}0 & 1 \\ -1 & 0 \\ 1 & 0\end{bmatrix}$, the column space of $A$ is the plane through the origin in $\mathbb{R}^3$ containing $\begin{bmatrix}0 \\ -1 \\ 1\end{bmatrix}$ and $\begin{bmatrix}1 \\ 0 \\ 0\end{bmatrix}$.
![[column_space.png]]

### Column space of $A$ and solving $A\boldsymbol{x} = \boldsymbol{b}$
Given a matrix $A$, the system of linear equations $A\boldsymbol{x} = \boldsymbol{b}$ is solvable exactly when $\boldsymbol{b}$ is a vector in the *column space* of $A$.
### Nullspace of $A$
The Nullspace* of a matrix $A$ is the collection $x$ to the equation $A\boldsymbol{x} = \boldsymbol{0}$

For example,
$$
\begin{bmatrix}1 & 1 & 2 \\ 2 & 1 & 3 \\ 3 & 1 & 4 \\ 4 & 1 & 5\end{bmatrix}\begin{bmatrix}x_1 \\ x_2 \\ x_3\end{bmatrix} = \begin{bmatrix}0 \\ 0 \\ 0 \\ 0\end{bmatrix},
$$
the Nullspace $N(A)$ consists of all multiples of $\begin{bmatrix}1 \\ 1 \\ -1\end{bmatrix}$. This Nullspace is a line in $\mathbb{R}^3$.

Attention, a nullspace is a vector space because it obviously satisfies the requirements about addition and scale multiplication. That is to say that any sum or multiple of solutions of $A\boldsymbol{x} = \boldsymbol{0}$ is also a solution: $A(\boldsymbol{x}_1 + \boldsymbol{x}_2) = \boldsymbol{0} + \boldsymbol{0} = \boldsymbol{0}$ and $A(c\boldsymbol{x}) = cA\boldsymbol{x} = c\boldsymbol{0} = \boldsymbol{0}$.

### Other values of $\boldsymbol{b}$
The solutions to the equation:
$$
\begin{bmatrix}1 & 1 & 2 \\ 2 & 1 & 3 \\ 3 & 1 & 4 \\ 4 & 1 & 5\end{bmatrix}\begin{bmatrix}x_1 \\ x_2 \\ x_3\end{bmatrix} = \begin{bmatrix}1 \\ 2 \\ 3 \\ 4\end{bmatrix},
$$

**do not form a subspace**. This conclusion is obvious since **the zero vector is not a solution** to the equation. Actually, the set of solutions forms a line in $\mathbb{R}^3$ that pass through the points $\begin{bmatrix}1 \\ 0 \\ 0\end{bmatrix}$ and $\begin{bmatrix}0 \\ -1 \\ 1\end{bmatrix}$, but not $\begin{bmatrix}0 \\ 0 \\ 0\end{bmatrix}$.
