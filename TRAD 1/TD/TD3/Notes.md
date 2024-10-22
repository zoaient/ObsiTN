# Analyse syntaxique ascendante et grammaire ambiguë
$$G'\begin{cases} E' \rightarrow E \quad r0\\
E \rightarrow E O E|entier \quad r1,r2\\
O \rightarrow +|-|*|/ \quad r3,r4,r5,r6
\end{cases}$$
> Cette grammaire est ambiguë , exemple : $1+2-3$  , montrons qu'une ambiguïté dans la grammaire implique un conflit dans un automate SLR(1)
## Automate SLR(1)
![[Automate SLR(1)]]
## Table SLR(1)

|     | entier |   +   |   -   |   *   |   /   |  $  |  E  |  O  | E'  |
| :-: | :----: | :---: | :---: | :---: | :---: | :-: | :-: | :-: | :-: |
| I0  |   d2   |       |       |       |       |     |  1  |     |     |
|  1  |        |  d4   |  d5   |  d6   |  d7   | OK  |     |  3  |     |
|  2  |        |  r2   |  r2   |  r2   |  r2   | r2  |     |     |     |
|  3  |   d2   |       |       |       |       |     |  8  |  3  |     |
|  4  |   r3   |       |       |       |       |     |     |     |     |
|  5  |   r4   |       |       |       |       |     |     |     |     |
|  6  |   r5   |       |       |       |       |     |     |     |     |
|  7  |   r6   |       |       |       |       |     |     |     |     |
|  8  |        | d4/r1 | d5/r1 | d6/r1 | d7/r1 |     |     |  3  |     |
> Il y à des conflits lecture reduction, donc la table n'est pas SLR(1)

## Priorités (pile)

| Pile    | mot     | Commentaires                                                                                                             |
| :------ | :------ | ------------------------------------------------------------------------------------------------------------------------ |
| 0       | 1+3\*5$ |                                                                                                                          |
| 012     | +3\*5$  |                                                                                                                          |
| 0E1     | +3\*5$  | r2                                                                                                                       |
| 0E1+4   | 3\*5$   |                                                                                                                          |
| 0E1O3   | 3\*5$   | r3                                                                                                                       |
| 0E1O332 | \*5$    |                                                                                                                          |
| 0E1O3E8 | \*5$    |                                                                                                                          |
| 0E1O3E8 | \*5$    | conflit d6/r1  , d6 seul choix possible pour conserver la priorité , r1 seul choix pour respecter l'associativité gauche |
## Comment rendre l'analyseur déterministe ?
- Enonçons des règles d'associativité
	- %left + - (associativité gauche pour + et -)
	- %left * / (associativité gauche pour \* et /)
		- Plus la règle est basse et plus elle est prioritaire
- Ces règles décomposent l'état 8 en 4 états
	- 8.1 :$E \rightarrow E+E!$
	- 8.2 :$E \rightarrow E-E!$
	- 8.3 :$E \rightarrow E*E!$
	- 8.4 :$E \rightarrow E/E!$
		- 8.1 en présence d'un + - il faut réduire 
		- 8.3 en présence d'un * / il faut lire
		- 8.1 en présence d'un + - il faut réduire
		- 8.1 en présence d'un * / il faut réduire