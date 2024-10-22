l# Recherche opérationnelle

## Definition
- Ensemble de méthodes d'analyse scientifique (maths et info) des phénomènes d'organisation qui traite de l'optimisation de l'architecture et du fonctionnement des systèmes (industriels , économiques, numériques etc )
- C'est un outil d'aide a la décision.

## Schéma général

voir image diapo 5 cours

## Introduction générale

### Les ponts de chepa ou
- Transformer le schema en graphe
- Démontrer qu'on ne peut pas parcourir une fois toutes les arrests dans un cycle
- L'Allemagne ratio
- Google bravo

### La production 1 PB 
- En connaissant toutes les données, quel produit fabriquer dans le but de rapporter le max de bénéfice a une entreprise ?
- Modélisation par programmation linéaire 

#### Exemple (exercice diapo 13)
Contraintes et équation a maximiser : $$
\begin{align}
 f(x1,x2)=6x1 +4x2  \\ 
10>=x1>=0\\
 9>=x2>=0 \\
3x1 + 9x2 <= 81 \\
4x1+5x2 <= 55 \\
2x1+x2 <= 20\\
\end{align}$$

Notation matricielle compacte de ce problème :
$$C=
\begin{pmatrix}
6 \\
4
\end{pmatrix}
,A=\begin{pmatrix}
3 & 9 \\
4 & 5 \\
2 & 1
\end{pmatrix}
,x=\begin{pmatrix}
x1 \\
x2
\end{pmatrix}
,b=\begin{pmatrix}
81 \\
55 \\
20
\end{pmatrix}
$$

Remarque , pour x,y appartenant a $R^N$ on dit que $x=<y <=> xi =< yi$ pour tout i entre 1 et n

#### Exemple 2 (exercice diapo 17)

Modélisation de problème de transport/logistique par programmation linéaire en nombre entier / "Branch-and-Bound"
3 magasins $(M_1, M_2, M_3)$ et deux entrepôts $(E_1, E_2)$

Tableau des coûts 

|                 | $M_1$ | $M_2$ | $M_3$ | Disponibilité entrepôts |
| --------------- | ----- | ----- | ----- | ----------------------- |
| $E_1$           | 5     | 3     | 4     | 8                       |
| $E_2$           | 6     | 7     | 2     | 9                       |
| Demande magasin | 4     | 5     | 8     |                         |
$$
\begin{align}
min_x(F(x) &=& 5x_{11} + 3x_{12} + 4x_{13}+ 6x_{21} + x_{22} +x_{23} )
\\ x_{11} + x_{21} &= 4 &\text{(demande du magasin } M_1)
\\ x_{12} + x_{22} &= 5  &\text{(demande du magasin } M_2)
\\ x_{13} + 9x_{23} &= 8  &\text{(demande du magasin } M_3)
\\ x_{11}+ x_{12} + x_{13} &\leq 8  &\text{(disponibilité entrepôt } E_1)
\\ x_{21} + x_{22} + x_{23} &\leq 9  &\text{(disponibilité entrepôt } E_2)
\end{align}
$$


#### Exemple > 3  : Affectation des cours , le problème du voyageur de commerce, etc ... 
 - En gros : c'est compliqué, et on utilise plein de trucs : voir TP 1



