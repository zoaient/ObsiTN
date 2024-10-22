# Exercice 1

## Image
|  0  |  0  |  0  |  3  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|  0  |  0  |  4  |  8  |  5  |  2  |  0  |  0  |  0  |  1  |  0  |  4  |  0  |  0  |
|  0  |  0  |  8  |  9  |  8  |  6  |  4  |  4  |  5  | 10  | 10  | 10  |  5  |  0  |
|  0  |  4  |  9  | 10  |  9  |  8  |  4  |  3  |  2  | 10  | 10  |  8  |  3  |  0  |
|  0  |  0  |  8  |  9  |  8  |  6  |  3  |  2  |  5  |  7  |  9  |  8  |  2  |  0  |
|  0  |  0  |  0  |  3  |  7  |  2  |  5  |  2  |  5  |  2  |  3  |  1  |  0  |  0  |
|  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |

## Q1
- 7 pixels sur 14, soit un ratio d'un pour deux, quantifiée sur 16 niveaux de gris

### Niveaux de gris
> On utilise les niveaux de gris d'une puissance de deux, toujours prendre la puissance de deux supérieure au maximum de niveaux de gris nécessaires

### Dynamique
- Gris plus sombre - gris plus clair , 10-0 = 10 , la dynamique est donc de 10

## Q2
- Le carré apparait rectangulaire parce que l'affichage d'un pixel est rectangulaire

### Résolution
- En x : 2 pixels /mm
- En y : 15 pixels / mm

## Q3
### Conventions

> On commence à compter les lignes et colonnes a 0, les coordonnées sont soit données en lignes colonnes soit en x,y

#### Exemple pour l'image actuelle
- En x,y I(2,1)=
- En i,j I(1,2)=

### Profil de ligne

![[Profil de ligne]]

![[TNI/TD/TD1 et TD2/AHHHHHHHHH 1.png]]
> J'avais pas encore trouvé l'outil grille


![[Profil de ligne plus joli]]
## Q4

### Histogramme sous forme d'un tableau

|  0  |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11-15 |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :---: |
| 50  |  2  |  6  |  6  |  6  |  6  |  2  |  2  |  7  |  5  |  6  |   0   |

## Q5

### Binarisation
Objectif : n'utiliser plus que deux niveaux de gris
- Niveau de gris de fond le plus grand : 4
- Niveau de gris d'objet le plus faible (empiriquement) : 6

> Il faut donc appliquer un filtre pour séparer le fond de l'objet, donc ==entre 4 et 8== environ 

## Q6

### Problématique

> ==Faut t'il raisonner globalement ou localement ?== 

### Moyenne médiane et dynamique locale
- Moyenne pour la ligne i : 5,7 -> 5
- Médiane : 4
- Dynamique/2 : 5
- Localement c'est bien, mais il faut une ligne sur laquelle il y a l'image

###  Moyenne médiane et dynamique globale
- Moyenne : 2.88 -> 3
- Médiane : 1
- Dynamique/2 : 5

### Autres méthodes
- Otsu , exponential fit

## Q7

### Principe

![[Réhaussement]]

### Application 


![[Réhaussement 2]]
## Q8

### Requantification 

#### Formules

$$w=\frac{b-a}{N} \quad T_k = (k-1)w \quad R_k=\frac{N}{N-1} \quad N=4$$

#### Table de correspondance

|  i  |  T  |  R  |
| :-: | :-: | :-: |
|  1  |  0  |  0  |
|  2  |  4  |  5  |
|  3  |  8  | 11  |
|  4  | 12  | 15  |
#### Requantification

![[Requantification]]

## Q9
# Exercice 2
## Principe
> On utile une transformation en deux seuils, pour pouvoir augmenter le contraste et voir que du noir ou que du blanc.


![[Transformation en deux seuils]]

## Lut 
> Lookup table - table de correspondance 