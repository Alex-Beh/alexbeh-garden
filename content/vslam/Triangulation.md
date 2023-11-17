# Triangulation

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
- Do the [[cross product]] on both side
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