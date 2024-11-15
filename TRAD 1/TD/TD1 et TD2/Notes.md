# Analyse syntaxique descendante
## Question 1
### Exemples
```
(1,(2.2),3)
nil
23
((2.3),(2,(3.4),nil))
(1)
```
### Test
$$G\begin{cases}
A->(A, B, A)|(nil, B ,A)|(A, B, nil)|(nil, B ,nil)|nil|(B)|(B,B,B)|(B,B,A)|(A,B,B) \\
B->0|1|2|3|4|5|6|7|8|9|0.C|1.C|2.C|3.C|4.C|5.C|6.C|7.C|8.C|9.C\\
C->1|2....|9|....|1C|2C...|9C
\end{cases}$$
### Correction
$$G\begin{cases}
A->V|(A . A)|(A S) \\
S->, A S | \varepsilon \\ 
V->entier | nil \\ 
\end{cases}$$
## Question  2
> ==Cette grammaire n'est pas LL(1) Car A->(A.A)  et A->(A.S)==
### Factorisation de G
![[TRAD 1/TD/TD1 et TD2/AHHHHHHHHH 1.png]]
On à pas fait la question ouin
update : on l'a fait [[TRAD 1/TD/TD4/Notes|la]]
# Analyse syntaxique ascendante
## Exercice 1
### Grammaire utilisée et réductions
$$G\begin{cases}
A'\rightarrow A \quad r0\\
A->V|(A . A)|(A S) \quad r1,r2,r3\\
S->, A S | \varepsilon \quad r4,r5\\ 
V->entier | nil \quad r6,r7\\ 
\end{cases}$$
### Automate LR(0)
#### Comment construire mon automate LR(0) ?
![[Merci typst'n !.png]]
##### Et en français ?
Pour chaque état, pour chaque règle, si on à un non terminal sur le caractère a gauche de notre marqueur, on rajoute l'ensemble des règles produites par ce non terminal avec le marqueur partant du début
Pour l'état initial on part de l'axiome
Sinon, on part des règles ou on peut avancer le marqueur en lisant un caractère spécifique
#### Automate
![[Juste envie de dcd]]
### Table d'analyse SLR(1)
#### Comment Remplir une table d'analyse SLR(1) ?
- Pour les non terminaux
	- Si on va vers un état, mettre l'état
- Pour les terminaux
	- Si on va vers un état , mettre d suivi de état
- Quand il y'a un item avec ! a la fin , exemple A -> a!
	- mettre r : réduction  aux suivants de A
#### Table d'analyse

|     |  (  |  )  | Entier | Nil |  .  |  ,  |  $  | A'  |  A  |  S  |  V  |
| :-: | :-: | :-: | :----: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| I0  | d3  |     |   d4   | d5  |     |     |     |     |  1  |     |  2  |
|  1  |     |     |        |     |     |     | OK  |     |     |     |     |
|  2  |     | r1  |        |     | r1  | r1  | r1  |     |     |     |     |
|  3  | d3  |     |   d4   | d5  |     |     |     |     |  6  |     |  2  |
|  4  |     | r6  |        | d5  | r6  | r6  | r6  |     |     |     |     |
|  5  |     | r7  |        |     | r7  | r7  | r7  |     |     |     |     |
|  6  |     | r5  |        |     | d7  | d9  |     |     |     |  8  |     |
|  7  | d3  |     |   d4   | d5  |     |     |     |     | 10  |     |  2  |
|  8  |     | d11 |        |     |     |     |     |     |     |     |     |
|  9  | d3  |     |   d4   | d5  |     |     |     |     | 12  |     |  2  |
| 10  |     | d13 |        |     |     |     |     |     |     |     |     |
| 11  |     | r3  |        |     | r3  | r3  | r3  |     |     |     |     |
| 12  |     | r5  |        |     |     | d9  |     |     | 14  |     |     |
| 13  |     | r2  |        |     | r2  | r2  | r2  |     |     |     |     |
| 14  |     | r4  |        |     |     |     |     |     |     |     |     |
#### Conclusion
> L'analyseur est SLR(1) car il n'y a pas de conflit
### Pile
![[Pile]]
## Exercice 2
### Grammaire
$$G'\begin{cases}
S'\rightarrow S \quad r0\\
S \rightarrow G=D|G \quad r1,r2\\
G \rightarrow  *D|idf \quad r3,r4\\ 
D \rightarrow G \quad r5\\ 
\end{cases}$$
### Analyseur SLR(1)?
#### Automate LR(0)
![[Ahh]]
> Cela donnerait un conflit si on faisait la table SLR(1) !
##### IMPORTANT
>  ==Il ne peut pas y avoir un conflit lecture/lecture !==
### Analyseur LR(1) ?
#### Automate LR(1) 
##### Comment construire mon automate LR(1) ? 
- Même principe que l'automate LR(0) , a la différence qu'on prend en compte les contextes 
###### Comment calculer mon contexte ?
- Voir CM4

##### Automate LR(1)
![[Automate LR(1)]]
##### Table LR(1)

|     |  =  |  *  | idf |  $  |  G  |  D  |  S  | S'  |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| I0  |     | d4  | d5  |     |  2  |  3  |  1  |     |
|  1  |     |     |     | OK  |     |     |     |     |
|  2  | d6  |     |     | r5  |     |     |     |     |
|  3  |     |     |     | r2  |     |     |     |     |
|  4  |     | d4  | d5  |     |  8  |  7  |     |     |
|  5  | r4  |     |     | r4  |     |     |     |     |
|  6  |     | d11 | d13 |     | 10  |  9  |     |     |
|  7  | r3  |     |     | r3  |     |     |     |     |
|  8  | r5  |     |     | r5  |     |     |     |     |
|  9  |     |     |     | r1  |     |     |     |     |
| 10  |     |     |     | r5  |     |     |     |     |
| 11  |     | d11 | d13 |     | 10  | 12  |     |     |
| 12  |     |     |     | r3  |     |     |     |     |
| 13  |     |     |     | r4  |     |     |     |     |
##### Etats similaires
- I4 - I11
- I7 - I12
- I8 - I10
- I5 - I13
###### Comment fusionner mes états ?
- On regarde dans la table, lorsqu'il n'y a pas de conflit en fusionnant les deux on peut alors les fusionner (j'suis sure que tu ne l'avais pas deviné ca cheffe)
##### Table LALR(1) (Quand on arrive a tout fusionner)

|     |  =  |  *   | idf  |  $  |  G  |  D  |  S  | S'  |
| :-: | :-: | :--: | :--: | :-: | :-: | :-: | :-: | :-: |
| I0  |     |  d4  |  d5  |     |  2  |  3  |  1  |     |
|  1  |     |      |      | OK  |     |     |     |     |
|  2  | d6  |      |      | r5  |     |     |     |     |
|  3  |     |      |      | r2  |     |     |     |     |
| 411 |     | d411 | d513 |     | 810 | 712 |     |     |
| 513 | r4  |      |      | r4  |     |     |     |     |
|  6  |     | d411 | d513 |     | 810 |  9  |     |     |
| 712 | r3  |      |      | r3  |     |     |     |     |
| 810 | r5  |      |      | r5  |     |     |     |     |
|  9  |     |      |      | r1  |     |     |     |     |

> Si on n'arrive pas a fusionner deux états alors l'automate n'est pas LALR(1)