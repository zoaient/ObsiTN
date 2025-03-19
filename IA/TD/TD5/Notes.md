BWAAAAAAH JSUIS EN PUR BWAAAAAH BWAAAAH JE VEUX ETRE DANS SES BRAS 
# Exercice 1 : Construction d'un arbre de décision
- 4 Attributs, Outlook, Temperature, Humidity, Windy
## Question 1 :
1) Critère d'arrêt : $i_0=0,33$
Noeud 1 : D1 = Dtrain
Indice de Gini : i(D1,play)=$1-\sum_{j=1}^2P1(play=C_j)^2=0,41>0,33$ Donc D1 n'est pas un terminal
2) Choix du test
a)
Outlook : 1 test n-raire
Outlook -> overcast,rainy,sunny
b)
Temperature : 1 test n-aire
Temperature : -> hot,cool, mild
c)
Humidity : 2 test binaires
c1) Humidity : < 75,5 -> vrai, faux
c2) Humidity: < 82.5 -> vrai ,faux
d)
Windy : 1 test binaire
Windy -> true false

### Calcul des gains : 
#### Outlook

$gain(D1,OutLook)=i(D1,play)-\sum_{V=1}^3P1(outlook=V)*i(D1,P)$
v={O,S,V}
##### Outlook = overcast(0)
P1(Outlook=0)=$4/14$  i(D1o,play)=0
gain=0,12

#### Temperature 
$gain(D1,)$
##### Temperature = hot
P1(Temperature=hot)=4/14
i(D1h,play)=0,5
##### Temperature = mild
P1(Temperature =mild)=6/14
i(D1m,play))=5/18
##### Temperature = cool
P1(temp=cool)=4/14
i(D1c,play)=3/8
##### Gain
gain(D1,temp)=0,041
#### Humidity
gain(D1,Humidity<82,5)=0,04
#### Windy
gain = 0,013

### Jsp
- max(gain,A)=0,12 -> on choisit le test n-aire Outlook

![[oui]]
#### Test Critère d'arret
##### Noeud3 :
i(D3,play)=0,32 < i_0
Noeud terminal i Classe dominante P(4/5)
##### Noeud4 : 
i(D4,play)=0,48 > i0
D4 n'est pas terminal
#### Choix du test
Temperature -> hot,cool,mild
Humidity