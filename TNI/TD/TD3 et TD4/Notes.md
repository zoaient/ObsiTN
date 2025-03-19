# Exercice 1
## 1 : Comment appliquer ma convolution ?
$$f=\begin{pmatrix}
1/9 & 1/9 & 1/9 \\
1/9 & 1/9 & 1/9 \\
1/9 & 1/9 & 1/9
\end{pmatrix}$$
- Il faut placer le filtre sur l'image et additionner les pixels multipliés par les coefficients du masque
	- Pour cela il faut retourner l'image horizontalement et verticalement
### Le problème des effets de bord
- Pour appliquer le masque aux bords de l'image, on manque des informations
	- Pour cela, on peut rajouter des informations mais cela crée des effets de bord
	- Sinon, on ne calcule que la ou c'est possible et on rajoute ensuite l'information en fonction des pixels proches
### Image après filtrage

| 100 | 100 | 90  | 90  | 90  | 100 | 111 | 111 | 111 | 100 | 100 |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 100 | 100 | 90  | 90  | 90  | 100 | 111 | 111 | 111 | 100 | 100 |
| 100 | 100 | 90  | 90  | 90  | 100 | 111 | 111 | 111 | 100 | 100 |
## 2 : Pic d'intensité

![[pic d'intensité]]
- La surface du pic d'intensité à augmenté mais son intensité a diminué
# Exercice 2
## 1 : C'est quoi les filtres de Prewitt et Sobel ?
$$Prewitt,nord : \begin{pmatrix}
1 & 1 & 1 \\
0 & 0 & 0 \\
-1 & -1 & -1
\end{pmatrix} , Sobel,nord : \begin{pmatrix}
1 & 2 & 1 \\
0 & 0 & 0 \\
-1 & -2 & -1
\end{pmatrix}$$
- Ces filtres servent à faire de la detection de contours, ce sont des filtres passe haut. (les contours correspondent à des hautes fréquences)
	- Une variation brusque d'intensité de niveau de gris pour un profil de ligne correspond, dans le domaine de Fourier sur une grande fréquence, et inversement.
		- Ce qui est intéressant, c'est qu'on connait les capacités humaines dans le domaine fréquentiel.
### Composante Est
$$Prewitt,est : \begin{pmatrix}
-1 & 0 & 1 \\
-1 & 0 & 1 \\
-1 & 0 & 1
\end{pmatrix} , Sobel,est : \begin{pmatrix}
-1 & 0 & 1 \\
-2 & 0 & 2 \\
-1 & 0 & 1
\end{pmatrix}$$
## 2 : Tableau
### Comment calculer mes composantes ?
- Voir ex 1
	- Ne pas oublier de renverser l'image horizontalement et verticalement
	- Donne l'indication de si il y'a un contour ou pas à cet endroit la

| Masque  | Composante Nord$\frac{\partial I}{\partial y}$<br> | Composante Est $\frac{\partial I}{\partial x}$ | Module(Cnord²+Cest²)^1/2 | Angle Est par rapport à Nord (arctan) |
| :-----: | :------------------------------------------------: | :--------------------------------------------: | :----------------------: | :-----------------------------------: |
| Prewitt |                         -9                         |                      -12                       |     $\sqrt{225}=15$      |                  37°                  |
|  Sobel  |                        -13                         |                      -17                       |       $\sqrt{458}$       |                                       |

# Exercice 3
## Image

| 4   | 3   | 4   | 5   | 25  | 30  | 28  | 25  | 24  | 5   | 6   | 4   | 6   | 3   | 4   | 4   |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- |
## Filtre
$$f = \begin{pmatrix}
-1 & 0 & 1
\end{pmatrix}$$
## 1 : Filtrage
### Image retournée

| 4   | 4   | 3   | 6   | 4   | 6   | 5   | 24  | 25  | 28  | 30  | 25  | 5   | 4   | 3   | 4   |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- |
### Image filtrée
| -1  | -1  | 2   | 1   | 0   | 1   | 18  | 20  | 4   | 5   | -3  | -25 | -21 | -2  | 0   | 0   |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- |
- **Oupsie je l'ai fait a l'envers**
## 2 : 
# Exercice 4 : Filtre médian
- On applique la médiane des pixels dans la fenêtre
- Pour la ligne $i_1$ on obtient **255,255,255,255,255,8,255,255,255,255**
- Pour la ligne $i_2$ on obtient **255,255,1,0,0,0,0,2,255,255**