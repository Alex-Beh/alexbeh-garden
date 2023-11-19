We have $AB = C$. $A$ is an $m \times n$ matrix and $B$ is an $n \times p$ matrix, then $C$ is an $m \times p$ matrix. We use $c_{ij}$ to denote the entry in row $i$ and column $j$ of matrix $C$ and the same denotation applies to $a_{ij}$ and $b_{ij}$.

#### Row times column 

$c_{ij} = \sum_{k=1}^n a_{ik}b_{kj}$

#### Columns

The product of matrix $A$ and column $j$ of matrix $B$ equals column $j$ of matrix $C$. This tells us that the columns of $C$ are combinations of columns of $A$.

$$
A
\begin{bmatrix}
| & | & | \\
column 1 & column 2 & column 3 \\
| & | & |
\end{bmatrix}
=\begin{bmatrix}
| & | & | \\
A(column 1) & A(column 2) & A(column 3) \\
| & | & |
\end{bmatrix}
$$

#### Rows
The product of row $i$ of matrix $A$ and matrix $B$ equals row $i$ of matrix $C$. So the rows of $C$ are combinations of rows of $B$. 

$$
\left[
\begin{matrix}
--- & row 1 & --- \\
--- & row 2 & --- \\
--- & row 3 & ---
\end{matrix}
\right]
B
=\left[
\begin{matrix}
--- & (row 1)B & --- \\
--- & (row 2)B & --- \\
--- & (row 3)B & ---
\end{matrix}
\right]
$$

#### Column times row

$$
AB = \sum_{k=1}{n}
\begin{bmatrix}a_{1k} \\ \vdots \\ a_{mk}\end{bmatrix}
\begin{bmatrix}b_{k1} & \cdots & b_{kp}\end{bmatrix}
$$
#### Blocks

$$
\begin{bmatrix}A_1 & A_2 \\ A_3 & A_4 \end{bmatrix}
\begin{bmatrix}B_1 & B_2 \\ B_3 & B_4 \end{bmatrix}
=\begin{bmatrix}
A_1B_1+A_2B_3 & A_1B_2+A_2B_4 \\
A_3B_1+A_4B_3 & A_3B_2+A_4B_4
\end{bmatrix}
$$

### Inverses

If $A$ is *singular* or *not invertible*,

then A does not have an inverse,

and we can find some non-zero vector $\boldsymbol{x}$ for which $A\boldsymbol{x} = \boldsymbol{0}$

#### Gauss-Jordan Elimination

$$
E
\left[
\begin{array}{c|c}
A & I
\end{array}
\right]
=\left[
\begin{array}{c|c}
I & E
\end{array}
\right]
$$
If $EA = I$, then $E = A^{-1}$.