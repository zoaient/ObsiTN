# Definitions
## AST (Abstract syntax tree) ou ASA (Arbre Syntaxique Abstrait)
Un AST est une structure permettant de représenter la construction d'un code a partir d'une grammaire, les noeuds représentent les non terminaux de la grammaire et les feuilles les symboles terminaux, dans le cadre d'un compilateur, il est produit par le parser
### Arbre syntaxique abstrait
Ce qui différencie un arbre syntaxique abstrait d'un arbre syntaxique normal c'est la suppression de tout les noeuds "inutiles" dans le sens qu'ils ne donnent aucune information et ne servent uniquement qu'a construire l'arbre
Typiquement, un noeud avec un seul fils est inutile et peut être supprimé, le fils de ce noeud allant directement au père de ce noeud. ce processus en général s'appelle l'élagage, L'ASA est donc indépendant de la grammaire
## Analyse syntaxique ascendante et famille LR(k)
Le principe d'une analyse syntaxique ascendante (voir parser : voir AST) est de construire notre arbre syntaxique en partant du bas (donc des feuilles) , pour cela on construit un automate LR(k) (généralement 1 ou 0)
Un automate LR(k) signifie qu'on lit le texte de gauche à droite (Left to right scanning, Rightmost derivation) et le k signifie le nombre de caractères qui nous faut lire en avance du caractère qu'on est en train de traiter pour prendre une décision(soit décalage ou réduction), ainsi, dans un  automate LR(0) , nous n'avons pas besoin de connaitre le caractère d'après pour construire notre arbre syntaxique
### Analyse syntaxique ascendante exemple
![[Analyse Syntaxique Ascendante]]
### Item
C’est la production de G avec un marqueur en partie droite. 
#### Exemple de construction d'un automate LR(0)
$$G\begin{cases}
A'\rightarrow A \quad r0\\
A->V|(A . A)|(A S) \quad r1,r2,r3\\
S->, A S | \varepsilon \quad r4,r5\\ 
V->entier | nil \quad r6,r7\\ 
\end{cases}$$

