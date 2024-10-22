# Exercice 2 : mots de Dyck
$$ \begin{cases}LP' \rightarrow LP \space r0 \\
LP1 \rightarrow UE \space LP2 \space r1 \\
\quad \quad UE \space r2\\
UE \rightarrow (LP) r3\\
\quad \quad (\varepsilon)r4\end{cases}
$$
## Définitions 
### Attributs (valeurs) synthétisés
**Ceux dont la valeur est déterminée a partir des valeurs des attributs des fils**
- Adapté au parcours ascendants
### Attributs hérités
**Ceux dont la valeur est calculée par un parcours descendant (donc à partir des valeurs du père**
## Question 1 : nombre de mots
### Mot utilisé
```(())()()(()())```
### Arbre syntaxique
![[TRAD 1/TD/TD5/Arbre syntaxique|Arbre syntaxique]]
### Règles utilisées
- Pour r0 , $écrire (nbmot(LP))$
- Pour r1,  $nbmot(LP1)=nbmot(LP2)++$
- Pour r2, $nbmot(LP)=1$
> Il y'a donc 4 mots au final
## Question 2 profondeur max
### Règles utilisées
- Pour r0 , $écrire, profmax(LP)$
- Pour r1 ,$profmax(LP1)=max(profmax(UE),profmax(LP2))$ 
- Pour r2, $profmax(LP)=profmax(UE)$
- Pour r3, $profmax(UE)=profmax(LP)++$
- Pour r4, $profmax=1$
# Exercice 3 : Nombres binaires
## Grammaire
$$\begin{cases}N \rightarrow L \quad r_0\\
N\rightarrow L.L \quad r1\\
L\rightarrow B \quad r_2\\
L\rightarrow B\space L \quad r_3\\
B\rightarrow 0 \quad r_4\\
B\rightarrow 1 \quad r_5
\end{cases}$$
> En binaire, 1011.1101 donne 11,8125
### Arbre syntaxique correspondant au mot
![[Arbre syntaxique correspondant]]
> **On peut utiliser une variable globale , ici pour faire un compteur de digit utilisés**
### Variables globales
- Valeur_10 (valeur en base 10)=0
- Partie_décimale = Faux
### Règles utilisées
- Pour r4 : Empiler 0
- Pour r5 : Empiler 1
- Pour r2 : f1
	- x= Dépile
	- if Partie_décimale :
		- Valeur_10+=x\*2^exp
		- partie_decimale = true
	- 