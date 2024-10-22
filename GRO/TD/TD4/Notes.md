# Feuille 3 ex 1
## Qu'est ce qu'on fait ? 
**Application de l'algorithme du simplexe**
## Etape 1
$$\begin{cases}e_1 = 100 -2 x_1 -4x_2-8x_3 -6x_4 \\
e_2 = 160 -10 x_1 -8x_2-6x_3 -10x_4\\
e_3 = 20 - x_1 -x_2-2x_3 -2x_4 \\
F = 50x_1 -40x_2-70x_3 -80x_4\end{cases}$$
### Variables de base
$$x_B =\begin{pmatrix}
e_1 \\
e_2 \\
e_3
\end{pmatrix} = \begin{pmatrix}
100 \\
160 \\
20
\end{pmatrix}$$
### Variables hors base
$$F= 0  \quad x_H=\begin{pmatrix}
x_1 \\
x_2 \\
x_3 \\
x_4
\end{pmatrix}=\begin{pmatrix}
0 \\
0 \\
0 \\
0
\end{pmatrix}$$
### Variable entrante
**On prend le maximum, dans le doute, on fait tout le temps comme ça c'est pas toi qui décide, c'est pas forcément la manière la plus optimisée, mais blc**
$$max(50,40,70,80) = 80 \implies x_e = x_4 $$
### Variable sortante
On maintient la positivité des variables de base
$$\begin{cases} 100 - 6x_4 \ge 0 \equiv x_4 \le \frac{100}{6}\eqsim 15
\\ 160 - 10x_4 \ge 0 \equiv x_4 \le \frac{160}{10}=16
\\ 20 - 2x_4 \ge 0 \equiv x_4 \le \frac{20}{2} =10
\end{cases}$$
> **Si les coefficients devant la variable entrante sont $\ge$ 0 alors l'ensemble des solutions réalisables n'est pas borné donc F n'est pas borné**
> On choisit $x_4=10 \implies e_3 =0$
Variable sortante $x_s=e_3=0$
### Nouvelle solution de base réalisable
#### Variables de base
$$x_B =\begin{pmatrix}
e_1 \\
e_2 \\
x_4
\end{pmatrix} = \begin{pmatrix}
100-6*10 \\
160 -10*10\\
10
\end{pmatrix}
=\begin{pmatrix}
40 \\
60\\
10
\end{pmatrix}$$
#### Variables hors base
$$F= 80*100  \quad x_H=\begin{pmatrix}
x_1 \\
x_2 \\
x_3 \\
e_3
\end{pmatrix}=\begin{pmatrix}
0 \\
0 \\
0 \\
0
\end{pmatrix}$$
## Etape 2
$$x_B=A_B^{-1}(b-A_Hx_H)$$
### Nouveau dictionnaire
**On remplace $x_4$ dans le nouveau dictionnaire par sa valeur**
$$\begin{cases}e_1=40+x_1-x_2-2x_3+2e_3\\
e_2=60-5x_1-3x_2+4x_3+5e_3\\
x_4 = \frac{1}{2}(20- x_1 -x_2-2x_3 -e_3) \\
F = 800 + 10x_1 -10x_3 -40e_3\end{cases}$$
### Variable entrante
$$x_e = x_1$$
### Variable sortante
**Il parait evident que $e_1$ ne peut être nul car $x_1$ est positif et le reste est (pour l'instant) nul , DONC**
$$x_S=e_2 \quad \text{avec}\quad x_1=\frac{60}{5}=12$$
### Nouvelle solution de base réalisable
$$x_B=\begin{pmatrix}
e_1 \\
x_1 \\
x_4
\end{pmatrix}=\begin{pmatrix}
52 \\
12 \\
4
\end{pmatrix}, \quad x_H =\begin{pmatrix}
e_2 \\
x_2 \\
x_3 \\
e_3
\end{pmatrix}=\begin{pmatrix}
0 \\
0 \\
0 \\
0
\end{pmatrix}$$
## Etape 3
### Nouveau dictionnaire
$$\begin{cases}x_1=12-\frac{3}{5}x_2+\frac{4}{5}x_3-\frac{1}{5}e_2+e_3\\ 
x_4 = 4-\frac{1}{5}x_2-\frac{7}{5}x_3+\frac{1}{10} e_2-e_3 \\
e_1=52-\frac{8}{5}x_2-\frac{6}{5}x_3-\frac{1}{5}e_2+4e_3\\
F = 920 - 6x_2 -2x_3 -2e_2 -30e_3\end{cases}$$
### Couts réduits
$$L_H=\begin{pmatrix}
-6 \\
-2 \\
-2 \\
-30
\end{pmatrix} < 0 \implies \text{on a atteint l'optimum}$$
# Exercice 2
$$(a) \quad L_H = \begin{pmatrix}
-\frac{1}{6} \\
-\frac{1}{6}
\end{pmatrix} <0 \implies \text{optimum atteint}$$
$$x_B^*=\begin{pmatrix}
x_1 \\
x_2 \\
e_3
\end{pmatrix} =\begin{pmatrix}
3 \\
3 \\
0 \rightarrow \text{base dégénérée}
\end{pmatrix}$$
$$x_H^*=\begin{pmatrix}
e_1 \\
e_2 
\end{pmatrix} =\begin{pmatrix}
0 \\
0
\end{pmatrix}$$
$$A_B=\begin{pmatrix}
3 & 2 & 0 \\
3 & 4 & 0 \\
0 & 1 & 1
\end{pmatrix} \quad , x_B^*=A^{-1}_Bb$$
## Autre solution de base
$$x_B^*=\begin{pmatrix}
x_1 \\
x_2 \\
e_2
\end{pmatrix}=\begin{pmatrix}
3 \\
3 \\
0
\end{pmatrix}$$
$$x_H^*=\begin{pmatrix}
e_1 \\
e_2 
\end{pmatrix} =\begin{pmatrix}
0 \\
0
\end{pmatrix}$$
$$A_B=\begin{pmatrix}
3 & 2 & 0 \\
3 & 4 & 1 \\
0 & 1 & 0
\end{pmatrix}$$
$$(b) L_h=\begin{pmatrix}
-1 \\
0
\end{pmatrix}\le 0$$
### Variable entrante
$$x_e=x_2
$$
### Variable sortante
$$x_S=e_2$$
# Exercice 3
## Question 1
$$max_{x,e} F(x)=c^Tx \quad \begin{cases}Ax+e=b\\
x\ge0\\
e\ge0\end{cases}$$
**Si $b\ge 0$  alors on choisit**
$$x_H=x=0  \quad x_B=e=b\ge 0$$
## Question 2
$$max F(x) \begin{cases}x_1+2x_2+2x_3+e_1=8\\
x_1+2x_2+3x_3-e_2=9\\
x_1,x_2,x_3,e_1,e_3\ge 0\end{cases}$$
> **On ne peut pas choisir $e_2=-9$ avec $x_1=x_2=x_3=0$**
### Problème auxiliaire
On cherche
$$min[a_2=F_{aux}]$$
$$P_{aux}=\begin{cases} x_1+2x_2+2x_3+e_1=8\\
x_1+2x_2+3x_3-e_2+a_2=9\\
x_1,x_2,x_3,e_1,e_2,a_2 \ge 0\end{cases}$$
Si la solution optimale de $P_{aux}$ est obtenue avec $a_2^*=0$ alors on a une solution 