- On part de l'état 0, avec tout les items liés a la fermeture de l'axiome
- Pour chaque terminal ou non terminal qu'on peut lire à partir de ces items on construit un nouvel état avec l'item qu'on a utilisé, on avance notre marqueur d'un
- ![[Merci typst'n !.png]]
- ##### Et en français ?
Pour chaque état, pour chaque règle, si on à un non terminal sur le caractère a gauche de notre marqueur, on rajoute l'ensemble des règles produites par ce non terminal avec le marqueur partant du début
Pour l'état initial on part de l'axiome
Sinon, on part des règles ou on peut avancer le marqueur en lisant un caractère spécifique
![[Juste envie de dcd]]
#### Table SLR(1) et Table LR(0)
La table SLR(1) (pour Short LR) reprend les informations de l'automate LR(0) dans une table divisée en deux sous tables, une table d'action pour les terminaux et une table de transition pour les non terminaux: elle se remplit de la manière suivante
- Pour les non terminaux
	- Si on va vers un état, mettre l'état
- Pour les terminaux
	- Si on va vers un état , mettre d suivi de état
- Quand il y'a un item avec ! a la fin , exemple A -> a!
	- Pour SLR(1) UNIQUEMENT : mettre r : réduction avec le numéro de la réduction liée a la règle utilisée aux suivants de A (ne pas oublier dollar)
	- Pour LR(0) UNIQUEMENT : mettre r : réduction avec le numéro de la réduction liée a la règle utilisée a tout les terminaux présents dans la règle et dollar (Ici, on note r reduction pour a ET dollar)
- Lorsqu'on a lu l'axiome dans l'état i , 
	- Mettre OK ligne i colonne dollar

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
| 12  |     | r5  |        |     |     | d9  |     |     |     | 14  |     |
| 13  |     | r2  |        |     | r2  | r2  | r2  |     |     |     |     |
| 14  |     | r4  |        |     |     |     |     |     |     |     |     |
Pour une table SLR(1) : Si il n'y a pas de conflits lecture/reduction, alors l'analyseur syntaxique est SLR(1)
#### Lecture d'un mot par une pile
- On regarde l'état dans lequel on est, si le caractère suivant est dans la table et lisible on le lit, on le met dans la pile ainsi que l'état dans lequel on va
- Si il y'a une réduction, on remplace tout ce qui est a remplacer dans la pile par ca, on revient dans l'état avant la réduction (donc celui a gauche de tout ce qu'on a enlevé , si c'est espilon on n'enlève rien)
- Le mot est lisible si on arrive a OK a la fin
### Automate LR(1)
#### Contexte ?
Le contexte, ou symbole de précision, est rajouté a un item pour un analyseur syntaxique LR(1) , il permet de savoir un caractère en avance et donc de créer des items différents pour éviter les shift reduce conflicts
Lorsqu'on calcule un état, et qu'on ajoute item par fermeture, on prend le premier de ce qui suit le non terminal qu'on a ajouté, a défaut, on remet le contexte précédent
##### Etat de l'automate LR(1)
- Ensemble des items LR(1) obtenus par ==fermeture==
- Calcul des fermetures pour un état I:
	- Si $[A \rightarrow \alpha .B \beta,a]$  est dans I
	- Si $[B \rightarrow \gamma ]\in G$
		- Alors ajouter $[B \rightarrow .\gamma ,b]ou \quad b \in Premier(\beta a)$
Ensuite, la table LR(1) se construit de la meme manière
#### Table LALR(1)
On fusionne les états similaires a contexte près, si ils ne provoquent pas de conflits lors de la fusion
## Analyse syntaxique descendante et Analyseur LL(1)
### Grammaire LL(1)
Symbole directeur $SD(A\rightarrow a)$ : Si on ne peut pas réécrire a en $\varepsilon$ alors $SD(A\rightarrow a)=Premier(a)$, sinon $SD(A\rightarrow a)=Premiers(a) \bigcup Suivants(A)$
Pour qu'une grammaire soit LL(1), il faut que l'intersection de tout ses symboles directeurs des règles différentes soient vides (par règles différentes, on entend par exemple $A\rightarrow a\space,A\rightarrow b$)


## Pile
### Chaînages
Chaînage statique : va au chaînage statique du bloc qui englobe la fonction (en cas de déclaration dans une déclaration) ou tout en bas si il n'y à pas de dit bloc, il n'y a pas besoin de chaînage statique dans tout les langages, par exemple en C il n'y en a pas besoin car on ne peut pas déclarer une fonction dans une déclaration de fonction (ou dans une fonction tout court)
Chaînage dynamique : va au chaînage dynamique de la fonction appelante

La pile sert à stocker les valeurs des variables. \
  Le chaînage dynamique sert à stocker les valeurs des variables et des constantes. \
  Le chaînage statique sert à stocker les valeurs des variables et des constantes, et à accéder aux variables locales et aux paramètres des fonctions. \ 
  L'appelant met en place les paramètres, les chaînages ainsi que de l'adresse de retour, tandis que l'appelé accède à ses valeurs.
### Exemple
[[TRAD 1/TD/TD7/Notes|Ici]]

## Trivia (Mais important quand même hein)
- Le mot vide n'est pas une unité lexicale, on ne la lit pas sous peine de se faire défoncer
- Structure d'un compilateur![[Pasted image 20241112163013.png]]
- D'apres wikipedia : La **surcharge de fonction** (également connue sous le nom de **surdéfinition**, **[polymorphisme](https://fr.wikipedia.org/wiki/Polymorphisme_(informatique) "Polymorphisme (informatique)") ad hoc** ou _**overloading**_ en anglais) est une possibilité offerte par certains [langages de programmation](https://fr.wikipedia.org/wiki/Langage_de_programmation "Langage de programmation") de définir plusieurs [fonctions](https://fr.wikipedia.org/wiki/Fonction_informatique "Fonction informatique") ou [méthodes](https://fr.wikipedia.org/wiki/M%C3%A9thode_(informatique) "Méthode (informatique)") de même nom, mais qui diffèrent par le nombre ou le [type](https://fr.wikipedia.org/wiki/Type_(informatique) "Type (informatique)") des [paramètres effectifs](https://fr.wikipedia.org/wiki/Param%C3%A8tre_effectif "Paramètre effectif"). Le polymorphisme ad hoc ne doit pas être confondu avec le polymorphisme d'inclusion des [langages à objets](https://fr.wikipedia.org/wiki/Programmation_orient%C3%A9e_objet "Programmation orientée objet"), permis par l'[héritage](https://fr.wikipedia.org/wiki/H%C3%A9ritage_(informatique) "Héritage (informatique)") de [classe](https://fr.wikipedia.org/wiki/Classe_(informatique) "Classe (informatique)") et la redéfinition de méthode (_overriding_ en anglais). La surcharge peut être [statique](https://fr.wikipedia.org/wiki/Typage_statique "Typage statique") (le choix de la version est alors fait en fonction du nombre d'arguments et de leur type statique [déclaré](https://fr.wikipedia.org/wiki/D%C3%A9claration_(informatique) "Déclaration (informatique)") à la [compilation](https://fr.wikipedia.org/wiki/Compilateur "Compilateur")) ou [dynamique](https://fr.wikipedia.org/wiki/Typage_dynamique "Typage dynamique") (le choix de la version est alors fait en fonction du type dynamique des arguments constaté à l'exécution). La surcharge dynamique est également appelée « [dispatch multiple](https://fr.wikipedia.org/wiki/Dispatch_multiple "Dispatch multiple") » et une méthode surchargée dynamiquement « multiméthode ».
- Garbage collector: Reponsable du recyclage de la mémoire préalablement utilisée mais liberée