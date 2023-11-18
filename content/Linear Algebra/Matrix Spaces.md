### $3$ by $3$ matrices

We identified $M$, the space of all $3$ by $3$ matrices; S, the space of all symmetric $3$ by $3$ matrices; U, the space of all upper triangular $3$ by $3$ matrices and D, the space of all diagonal $3$ by $3$ matrices.

You can see the introduction of [[Matrix Type]]

The dimension of $M$ is $9$. A good choice of basis is:
$$
\begin{bmatrix}1 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 1 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 1 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix},
\dots,
\begin{bmatrix}0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 1 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 1\end{bmatrix}.
$$
The dimension of $S$ is 6 and one basis is:
$$
\begin{bmatrix}1 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 1 \\ 0 & 0 & 0 \\ 1 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 1\end{bmatrix}.
$$
The dimension of $U$ is also 6 and a basis for $U$ is:
$$
\begin{bmatrix}1 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 1 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 1 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 1\end{bmatrix}.
$$
The subspace $D = S  \cap U$ has dimension 3. A good basis is:
$$
\begin{bmatrix}1 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 0\end{bmatrix},
\begin{bmatrix}0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 1\end{bmatrix}.
$$
$S \cup U$ is NOT a [[Subspaces]] of $M$. However, $S + U$, which means all possible sums of elements of $S$ and elements of $U$, is a subspace of $M$. In fact, the subspace is just $M$ itself. We can find that dimensions follow this rule:
$$
\text{dim }S + \text{dim }U = \text{dim }(S + U) + \text{dim }(S \cap U).
$$

### Differential equations

We can think of the solutions $y$ to $\dfrac{\mathrm{d}^2y}{\mathrm{d}x^2} + y = 0$ as the elements of a Nullspace.

The complete solution is:
$$
y = c_1\cos x + c_2\sin x,
$$
where $c_1$ and $c_2$ can be any complex numbers. The solution space is a two dimensional vector space with [[Basis]] vectors $\cos x$ and $\sin x$.
