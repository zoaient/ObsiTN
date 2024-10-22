# Programmation linéaire
****
## C'est quoi la programmation linéaire ?
- Dans un problème de programmation linéaire les contraintes et l'objectif sont des fonctions linéaires des variables (PL) , en gros, on obtient un système linéaire
- Les problèmes qu'on a à résoudre sont modélisables sous la forme de PL

### Exemple de modélisation de PL (Feuille 1 ex 1 question 1)
#### Problème

|               | M1  | M2   | M3  | M4  |
| ------------- | --- | ---- | --- | --- |
| P1            | 0h  | 1,5h | 2h  | 3h  |
| P2            | 3h  | 4h   | 3h  | 0h  |
| Disponibilité | 39h | 60h  | 57h | 57h |
|               |     |      |     |     |
#### PL
$$\mathrm{max}F(x_1, x_2)_(x_1,x_2) = \begin{cases}
    3x_2 \le 39 \\ 
    1,5 x_1 + 4x_2 \le60\\
    2 x_1 + 3x_2 \le57\\
	3 x_1  \le57\\
\end{cases}
$$

### Formes de modélisation
#### Canonique mixte
- Osef ?
- ![[Pasted image 20241018161326.png]]
#### Canonique pure
$$max_x[F(x)=c^Tx], \begin{cases}Ax\le b \\
x \ge 0\end{cases}$$
#### Forme Standard
$$max_x[F(x)=c^Tx], \begin{cases}Ax= b \\
x \ge 0\end{cases}$$

> Dans ces deux cas , on impose $x\ge 0$
##### Mise sous forme standard , exemple (Feuille 1 ex1 question 1)
$$A=\begin{pmatrix}
0 & 3 \\
1,5 & 4 \\
2 & 3 \\
3 & 0
\end{pmatrix}, b=\begin{pmatrix}
39 \\
60 \\
57 \\
57
\end{pmatrix}$$

**Tout PL sous forme standard s'écrit de façon équivalente en un PL sous forme canonique pure et inversement**
##### Forme Standard Simpliciale
### Variables d'écart : Concept
**Permet de passer de la forme Ax<=b a la forme Ax=b**
$$Ax\le b \equiv Ax+e=b, e=(e_1,...,e_m)^T$$
![[Pasted image 20241018163422.png]]
### Comment résoudre mon problème ? 
#### Résolution graphique (Feuille 1 ex 1 question 2)
- N'est faisable que pour des PL à deux variables, t'a capté cheffe
#### Solution réalisable
- Tout x qui vérifie $Ax=b , x\ge0$
#### Solution de base
$$x=(x_B\space x_H)^T,x_H=0\implies x_B=A^{-1}_Bb$$
**Cette solution de base est une solution de base réalisable si en plus xB >= 0**
### Variables de base
- Tu vois une matrice pas carrée, ouais, rectangulaire, bah, tu prends une partie qui est carrée, toutes les variables qui sont à l'intérieur sont des variables de base, le reste c'est des variables hors base
$$A=(A_B|A_H), x=(x_B \space x_H)^T$$
$A_B$ Est inversible
Alors : 
$$Ax=b \equiv A_Bx_B+A_Hx_H=b$$
## Méthode du simplexe
### Principe
- Faire rentrer une variable hors-base dans la nouvelle base (variable entrante) et faire sortir à la place une variable de base (variable sortante)

 