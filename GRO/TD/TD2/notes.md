# Exercice 1
## Rappels
> j'ai pas suivi le cours du coup c'est pas un rappel de fou
![[AHHHHHHHHH.png]]

$$C = \begin{cases}x\in \mathbb{R}^n , Ax=b, 0 \le x \end{cases}$$
- A matrice de taille m\*n  Avec $m \le n$ (matrice rectangulaire)
- On décompose $A=(A_b | A_h)$ à une permutation près des colonnes
	- $A_b$ matrice carrée m\*m inversible
	- $A_h$ matrice m * (n -m)
	- Pour $x\in \mathbb{R}^n,x=(x_B|x_H)^T$

$$\text{on a}\quad Ax=(A_B|A_H)(x_B|x_H)^T=A_Bx_B+A_Hx_H$$
- $Ax=b \equiv A_Bx_B + A_Hx_H=b$
- $Ax=b\equiv A_Bx_B=b-A_Hx_H \equiv x_B=A_{B}^{-1}(b-A_Hx_H)$
- On choisit $x_H$ la solution de base associée a $A_B$ , on obtient $x_B$ unique solution du système linéaire $A_Bx_B=b,(x_B=x_B=A_{B}^{-1}b)$   $$x_H=\begin{pmatrix}
0 \\
... \\
0
\end{pmatrix}$$
## Exercice (en soi)
### Question 1
- Montrer que $D_R=\{x\in \mathbb{R}^n | Ax =b, 0 \le x \}$ est convexe


