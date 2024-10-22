# Introduction ?
## Pourquoi des cours de système ?
- Concepts fondamentaux de l'informatique:
	- Information
	- Machine
	- Algorithme
	- Langage

> En gros, ca sert à plein de trucs 

Objectif :

> Comment utiliser efficacement le système d'exploitation ?


## Qu'est ce qu'un système d'exploitation ? 

### OS (operative system)
- Logiciel qui permet l'exploitation du matériel (interface inférieure) offrant des services (interface supérieure unifiée) aux applications


![[Systèmes/CM/CM1/Schema 1]]![[Schema 2]]
### Role de L'OS: intermédiaire matériel <-> applications

#### Deux fonctions complémentaires :

##### Adaptation d'interface
- Offre une interface plus pratique que le matériel
- Dissimule les détails de mise en oeuvre (abstraction)


### Fonctions du système d'exploitation

#### Gestion de l'activité
- Déroulement de l'exécution (processus) géré par le cpu
- Evénements matériels , cpu

#### Gestion de l'information
- Accès dynamique (exécution, mémoire) , mémoire principale
- Conservation permanente
- Partage

#### Gestion des communications
- Interface avec utilisateur
- Impression et périphériques
- Réseau

#### Protection
- De l'information
- Des ressources


## Evolution des systèmes d'exploitation

### Une machine, un utilisateur, une application
-  A l'origine pas d'OS !
	- Besoin d'un opérateur au début
	- Aujourd'hui systèmes embarqués
	- Entre les deux MS DOS


### Systèmes monoprogrammés

#### Problème
- Usage inefficace des ressources matérielles : pas de recouvrement des ES

#### Solution
- Permettre la coexistence de plusieurs programmes dans le système afin de maximiser l'utilisation du matériel

### Systèmes multiprogrammés (multijob)
- Plusieurs programmes peuvent être chargés en mémoire en même temps
	- Si un processus se bloque, un autre peut être exécuté
- Problèmes liés a la concurrence entre processus sont a résoudre : si un processus fait une boucle infinie , écrit dans la mémoire d'un autre processus ? 
	- Fonction de protection a assurer par l'os

### Systèmes multi-utilisateur (multiuser)
- Apparus avec l'arrivée des terminaux
- J'arrive pas a écrire assez vite bordel

# Pourquoi UNIX ?

## Qu'est ce que UNIX ? pourquoi étudier UNIX ?
- C'est bien

## Et windows ? 
- C'est pas bien 