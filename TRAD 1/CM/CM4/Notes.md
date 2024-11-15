# Analyseurs Ascendants LR(1)

## Principe 
$$I_i=\begin{cases}A\rightarrow B.aDa\\
D \rightarrow B. \\
...

\end{cases}
I_j=\begin{cases}A\rightarrow Ba.Da\\
...

\end{cases}$$
- Si on lit ==a=== :
	- Action (Ii,a) = "décaler" et on a aussi :
	- Action (Ii,a) = "réduire par D -> B"
		- Il y a un conflit dans la table !
			- Quelle table au juste ? j'en sais rien, c'est pas grave, je suis sur le coup (non)

- On va ajouter 1 info supplémentaire dans les items:
	- Un item devient $[A\rightarrow \alpha .\beta, a] ou A \rightarrow \alpha \beta \in G \quad \text{et a est un terminal, ou \$}$
		- a est le ==contexte== ou symbole de ==prévision==
			 - La prévision du contexte n'aura un effet que sur les items de la forme $[A\rightarrow \alpha ., a]$ ou l'action dans la table devient "réduire par $[A\rightarrow  \alpha]$  uniquement pour le symbole a"
## Définition et construction des items LR(1)
### Rappel
- Les analyseurs syntaxique ascendant LR(0) et SLR(1) sont basés sur un automate LR(0)
	- Cet automate est constitué d'items LR(0)
### Item LR(1)
- $[A \rightarrow \alpha .\beta,a]$

### Table d'analyse syntaxique ascendante LR(1)
- (idem pour SLR(1))
- La différence est sur les réductions
#### Exemple
$$\begin{cases}S' \rightarrow S \quad r0\\
S \rightarrow CC \quad r1\\
C \rightarrow aC \quad r2\\
d\quad r3\end{cases}$$
##### ASA LR(1) ?
##### Automate LR(1)
![[Table LR(1)]]
##### Table LR(1)
|     |  a  |  d  |  $  |  C  |  S  | S'  |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| I0  | d3  | d4  |     |  2  |  1  |     |
|  1  |     |     | OK  |     |     |     |
|  2  | d6  | d7  |     |  5  |     |     |
|  3  | d3  |     |     |  8  |     |     |
|  4  | r3  | r3  |     |     |     |     |
|  5  |     |     | r1  |     |     |     |
|  6  | d6  | d7  |     |  9  |     |     |
|  7  |     |     | r3  |     |     |     |
|  8  | r2  | r2  |     |     |     |     |
|  9  |     |     | r2  |     |     |     |
##### Conclusion
> Il n'y a pas de conflits lecture/reduction ou reduction/reduction dans cette table, alors on peut construire un analyseur LR(1) pour cette grammaire
##### Simplification de l'automate
- I4-I7 , I8-I9 , I3-I6 sont des états similaires a contexte près
##### Construction de la table d'analyse LALR(1)
- A partir de l'automate LR(1) et des items LR(1)
	- Avec fusion d'états ayant le même noyau (hors contexte)
###### Exemple de fusion
$$I_i=[C\rightarrow d!,[a,d]],\quad I_j=[C \rightarrow d!,[$]]$$
- Donnent
$$I_{i,j}=[C \rightarrow d!, [a,d,$]$$
###### Table LALR(1)

|     |  a  |  d  |  $  |  C  |  S  | S'  |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| I0  | d36 | d47 |     |  2  |  1  |     |
|  1  |     |     | OK  |     |     |     |
|  2  | d36 | d47 |     |  5  |     |     |
| 36  | d36 | d47 |     | 83  |     |     |
| 47  | r3  | r3  | r3  |     |     |     |
|  5  |     |     | r1  |     |     |     |
| 89  | r2  | r2  | r3  |     |     |     |

### Analyseur LR(1) et grammaire



