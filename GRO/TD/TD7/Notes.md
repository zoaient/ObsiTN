# Exercice 5 Feuille 4
![[Pasted image 20241108102510.png]]
## 1 ) flot réalisable
- $\alpha_{i,j}\le f_{i,j} \le\beta{i,j}$
$$f^{'}{i,j}\implies 0\le f^{'}{i,j} \le \beta{i,j}- \alpha_{i,j} =c^{'}_{i,j}$$
![[Graphe auxilliaire G']]
> Ce graphe auxilliaire est une transformation de G pour éviter de gerer les capacités minimales de chaque arrête
$f_{i,j}$ est un flot réalisable pour G donc $f^{'}_{i,j}$ est un flot maximal pour G' tel que :
- Toutes les arrêtes partant de S' sont saturées $\forall j \neq t',f'_{S'j}=c'_{S"j}$
- Tout les arrêtes arrivant en t' sont saturées : $f'_{i,t'}=c'{it'},\forall i\neq S'$
## Flot max sur G' avec parcours largeur (file)
- Si les arrêtes rajoutées ne sont pas saturées alors il n'y a pas de flot réalisable

| E             | S'       | t   | a   | b   | t'              |
| :------------ | :------- | :-- | :-- | :-- | :-------------- |
| Origine       | -        | S'  | t   | t   | b               |
| $\varepsilon$ | $\infty$ | 2   | 2   | 2   | $\varepsilon$=2 |
# Exercice 4 
- Image bruitée $\alpha : [|1,n|]\rightarrow \{+1,-1\}$ (données)
- image débruitée $\sigma : [|1,n|] \rightarrow \{+1,-1\}$ (inconnues)
$$J(\sigma)=-\sum_{i=1}^n \alpha _i \sigma_i - \sum_{1\le i,j \le n}\gamma_{i,j}\sigma_i \sigma_j$$
-> Correction sur arche

# Feuille 5 exercice 1
$$max_{x\in \mathbb{R}}(F(x)=c^Tx), \begin{cases}Ax=b, \text{ b entier}\\
x\ge 0\end{cases}$$
