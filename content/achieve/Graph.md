Graph consist of Nodes & Edges where m(row) is \#edges & n(col) is \#nodes

For the following example, the graph is consist of 4 nodes and 5 edges.
![[graph.png]]

### Incidence Matrices
$$
\begin{array}{c | c c c c}
       & node_1 & node_2 & node_3 & node_4 \\
\hline
edge_1 & -1     & 1      & 0      & 0      \\
edge_2 & 0      & -1     & 1      & 0      \\
edge_3 & -1     & 0      & 1      & 0      \\
edge_4 & -1     & 0      & 0      & 1      \\
edge_5 & 0      & 0      & -1     & 1      \\
\end{array}
$$

Write into Matrix form
$$
A=
\begin{bmatrix}
-1 & 1 & 0 & 0 \\
0 & -1 & 1 & 0 \\
-1 & 0 & 1 & 0 \\
-1 & 0 & 0 & 1 \\
0 & 0 & -1 & 1 \\
\end{bmatrix}
$$
Observation from the first three rows, we notice there is linear dependent relationship, which mean the three row spaces form an _loop_.
