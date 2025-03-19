# 1 : Le problème du parking
## Q1 : Etats
- Il y a 2n+1 états, un état devant la ligne et un état garé dans la ligne, dans chaque état de devant de ligne on peut faire deux actions, chercher ou ne pas chercher, donc deux transitions possibles vers l'état devant suivant (Prendre en compte l'état parking ext d'ou le +1)
## Q2 : Graphe
![[ex1TD4]]
> Pour transformer le problème en problème a horizon infini, on rajoute des états qui bouclent au lieu des états terminaux

### Actions possibles
Ari={ar,ag}
- ar : avancer
- ag : tenter de se garer
Agi={ag}
- ag : rester garé
### Probabilités de transition 
Tu as capté

$\gamma =1, n=5$
### Couts des actions : 
- Reussir a se garer dans la rangée i : C(ri,ag,gi)=i/2=temps de marche
- Echouer a se garer dans la rangée i 
	- C(ri,ag,ri-1)=0
	- C(r1,ag,g0)=5
- Tenter de se garer dans la rangée i
	- C(ri,ag)=0,15i
	- Pour i =1 C(r1,ag)=3,65
- Avancer vers la rangée suivante
	- C(ri,ar)=C(ri,ar,ri-1)=0
	- C(r1,ar)=C(r1,ar,g0)=5
C represente l'esperance du cout pour une action spécifique
## Question 3 : algo d'itération sur les valeurs
Rappel : a chaque itération, maj des valeurs
$$V_{t+1}(s)=min_{a\in As}\{c(s,a)+\gamma*\sum_{s'\in S}P(s'|s,a)*V_t(s')\}$$
- Initialisation arbitraire des valeurs (t=0) $$\forall s \in S, V_0(s)=0$$
- Itération t=1
	$$\forall i \in [0,n], V_1(gi)=c(g_i,a_g)+\gamma P(g_i|g_i,ag)*V_0(g_i)=0$$
	$$\forall i \in [2,n],V_1(ri)=0 \text{ après simplifications}$$
	de même
	$$V_1(r_1)=3,65,V_2(r_2)=2,855,V_3(r_3)$$
	