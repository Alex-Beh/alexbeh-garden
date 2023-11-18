A skew-symmetric matrix A is a _square matrix_ whose _transpose equals its negative_, i,e. $A^T=−A$ 

$$
\mathbf{a}^\wedge = 
\begin{bmatrix}
0   & -a_3 & a_2\\
a_3 & 0  & -a_1 \\
-a2 & a_1  & 0 
\end{bmatrix}
$$

The main use case is it can simplify the [[Cross Product]] between two matrix into dot product.
$$
\begin{equation}
\vec{a} \times \vec{b} = {a}^{\wedge}\cdot\vec{b}
\end{equation}
$$

## Proof
Let's assume $\vec{a}=\begin{bmatrix}a_1&a_2&a_3\end{bmatrix}^T$ and $\vec{b}=\begin{bmatrix}b_1&b_2&b_3\end{bmatrix}^T$
$$
\begin{align*}
\vec{a}\times\vec{b}
&=
\begin{bmatrix}
a_2b_3-a_3b_{2}\\
a_3b_1-a_1b_3\\
a_1b_2-a_2b_1
\end{bmatrix} \\
&=
\begin{bmatrix}
0   & -a_3 & a_2\\
a_3 & 0  & -a_1 \\
-a2 & a_1  & 0 
\end{bmatrix}
\cdot
\begin{bmatrix}
b_1 \\
b_2 \\
b_3
\end{bmatrix}\\
&= {a}^{\wedge}\cdot\vec{b}
\end{align*}
$$