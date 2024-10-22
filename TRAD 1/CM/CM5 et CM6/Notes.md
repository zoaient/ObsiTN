# ASA et grammaire ambigue
## Exemple
- J'ai pas compris, aled
## Comment lever le problème ?
- Modifier la grammaire
- Garder la grammaire et utiliser les ==précédences==
### Utiliser les précédences de token
- Par ex : * a une précédence plus haute que +
	- Soit $$\begin{cases}P \rightarrow \alpha.t \beta. \{...\} \quad \text{décalage sur t}\\ Q \rightarrow \gamma u R.,\{t\}\quad \text{réduce pour t}\end{cases}$$
	- Si le symbole de prévision est t, on a 3 possibilités dans cet item, ==u== est déjà empilé. On va comparer u et t.
		-  ==u== à une précédence supérieure a ==t==
			- Alors $prec(u) > prec(t) \implies REDUCE$
		-  ==u== à une précédence inférieure à ==t==
			- Alors $prec(u) < prec(t) \implies LECTURE$
		-  ==u== à une précédence égale à ==t==
			- Alors $prec(u) = prec(t) \implies SHIFT/REDUCE$
				- Voir TD
> L'associativité gauche ou droite conditionne la grammaire (si la grammaire penche a gauche ou a droite)
> Les symboles prioritaires sont au plus bas dans l'arbre syntaxique

# ASA : Ajouter dans la grammaire des ''fonctions sémantiques''

## Que signifie le "k" dans LR(k), SLR(k) ?
- On regarde k unités lexicales d'avance qu'on utilise lors d'une réduction
# CHAPITRE 4 : Analyse sémantique
- Se passe après l'analyse lexicale
- But final : représenter le programme sous forme d'un arbre abstrait pour vérifier que le programme satisfait un ensemble de règles de construction défini
	- Cet arbre enlève tout les terminaux, c'est la forme minimale du programme avec toutes les informations nécessaires
## Exemples de règles sémantiques
- Double déclaration de variable et de fonctions impossible
- Impossibilité de déclarer des variables avant de les utiliser
- Compatibilité de type
- Nombre de paramètres effectifs
### Contrôle sémantique dynamique
- Statique = connu a la compilation
- Dynamique = connu a l'exécution
- Exemple : la division par zéro
	- Si x=y/z c'est correct statiquement, mais z peut être égal a 0 et donc être faux dynamiquement

![[TRAD 1/CM/CM5 et CM6/schema 1]]
### Table des symboles
- Table par bloc
- Contient toutes les déclarations 
- oh smr pas la force de suivre
- 