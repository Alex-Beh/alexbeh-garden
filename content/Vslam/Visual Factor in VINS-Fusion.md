## projectionOneFrameTwoCamFactor
Parameters to be optimised:

1. $[P_{b_i}^w, q_{b_i}^w]$ : SE(3) pose of body in frame i
2. $[P_{b_j}^w, q_{b_j}^w]$ : SE(3) pose of body in frame j
3. $[p_{c}^b, q_{c}^b]$: Extrinsic parameter between body and camera
4. $\lambda_l$: inverse depth, it is the depth of feature in frame i
5. $t_d$: time difference between camera & imu

![[feature_factor.png]]
$$
\begin{align*}
residuals &= measurement - result\_from\_projection\\
r_c
&=
\begin{bmatrix}
u_j-\frac{X_j}{Z_j}\\
v_j-\frac{Y_j}{Z_j}
\end{bmatrix}
\end{align*}
$$
```c++
residual = (pts_camera_j / dep_j).head<2>() - pts_j_td.head<2>();
residual = sqrt_info * residual;
```
There are 4 Jacobian in Evaluate function.

- For feature point that is first observed in camera at frame i and project it into camera at frame j
  $$
  \begin{bmatrix}
  X_{c_j}\\
  Y_{c_j}\\
  Z_{c_j}\\
  1\\
  \end{bmatrix} =
  T_b^c*T_w^{b_j}*T_{b_i}^w*T_c^b*
  \begin{bmatrix}
  X_{c_i}\\
  Y_{c_i}\\
  Z_{c_i}\\
  1
  \end{bmatrix} \tag{1}
  $$
  Since $\frac{1}{\lambda} = Z_{c_i}$ and using the projection function, let's further modify Equation(1)
  $$
  \begin{bmatrix}
  X_{c_j}\\
  Y_{c_j}\\
  Z_{c_j}\\
  1\\
  \end{bmatrix} =
  T_b^c*T_w^{b_j}*T_{b_i}^w*T_c^b*
  \begin{bmatrix}
  \frac{1}{\lambda}u_{c_i}\\
  \frac{1}{\lambda}v_{c_i}\\
  \frac{1}{\lambda}\\
  1
  \end{bmatrix} \tag{2}
  $$
  Expand the Equation(2) by $T_b^aP^b=R_b^aP^b+t_b^a$,
  $$
  f_{c_j} = 
  \begin{bmatrix}
  X_{c_j}\\
  Y_{c_j}\\
  Z_{c_j}
  \end{bmatrix}
  \begin{align*}
  &=R_b^cR_w^{b_j}R_{b_i}^wR_c^b\frac{1}{\lambda}
  \begin{bmatrix}
  u_{c_i}\\
  v_{c_i}\\
  1
  \end{bmatrix} \\
  &+R_b^c(R_{b_j}^w(R_{b_i}^wp_c^b+p_{b_i}^w-p_{b_j}^w)-p_c^b)
  \end{align*} \tag{3}
  $$
  What is our target? To find out the derivative of residual, which is the **Jacobian** of [[Lie Group]]

  ![img](https://img-blog.csdnimg.cn/2a5ae2f5579442bc8c862e4fe694edd2.png)

  By using Chain Rule:  $$
  \frac{\delta r_c}{\delta P} = \frac{\delta r_c}{\delta f_{c_j}}*\frac{\delta f_{c_j}}{\delta P} \tag{4}
  $$
  P consists of all the parameters that we want to optimise: 
  [note: $t_d$ is missing in the picture]
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/2b8635392eef49f69c42288795008f49.png)

​		For the first term in Equation(4), in code it is declare as **reduce**
$$
\frac{\delta r_c}{\delta f_{c_j}} =
\begin{bmatrix}
\frac{1}{Z_{c_j}} & 0 & -\frac{X_{c_j}}{Z_{c_j}^2} \\
0 & \frac{1}{Z_{c_j}} & -\frac{Y_{c_j}}{Z_{c_j}^2}
\end{bmatrix} \tag{5}
$$
​		For the second term in Equation(4), let's take the derivative for each parameters

1. Jacobian[0]   $$
   \frac{\delta f_{c_j}}
   {\delta
   \begin{bmatrix}
   \delta p_{b_i}^w \\
   \delta \theta_{b_i^w}
   \end{bmatrix}
   } 
   =
    \begin{bmatrix}
   \frac{\delta f_{c_j}}{\delta p_{b_i}^w} ,
   \frac{\delta f_{c_j}}{\delta \theta_{b_i}^w} ,
   \end{bmatrix}
   $$
   Let's take derivative example for the first term,
   $$
   \frac{\delta f_{c_j}}{\delta p_{b_i}^w} = R_b^cR_w^{b_j}
   $$

2. Jacobian[1]
   ```c++
   Eigen::Matrix<double, 3, 6> jaco_j;
   jaco_j.leftCols<3>() = ric.transpose() * -Rj.transpose();
   jaco_j.rightCols<3>() = ric.transpose() * Utility::skewSymmetric(pts_imu_j);
   ```
   $$
   jaco\_j_{3x6} = 
   \begin{bmatrix}
   | & - & | & | & - & | \\
   | & \frac{\delta f_{c_j}}{\delta p_{b_i}^w} & | & | & \frac{\delta f_{c_j}}{\delta q_{b_i}^w} & | \\
   | & - & | & | & - & | 
   \end{bmatrix}
   $$

3. Jacobian[2]: extrinsic parameter between body and camera
4. Jacobian[3]: about feature
   $$
   \begin{aligned}
   \frac{\partial \mathbf{r}_{\mathcal{C}}}{\partial \lambda_l} & =\frac{\partial \mathbf{r}_{\mathcal{C}}}{\partial p_l^{c_j}} \frac{\partial p_l^{c_j}}{\partial \lambda_l} \\
   \text{where }
   \frac{\partial p_l^{c_j}}{\partial \lambda_l}
   &= R_b^cR_w^{b_j}R_{b_i}^wR_c^b
   \pi_c^{-1}\left(\left[\begin{array}{c}
   u_l^{c_i} \\
   v_l^{c_i}
   \end{array}\right]\right) \frac{1}{\lambda_l^2}
   \end{aligned}
   $$

5. Jacobian[4]: about time $t_d$

## Reference

1. [VINS-MONO理论学习---紧耦合后端非线性优化](https://blog.csdn.net/xiaojinger_123/article/details/119669141)
2. [VINS 系统中的视觉重投影因子](https://sxij.xyz/posts/visual-projection-factor-in-vins/)
3. [VINS_FUSION入门系列－优化optimization](https://blog.csdn.net/pj_find/article/details/106497124)

   