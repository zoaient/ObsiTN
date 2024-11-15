# Exercice 1 : Morphologie mathématique
$$B_0=\begin{matrix}
1 & \underline{1} & 1
\end{matrix}$$
$$B_1=\begin{matrix}
1 \\
\underline{1}
\end{matrix}$$
**Le 1 souligné indique qu'on se centre sur ce 1 pour le produit de convolution**
## Exemple
$$I=\begin{matrix}
0 & 1 & 0
\end{matrix}$$
### Dilatation
**On fait des OU logique entre les résultats du produit de convolution ici :**
$$\begin{matrix}
0 & 1 & 0
\end{matrix} \rightarrow 1$$
### Erosion
**On fait des ET entre les résultats du produit de convolution ici :**
$$\begin{matrix}
0 & 1 & 0
\end{matrix} \rightarrow 0$$
> Ouverture : Erosion + Dilatation
> Fermeture : Dilatation + Erosion

## Application de la fermeture

### Avant fermeture
![[Image avant dilatation.png]]
### Après fermeture avec $B_0$
![[Image apres dilatation.png]]
**Note a moi meme, plus jamais d'excel**
![[AHHHHHHHHH.png]]
### Après fermeture avec $B_1$
![[Image après dilatation 2.png]]
**le carré à été déplacé vers le bas**
# Exercice 3 Erosion - Dilatation
