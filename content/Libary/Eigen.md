## API
1. Eigen::Matrix<double, 2, 3>: Matrix4f is a 2x3 matrix of doubles
$$
\begin{bmatrix}
a_1 & a_2 & a_3 \\
b_1 & b_2 & b_3
\end{bmatrix}
$$
2. Eigen::Isometry

   ```c++
   Eigen::Isometry3d T1=Eigen::Isometry3d::Identity();
   T1=Eigen::Isometry3d::Identity();
   T1.rotate(rotation_matrix1);
   T1.pretranslate(t1);
   ```

3. Eigen::Matrix4d

   ```c++
   Eigen::Matrix4d T2;
   T2.setIdentity();
   T2.block<3,3>(0,0) = rotation_matrix1;
   T2.block<3,1>(0,3) = t1;
   ```

   

## Using block operations
$$
Eigen::MatrixXf \;m(4,4) = 
\begin{bmatrix}
1 & 2 & 3 & 4\\
5 & 6 & 7 & 8\\
9 & 10 & 11 & 12\\
13 & 14 & 15 & 16
\end{bmatrix} \tag{1}
$$
1. m.leftCols(2)
$$
\begin{bmatrix}
1 & 2\\
5 & 6\\
9 & 10\\
13 & 14
\end{bmatrix}
$$
2. m.bottomRows<2>()
   $$
   \begin{bmatrix}
   9 & 10 & 11 & 12\\
   13 & 14 & 15 & 16
   \end{bmatrix}
   $$

3. 
![[Pasted image 20231130100928.png]]
## Column-major and row-major storage

1. Row-major

   Matrix is stored in **row-major** order if it is stored row by row. The entire first row is stored first, followed by the entire second row, and so on.

   

   If this matrix(1) is stored in row-major order, then the entries are laid out in memory as follows:

   `1 2 3 4 5 6 ... 15 16`

2. Column-major

   If it is stored in col-major order,  it is laid out as follows: `1 5 9 13 2 6 ... 12 16`
