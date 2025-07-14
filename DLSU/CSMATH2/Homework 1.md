
> [!tip]
> - $m$ and $n$ define the size of the resulting matrix after multiplication. $p$ is the "inner dimension" that must match for the multiplication to be valid, but it does _not_ define the size of the result.


---

Write your solutions on a clean sheet of paper and upload them here on Canvas. Work independently.

1. **Let $A$, $B\in M_{3,4}$ and $C \in M_{4,1}$. Give the dimensions of the following matrices.**
	(a.) $(5A^T + B^T)^T$
	If $A\in M_{3,4}$, then $A^T$ is $\in M_{4,3}$ and the same goes for matrix $B$. Since $5A^T$ is scalar multiple of $A^T$, it remains $\in M_{4,3}$. Therefore, $A^T_{4,3} + B^T_{4,3} \in M_{4,3}$ which if transposed by $(5A^T + B^T)^T$ then $M_{4,3} \rightarrow M^T_{3,4}$.

	**(b.) $C^T C$**
	Given a matrix of $C \in M_{4,1}$, $C^T=C_{1,4}\cdot C_{4,1}$. It equates to a scalar which is $\in C_{1,1}$ because the outer is $1\times 1$.

	**(c.) $CC^T$**
	$C\in M_{4,1}$ and $C^T \in M_{1,4}$, it's multiplicable because both number of columns and row of are the same. Therefore, it results to $\in M_{4,4}$ with a result of $4\times 4$ matrix.

	**(d.) $(-1BC)^T$** 
	Given a matrix of $B\in M_{3,4}$ and $C\in M_{4,1}$, it results in $3\times 1$ matrix multiplied by a scalar value of $-1$ and is tranposed to $(-1BC)^T = (M_{3,1})^T=M_{1,3}$.
	 
	**(e.) $((A-2B)C)^T$**
	Given a matrix of $A,B\in M_{3,4}$, $C\in M_{4,1}$, $A_{3,4}-2(B_{3,4})\in M_{3,4}$. Then, $((A-2B)_{3,4}\cdot C_{4,1})^T=1\times 3$ matrix or $M_{1,3}$.
	

2. **Let $A \ in \begin{bmatrix}1 & 0 & 2\\ * & -1 & * \\ * & 3 & 4\end{bmatrix}$ and $B=\begin{bmatrix}* & 0 & * \\ 6 & -1 & 4 \\ * & 1 & -2\end{bmatrix}$ , where asterisks represent entries of $A$ and $B$ which are not given. Answer the following questions.**
	(a.) What is the $(3,2)$ entry of $AB$?

	The row $3$ of $A=\begin{bmatrix}* & 3 & 4\end{bmatrix}$ and $B=\begin{bmatrix}0\\-1\\1 \end{bmatrix}$. Multiplying gives $(* \cdot 0) + (3 \cdot -1) + (4 \cdot 1)=\boxed{1}$
	
	(b.) What is the $(3,2)$ entry of $BA$?

	The row $3$ of $B=\begin{bmatrix}* & 1 &-2\end{bmatrix}$ and $A=\begin{bmatrix}0\\-1\\3\end{bmatrix}$. Multiplying gives  $(* \cdot 0) + (1 \cdot -1) + (-2 \cdot 3)=\boxed{-7}$

	(c.) Are $AB$ and $BA$ equal? Explain.

	They are both scalar but they don't have equal values. Commutative property doesn't work in Matrices.

	(d.) What is the $(3,3)$ entry of $2A-3B+I_3$, where $I_3$ is the $3\times 3$ identity matrix?


	(e.) Assume that $A=A^T$. Find $A$.

	
