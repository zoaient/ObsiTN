# Algorithmes génétiques
## Principes
1) Codage (Chromosome)
2) Fitness
3) Génération
	1) Selection
	2) Croisement
	3) Mutation
## Exercice 1
### 1) Génotype
G n-uplet : $\forall i , G[i]=\begin{cases}1\text{ si on implante un magasin}\\0\text{ sinon}\end{cases}$     $G\in\{0,1\}^n$
### 2) Fonction d'évaluation
- $f(G)=\frac{\sum \text{Bénéfices des arrets couverts - cout}}{\text{magasin * nb magasins}}$
#### Formule
B un n-uplet $B[i]=$ Bénéfice du i eme arret
C une matrice $n*m$ tq $C[i,j]=\begin{cases}1\text{si i et j sont adjacents}\\0 \text{ sinon}\end{cases}$
K une matrice $n*n$ tq $K[i,j]=G[i]*C[i,j]$ OU $K(i,j)=\begin{cases}1\text{ si arret j est couvert}\\0 \text{ sinon}\end{cases}$
$f(G)=\sum_j OU(K(i,j))*B[j]-6*G [j]$
$$G=\begin{pmatrix}
1 & 1 & 0 & 1
\end{pmatrix}, B=\begin{pmatrix}
6 & 5 & 10 & 2
\end{pmatrix}$$

$$C=\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 1 & 0 \\
0 & 1 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix},K=\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 1 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}$$
### 3) Selection
Selection proportionnelle (voir cours)
#### 3b) Recombinaison (croisement)
Pc)0,7
G1= 0 1 1 0 1 1 1 
G2= 1 0 0 1 1 0 1
G1'=1 0 0 0 1 1 1
G2'=0 1 1 1 1 0 1
#### 3c) Mutation
Pm=0,001
G1'=1 0 0 0 1 1 1
G2'=1 0 1 0 1 1 1 
### Condition d'arrêt
1) Approche de la solution (Si connue)
2) Patience sur n générations (n générations sans amélioration de l'évaluation moyenne de la population)
## Exercice 2
### Q1
G=$2*n*n$-uplet à valeur dans $\{0,1\}^n$ 
	- 00 -> bas
	- 11 -> haut
	- 10 -> gauche
	- 11 -> droite
### Q2
- $F_1(G)=d_{max}-\text{distance de Manhattan}$
	- Souci : ne prend pas en compte les murs
- $F_2(G)=\begin{cases}1\space si \space sol\\0\space sinon\end{cases}$
	- Souci : ne donne aucune information
- $F_3(G)=\text{nb de cases visitées}$
	- Souci : on peut tourner en rond
- $F(G)=\begin{cases}1\text{si solution}\\\alpha F_1(G)+\beta F_3(G) +b\end{cases}$
	- b bonus possible si on s'approche de la solution
	- On peut ponderer alpha et beta pour un meilleur résultat
### Q3
JSP
## Exercice 3
### Q1 : kecese phénotype ?
Le phénotype correspond aux parcours des m véhicules
### Q2
Un codage possible est de stocker dans G  les n lieux selon l'ordre de desserte, en intercalant **(n-1)** valeurs séparatrices pour distinguer les parcours des différents véhicules