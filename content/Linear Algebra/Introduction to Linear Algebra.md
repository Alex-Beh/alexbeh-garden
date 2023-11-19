## Vectors
### Closure
A collection of vectors has to satisfy two conditions:
1. closed under addition, which means the sum of any two vectors in the collection lies again in the collection,
2. closed under multiplication by any real numbers, that is to say that multiplying any vector in the collection by any real number will not give a vector beyond the collection,
or, to put it in another way, closed under linear combinations.
s.t. we call the collection a *vector space*.

## Matrix
### Pivot Point
- Associative
	矩阵乘法虽然不能随意变动相乘次序，但是可以变动括号位置
- Commutative
## Condition to solve $Ax=b$ or $Ax=0$
- $A$ is invertible

   - $A\boldsymbol{x} = \boldsymbol{b}$ has the unique solution $\boldsymbol{x}$ for each $\boldsymbol{b}$
   - $A\boldsymbol{x} = \boldsymbol{0}$ has no non-zero solution $\boldsymbol{x}$
   - The columns of $A$ are *independent*
   - All vectors $A\boldsymbol{x}$ cover the whole vector space \
    Example: $A = \begin{bmatrix}1 & 0 & 0 \\ -1 & 1 & 0 \\ 0 & -1 & 1\end{bmatrix}$
- $A$ is not invertible
    - $A\boldsymbol{x} = \boldsymbol{b}$ has a solution $\boldsymbol{x}$ only for some of $\boldsymbol{b}$ in the vector space
    - $A\boldsymbol{x} = \boldsymbol{0}$ has non-zero solutions $\boldsymbol{x}$
    - The columns of $A$ are *dependent*
    - All vectors $A\boldsymbol{x}$ lies in only a subspace of the vector space \
    Example: $A = \begin{bmatrix}1 & 0 & -1 \\ -1 & 1 & 0 \\ 0 & -1 & 1\end{bmatrix}$
