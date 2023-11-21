To find out the feature point in world coordinate when it is observed at least in two camera frames

Given:

- 2D image observations **[*u*,*v*]** in multiple frames.
- Camera intrinsic matrix ***K***.
- Camera poses **[$R_{c_i}^w$,$t_{c_i}^w$]** for each observation frame.

![[multiview_triangulation.png]]
## Theory

$$
\begin{align*} 
\begin{bmatrix}
x\\
y\\
z
\end{bmatrix} &= \frac{1}{s}*[R_{c_i}^w,t_{c_i}^w]*P^w \tag{1}&
\begin{bmatrix}
x\\
y\\
z
\end{bmatrix} &= K^{-1}*
\begin{bmatrix}
u\\
v\\
1
\end{bmatrix} 
\end{align*} 
$$
### Homogeneous Method
- From Equation (1)
$$
\begin{align*} 
\begin{bmatrix}
x\\
y\\
z
\end{bmatrix} &= \frac{1}{s} *
\begin{bmatrix}
{T_{c_i}^w}^1*P\\
{T_{c_i}^w}^2*P\\
{T_{c_i}^w}^3*P
\end{bmatrix}
\end{align*} \\
$$
- Do the [[Cross Product]] on both side
$$
0 =\begin{bmatrix}
x\\
y\\
z
\end{bmatrix} \times 
\begin{bmatrix}
x\\
y\\
z
\end{bmatrix} = 
\begin{bmatrix}
x\\
y\\
z
\end{bmatrix} \times
\begin{bmatrix}
{T_{c_i}^w}^1*P\\
{T_{c_i}^w}^2*P\\
{T_{c_i}^w}^3*P
\end{bmatrix}
$$
- Transform into [[Skew Symmetric Matrix]]
$$
\begin{bmatrix}
\begin{align*}
-{T_{c_i}^w}^2P&+y{T_{c_i}^w}^3P\\
{T_{c_i}^w}^1P&-x{T_{c_i}^w}^3P\\
-y{T_{c_i}^w}^1P&+x{T_{c_i}^w}^3P\\
\end{align*}
\end{bmatrix} = 
\begin{bmatrix}
0\\
0\\
0
\end{bmatrix} \tag{2}
$$
> Since row3 is linearly dependant on row1 & row2, so we need another set of Equation(2) in order to recover the 3D Position of the feature point.

- We can solve the Equation(2) by using [[Singular Value decomposition]]. Since P is [[Homogeneous Coordinates]], so we need to homogeneous V by $P=V[0:3]/V[4]$.
- When there is noise in the measurement, $V[4]$ could be a value that is close to zero. Then the recovered position from P might be a infinity point. This is a problem of doing triangulation by homogeneous method.  
### Non-Homogeneous Method


### Code Implementation
#### Homogeneous Method
```

```

### Reference
1. [多帧三角化原理](https://blog.csdn.net/xhtchina/article/details/127541440)
2. [三角化特征点(triangulation)方法及实现对比](https://blog.csdn.net/weixin_41469272/article/details/123696963)
3. [SLAM中多目三角化](https://rupingcen.blog.csdn.net/article/details/115602175?ydreferer=aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hodGNoaW5hL2FydGljbGUvZGV0YWlscy8xMjc1NDE0NDA%3D?ydreferer=aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hodGNoaW5hL2FydGljbGUvZGV0YWlscy8xMjc1NDE0NDA%3D?ydreferer=aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hodGNoaW5hL2FydGljbGUvZGV0YWlscy8xMjc1NDE0NDA%3D?ydreferer=aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hodGNoaW5hL2FydGljbGUvZGV0YWlscy8xMjc1NDE0NDA%3D)
4. 

