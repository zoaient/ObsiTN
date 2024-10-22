# Exercice 1 
## Q1

| Toto.txt existe | oui | oui | non | non |
| :-------------- | :-- | :-- | :-- | :-- |
| Titi.txt existe | oui | non | oui | non |
| fd2             | 3   | -1  | 3   | -1  |
| errno           | 0   | 2   | 9   | 2   |
- fd1 = 3 (premiere code possible après stdin = 1 stdout =2 stderr =3)
	- Réattribué avec close (fd1)
- 2 correspond au code "il n'y a pas de fichier"
- 9 comme erreur car on ferme un fichier qui n'existe pas 
	- errno correspond a la dernière erreur en date, elle est donc produite pour le dernier cas MAIS est overwrite par une autre erreur 
## Q2
### Deux open
#### OFT
- Table globale pour tout les processus
- Les descripteurs pointent vers cette table
	- "Un open, une entrée"
- Cette table contient les positions de lecture
#### Programme
- fd1 =3
- fd2 = 4
- Lorsqu'on lit fd1 , la position est update dans l'OFT **uniquement** pour fd1
	- On lit alors "L"
- Pareil pour fd2
- Alors on print "L"
![[EX1Q2P1]]
### Après fork
- La "table des erreurs" (je ne sais pas comment appeler ca) est unique a chaque processus, ici elle se répète avec un fork
	- Dans ce cas, fd=3 dans le processus père **et** le processus fils
		- Donc, une lecture va update la position dans l'OFT pour les deux
			- Alors, on lit "L" , puis "A" et on print "A"
![[EX1Q2P2]]
### Après (fel)dup
#### Dup(lication)
- Fait pointer un nouveau descripteur vers une nouvelle entrée dans l'OFT (crée un nouveau descripteur)
- On obtient "A" , heuuu j'ai pas tout suivi
# Exercice 2
## Q3
- Le shell crée un fork à chaque commande utilisée avec un exec("commande")
```
if(fork()){
fd=open("toto")
dup2(fd,0)
exec("cat","cat","N)
}
```
- dup2(fd,0) permet de renvoyer l'entrée standard (stdin) vers la ou pointe le descripteur fd , cela traduit le symbole "<"
## Q4, Q5
![[AHHHHHHHHH.png]]
# Exercice 3
## Q6 
### Principe
![[Q6 , principe]]
#### Pipe (mdr)
> **pipe**() crée un tube, un canal unidirectionnel de données qui peut être utilisé pour la communication entre processus. Le tableau _pipefd_ est utilisé pour renvoyé deux descripteurs de fichier faisant référence aux extrémités du tube. _pipefd[0]_ fait référence à l'extrémité de lecture du tube. _pipefd[1]_ fait référence à l'extrémité d'écriture du tube. Les données écrites sur l'extrémité d'écriture du tube sont mises en mémoire tampon par le noyau jusqu'à ce qu'elles soient lues sur l'extrémité de lecture du tube. 
```
int mypopen(char * cwd)
int fd[2]
pipe(fd)
if(fork()){
	close fd[1]
	return fd[0]
}else{
	close fd[0]
	dup2(fd[1],0)
	close fd[1]
	exec ("sh","sh","-c",cmd,NULL)
}
```