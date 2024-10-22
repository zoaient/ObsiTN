
# Chapitre 1 : Introduction 
## Définitions
### Compilateur : 
- logiciel qui traduit un programme écrit dans un langage de haut niveau en instructions exécutables. Il compile une fois pour toutes, contrairement a l'interpréteur.
### Compilation : 
- Ensemble des algorithmes et des structures de données nécessaires à la traduction.
### Compilateur != Interpréteur
- L'interpréteur ne génère pas d'exécutables.
### Exemples : 
- C est compilé , python est interprété,  java est compilé PUIS interprété.
## Schéma Général d'un compilateur : 

![[Schéma Général d'un compilateur.png]]
## Historique :
- Les langages : c'est vieux, les concepts sont vieux aussi, les compilos aussi, fin ta capté.
## Garbage collector (ramasse miettes (mdr)) :
- Récupère les zones non référencées et réalloue la mémoire (TL:DR , cela permet de compacter la mémoire et donc de pouvoir allouer de grands espaces de mémoire)
# Chapitre 2 Analyseur lexical
## Analyseur lexical :
-  Lit le texte source caractère par caractère (seul "module" du compilateur qui lit le texte source).
- Reconnait les unités lexicales (token) qui sont les mots du langage, et les présente a l'analyseur syntaxique.
- C'est un automate.
- Le lexeur "code" les unités lexicographiques reconnues -> efficacité , dans un lexique.
## Principales unités lexicales :
- Caractères simples : `= , - ( ) '` 
- Unités à 2 caractères : `++  ,  :=  , <= , >=`
- Identificateurs  : `x , y`
- constantes numériques : `3 , 6.2`
- mots clés : `if , then , else`
## Autres taches du lexeur :
- Supprimer les espaces, tabulations, fins de ligne.
- Supprimer les commentaires.
- Afficher les erreurs lexicales : Caractères inconnus , constante trop grande, identifiant trop long
## Lexique
- Table permettant de mémoriser les éléments récurrents.
- Cela permet de réduire la table de l'arbre abstrait sortant.

![[Lexique]]
## Exemple

### Code source
````ceci est un exemple x := y + 2x;````
### Codage des 'caractères simples' , unités lexicales simples :
- '+' codé par 1
- '-' codé par 2
- '* ' codé par 3
### Codage des unités lexicales doubles :
- ':=' codé par 10
- <=  codé par 11
### Codage des mots clés du langage :
- if codé par 20
- then codé par 21
### Codage des unités lexicales génériques
- Identifiants codés par 30
- Constantes codées par 31
### Texte codé
```(30, 1) 10 (30,2) 1 (31,2)3 (30,1)```
