# Exercice 5 feuille 3 : Analyse post-optimale
**principe du dictionnaire : on exprime tout en fonction des variables hors base**
## Question 1)
### Dernier dictionnaire
![[AHHHHHHHHH.png]]
J'ai pas le début du cours
$$\begin{cases} x_1=12-3/5x_2+4/5x_3 - 1/5e_2 +e_3 \\
x_4=4-1/5x_2 -7/5x_3 +1/10e_2 -e_3\\
e_1=52-8/5x_2 -6/5x_3 -1/5e_2 +4e_3\\
F=920-6x_2 -2x_3 -2e_2 -30e_3\end{cases}
$$
$$x_B^*=\begin{pmatrix}
x_1 \\
x_4 \\
e_1
\end{pmatrix}=\begin{pmatrix}
12 \\
4 \\
52
\end{pmatrix}$$
$$x_B^*=A_B^{-1}$$
$$A_H^*x_H^*=\begin{cases}-\frac{3}{5}x_2+\frac{4}{5}x_3-\frac{1}{5}e_2+e_3\\ 
-\frac{1}{5}x_2-\frac{7}{5}x_3+\frac{1}{10} e_2-e_3 \\
-\frac{8}{5}x_2-\frac{6}{5}x_3-\frac{1}{5}e_2+4e_3\\
\end{cases}$$
### Cout réduit
$$L_H=\begin{pmatrix}
-6 \\
-2 \\
-2 \\
-30
\end{pmatrix} <0 \implies \text{optimum unique atteint}$$

## Question 2 ) Analyse de sensibilité de l’objectif
> On remplace le coeff 50 dans F par un paramètre $c_1$ , on utilise les conditions d'optimalité
$$F(x)=c^Tx=c^T_Bx_B+c^T_Hx_H$$

$$Ax=b \equiv x_B =A^{-1}_Bb-A^{-1}_BA_Hx_H$$On pose : 
$$x_B^*=A_B^{-1}b,A_H^*=A_B^{-1}A_H$$
Donc: 
$$F(x)=c_B^Tx_B^*+(c_H^T-c^T_BA^*_H)x^*_H$$
On pose : 
$$L^T_H=c^T_H -c^T_BA^*_H$$
### Condition d'optimalité
$$L_H<0 \quad$$
$$c_H=\begin{pmatrix}
40 \\
70 \\
0 \\
0
\end{pmatrix},c_B=\begin{pmatrix}
c_1 \\
80 \\
0
\end{pmatrix}$$
$$x_B=A^{-1}_Bb-A_H^*x_H$$
$$L^T=\begin{pmatrix}
40 & 70 & 0 & 0
\end{pmatrix}-\begin{pmatrix}
c_1 & 80 & 0
\end{pmatrix}*A^*=
\begin{pmatrix}
24-0,6c_1 & -42+0,8c_1 & 8-0,2c_1 & -80 + c_1
\end{pmatrix}$$
Au final on trouve : $40 \le c_1 \le 52,5$
**(c1) étant le nombre de premiers produits**
### Conclusion
Si on choisit $c_1 \in [40,52,5]$ la solution optimale est inchangée
## Question 3
$$e_1=52\implies équipement\space excédent$$
**On change le second membre 100 en un paramètre d1**
Donc $$b=\begin{pmatrix}
d_1 \\
160 \\
20
\end{pmatrix}$$
Condition de faisabilité (positivité)
$$x^*_B=A^{-1}_Bb\ge0$$
Avec$$A_B=\begin{pmatrix}
2 & 6 & 1 \\
10 & 10 & 0 \\
1 & 2 & 0
\end{pmatrix}$$
- Quand les variables de base initiales sont les variables d'écart, on lit l'inverse $A_B^{-1}$ directement à partir de $A_H^*$ 
Donc :
$$A^{-1}_B=\begin{pmatrix}
0 & 1/5 & -1 \\
0 & -1/10 & 1 \\
1 & 1/5 & -4
\end{pmatrix}$$
Donc :
$$x^*_B=\begin{pmatrix}
12 \\
4 \\
d_1 - 48
\end{pmatrix} \ge 0 \equiv d_1\ge 48$$
