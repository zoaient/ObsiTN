# Exercice 1

|               | M1  | M2   | M3  | M4  |
| ------------- | --- | ---- | --- | --- |
| P1            | 0h  | 1,5h | 2h  | 3h  |
| P2            | 3h  | 4h   | 3h  | 0h  |
| Disponibilité | 39h | 60h  | 57h | 57h |

## Objectif

> Maximiser le bénéfice total , $max(F(x)=1700x_1+3200x_2)$  
## Question 1
- Modéliser ce problème sous forme de PL, donner la forma canonique pure et al forme standard du programme linéaire

Soit :
- x1 quantité de produit P1
- x2 quantité de produit P2

$$x_1,x_2 \in  \mathbb R$$
### Contraintes

$$\begin{cases}
    0x_1 + 3x_2 \le 39 \\ 
    1,5 x_1 + 4x_2 \le60\\
    2 x_1 + 3x_2 \le57\\
	3 x_1  \le57\\
	x_1,x_2 \ge 60
\end{cases}
$$
###  Forme canonique pure
- (uniquement pour des inégalités dans les contraintes)

> max F(x) = c <sup>T</sup> x pour x=(x<sub>1</sub>,x<sub>2</sub>)

- Ax <= b
- x >= 0

$$x=\begin{pmatrix}
 \\
x_1 \\
x_2
\end{pmatrix},c=\begin{pmatrix}
 \\
1700 \\
3200
\end{pmatrix},a=\begin{pmatrix}
 \\
a_1 \\
...\\
a_n
\end{pmatrix},b=\begin{pmatrix}
 \\
b_1 \\
... \\
b_n
\end{pmatrix},a\le b$$

### Forme Standard Ax = b

$$A=\begin{pmatrix}
0 & 3 \\
1,5 & 4 \\
2 & 3 \\
3 & 0
\end{pmatrix}$$


$$
Ax=b \equiv Ax\ge b,Ax\le b \equiv Mx \le d
$$

$$M=\begin{pmatrix}
A \\
-A
\end{pmatrix}, d=\begin{pmatrix}
b \\
-b
\end{pmatrix}$$


### Variables d'écart

$$\begin{cases} 
 e_1 = 39 - 3x_2 \\
 e_2 = 60 - 1,5x_1 - 4_2  \\
 e_3 = 57 - 2x_1 - 3x_2 \\
 e_4 = 57 - 3x_1 \\
\end{cases}
$$



$$\mathrm{max}F(x_1, x_2)_(x_1,x_2) = \begin{cases}
    3x_2 \le 39 \\ 
    1,5 x_1 + 4x_2 \le60\\
    2 x_1 + 3x_2 \le57\\
	3 x_1  \le57\\
\end{cases}
$$

## Question 2

### Résolution graphique
![[Ex1 Q2.png]]
# Exercice 2 (vite fait)


![[AHHHHHHHHH.png]]

> ==J'ai pas suivi==


# Exercice 3

![[Ex3 1]]

## Variables binaires


$$x_{i,j} = \begin{cases} 
1 & \text{Si la tâche i est executée sur le processeur j} \\
0 & \text{Sinon}



\end{cases}
\quad \forall i\in [1,n] , \forall j \in [i,m] \quad n*m \quad \text variables
$$

## Temps total d'exécution sur le processeur j 

$$ T_j =  
\sum_{i=1}^{k} c_{i,j}x_{i,j}
$$

# Exercice 4 : Stockage
## Principe
- n fichiers de taille $c_1,...c_n$ 
- m disques durs de capacité $C$

## Variables
$$y_j=\begin{cases}1 \quad \text{si le disque j est utilisé}\\
0 \quad \text {sinon}\end{cases} 
\quad x_{i,j}=\begin{cases}1 \quad \text{si le fichier i est stocké sur le disque j}\\
0 \quad \text {sinon}\end{cases}$$
- Pour $i \in [1,n], j \in [i,m]$ , Nombre de variables : m+n\*m

## Objectif
> On cherche a minimiser le nombre de disques utilisés , ce qui correspond à $min \sum_{j=1}^{m}y_j$*
## Contraintes
- (1)$\sum_{i=1}^{n}x_{i,j}c_{i,j}\le C ,\forall j \in [1,m]$ (On ne dépasse pas la capacité du disque)
- (2)$\sum_{j=1}^{m}x_{i,j}=1, \forall i \in [1,m]$ (fichier i stocké une et une seule fois)
- (3)$x_{i,j}\le y_{j}, \forall i , \forall j$ (n\*m contraintes)
## Variante
- On remplace (1) par (1') $\sum_{i=1}^{n}c_{i,j}x{i,j}\le Cy_j, \forall j$
	- On a bien $y_j = 0 \implies x_{i,j} =0 , \forall i$
## Mise en forme du problème
$$min F(x)=c^Tx, \begin{cases}Ax \le b \\
Bx=d=\begin{pmatrix}
1 \\
... \\
1
\end{pmatrix} \in \mathbb{R}^n \\
x \in \{0,1\}^{m+n*m}
\end{cases}$$
## Variables (a nouveau)
$$x=(x_{1,1}...,x_{n,1},...x_{n,m},y_1,...,y_m)^T,p=(0,...,1,...,1)^T$$
- n * m zéros ,  m 1
- Pour $i=1, \sum_j x_{i,j} =x_{1,1}+...+x{1,m}=1$
- B matrice de taille n*(n\*m+m) composés de blocs de matrice identité a l'horizontale
- pour j=1 n, $c_1x_{1,1}+...c_nx{n,1}-Cy_1\le0$
- 1 matrice relou

![[no-bitches 1.jpg]] No matrice ?