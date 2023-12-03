- Transform a point in frame A to world frame with the transformation $T_{A}^W$
$$
P^W=T_{A}^W*P^A
$$
- Transform a point in world frame to frame B with the transformation $T_{B}^W$ 
$$
\begin{align*}
P^B &= T_W^B*P^W \\
&= (T_B^W)^{-1}*P^A \\
&= (R_B^W)^{T}(P^W-t^B)
\end{align*}
$$
- To transform a point by the composition of the transform from  A→W and then  W→B:
$$
\begin{align*}
P^B &= T_W^B*T_{A}^W*P^A \\
&= (T_B^W)^{-1}*T_{A}^W*P^A \\
&= (R_B^W)^{T}R_A^Wp^A+(R_B^W)^{T}(t_A^W-t_B^W)
\end{align*}
$$

### Proof step by step



https://motion.cs.illinois.edu/RoboticSystems/CoordinateTransformations.html

## Remember this Lesson!!!!
![[rotation-hard-lesson.png]]