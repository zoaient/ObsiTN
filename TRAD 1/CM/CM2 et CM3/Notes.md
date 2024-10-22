# Chapitre 3 Analyse syntaxique
## ATTENTION ZOE

> j'ai loupé le cm3 je fais de mon mieux la team !
![[AHHHHHHHHH.png]]
## But
- Vérifier que la phrase en entrée est conforme à la syntaxe du langage
	- Définie par une grammaire
- Dans le cadre du projet il faudra être capable de reconnaitre les unités syntaxiques décrites par la grammaire, en particulier le déclarations , les instructions , les variables, les expressions

## Détecter les erreurs syntaxiques
- Parfois, le parseur propose une correction
	- Il localise l'erreur
		- Numéro de ligne
		- Message clair
- Il n'arrête pas a la première erreur syntaxique rencontrée , mais ne passe pas a l'étape suivante si il y a des erreurs 

## Exemple

![[Analyse Syntaxique Descendante]]


## Analyse Syntaxique descendante (ASA)

### Principe
- On part du mot à analyser
- On remplace itérativement des fragments du mot courant qui correspondent exactement à des membres droits de la règle de production par le membre gauche de cette règle
- Succès si le mot courant final est l'axiome de la grammaire
- Deux actions principales en ASA
	- Décalage (ou lecture)
	- Réduction


> ===Les ASA fonctionnent avec une Pile===
### Exemple

![[Analyse Syntaxique Ascendante]]

### Dénomination des ASA

#### Définitions 
- Item : C'est une production de G avec un marqueur en partie droite
	- Exemple, pour [A -> aAbB] appartenant a G il y à 5 items possibles
	- A -> .aAbB
	- A -> a.AbB
	- A -> aA.bB
	- A -> aAb.B
	- A -> aAbB.
- Etat Ic : un ensemble d'états obtenus par fermeture
- Fermeture(I): un ensemble d'items construits à partir de I selon l'algo suivant:
	- Placer chaque item de I dans Fermeture (I)
	- Si [A -> aBb] appartenant à Fermeture (I) et [B -> c]
		- Alors ajouter [B-> .c] à Fermeture (I) sauf si déjà déduit
	- Itérer jusqu'à ne plus trouver d'items a ajouter a fermeture(I)

> ==Le mot vide "^" n'est pas une unité lexicale => on ne le lit pas==
> A -> ^ donne l'item A -> .


### Famille LR(k)
- Left to right scanning 
- Right to left dérivation
- On utilise les k unités lexicales, du mot d'entrée pour faire la prédiction

#### Exemple

On considère la grammaire suivante

$$\begin{cases}
S'->S\\
S->Ac\\
A->AaAb \\
A->s
\end{cases}$$

##### Comment reconnaitre les états ?
![[Merci typst'n !.png]]
##### Construction de l'automate LR(0)
![[Construction de l'automate LR(0)]]

> L'automate LR(0 est en fait codé dans une table partagée en :

###### Table d'action

$$Si \quad [S' \rightarrow S!] \in I_i \quad Action(I_i,\$) = "accepter" $$
	$$Si [X \rightarrow \beta] \in I_i, X \neq S' \text{(ou S' est l'axiome), alors Action}(I_i,a)=\text{"réduire avec"}X \rightarrow \beta \quad ou \forall a \in T \cup \$ $$

$$Si [X \rightarrow \alpha.a\beta]  \in I_i, \text{alors ACTION}(I_i,a)=\text{"aller a l'état"}I_j$$

$$\text{"erreur" dans toutes les autres cases}$$ 
###### Table de transition
$$\text{Si dans l'automate on a transition}(I_i,X)=I_j\text{alors TRANSITION}(I_i,X)=j$$