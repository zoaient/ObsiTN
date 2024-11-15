# TD CSP Exercice 1 : Rendu de monnaie
![[AHHHHHHHHH.png]]
On a pas le TD VOUINNNNNNNNNNN, update on l'a , bravo

## Qu'est ce que c'est un CSP ?
> Un problème de satisfaction de contraintes ou CSP (Constraint Satisfaction Problem) c'est : 
• n variables x 1 , x 2 ,…,x n 
• Pour chaque variable x j , un domaine fini D j de valeurs possibles (souvent D j = Ν) • m contraintes C 1 , C 2 ,…,C m où C i Í D i1 x D i2 x …x D ik1 est une relation entre k i variables 
• Une solution est l'affectation d'une valeur de D j à x j , pour tout j=1…n telle que toutes les relations C i sont satisfaites
## Question 1 
### Variables
$X=(XE2,XE1,XC50,XC20,XC10), X<i>:$nb de pieces de type i a rendre
### Domaines
$DE2=\{0,...,RE2\}$
$DE1=\{0,...,RE1\}$
$DC50=\{0,...,RC50\}$
$DC20=\{0,...,RC20\}$
$DC10=\{0,...,RC10\}$

> Ici $D<i>$ correspond au domaine de $X<i>$ , donc ici le nombre de pieces rendues est entre 0 et le nombre maximal de pièces en stock.
### Contraintes
$C_D=T-P=XE2*200+XE1*100+XC50*50+XC20*20+X10*10$
- *Cette contrainte est une contrainte globale, elle nous limite sur les algorithmes de résolution à utiliser*
	- Générer et test
	- Backtracking
> Cette liste de contraintes ne s'appliquent qu'aux contraintes unaires ou binaires
> - Forward checking
> - Partial lookahead
> - full lookahead
> - AC3
## Question 2
$A$ : ensemble des affectations completes
$S$ : ensemble des solutions

$A=DE2*DE1*DC50*DC20*DC10$ **(au sens du produit cartésien)**
$S=\{a\in A|\text{a satisfait la contrainte }C_D\}$
$L(a)=\sum_{a\in S}a[i]=XE2+XE1+XC50+XC20+XC10$
### But
$a^*=argmin(L(a))$
## Question 3
### Approche gloutonne
- Pour rendre le moins de pièces je crois que ca marche ? ah en fait non
# Exercice 2 : Coloration de graphe

## Question 1
### Variables
$X=\{XWA,XNT,XSA,XQS,XSW,XVI,XTA\}$
### Domaines
$DWA=\{rouge,bleu,vert\}$
$DNT=\{rouge,bleu,vert\}$
$DSA=\{rouge,bleu,vert\}$
$DQS=\{rouge,bleu,vert\}$
$DSW=\{rouge,bleu,vert\}$
$DVI=\{rouge,bleu,vert\}$
$DTA=\{rouge,bleu,vert\}$
### Contraintes
$XWA\neq XNT$
$XWA\neq XSA$
$XNT\neq XSA$
$XNT \neq XQS$
$XSA \neq XQS$
$XSA \neq XSW$
$XSA \neq XVI$
$XQS\neq XSW$
$XSW \neq XVI$
## Question 2
![[Australie]]
## Question 3
### But de l'algo AC-3
- On essaie de diminuer le domaine de chaque variable (cela facilite l'application du backtracking)
- Meilleur prétraitement possible

Au final , il n'y a pas de simplification a faire (j'ai pas tout compris ???)
## Question 4
### Application du backtracking
- L'ordre d'instanciation est arbitraire, ici XSW, XNT, XQA , XSA , XTA , XVI, XWA
- Ordre des valeurs R V B

![[Backtracking]]
## Question 5
- même ordre d'instanciation et de valeurs que Q4
### Forward checking
$XSW=R$ donc $DSA=DQA=DVI=\{V,B\}$
$XNT=R$ donc $DWA= \{V,B\}$ 
$XQ=V$ donc $DSA=\{B\}$
$XSA=B$ donc $DV=DWA\{V\}$
$XT=R$
$XV=V$
$XWA=V$
# Exercice 3 : Les quatre dames
## Question 1 : backtracking 
