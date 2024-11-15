# 1 : Diagrammes de sequence
## A : Création d'une offre d'emploi

![[Diagramme de sequence 1.png]]
> - L'utilisateur arrive sur le **contrôleur** "Contrôleur"
> - Une offre d'emploi est créée par le **créateur** "Créateur d'offre d'emploi" , est intégrée dans la base de données par **l'expert** "Offre d'emploi"
> - Enfin, une notification est créée par l'interface de notification.
## B : Validation d'une offre d'emploi
![[Diagramme de sequence 2.png]]
>  - L'utilisateur arrive sur le **contrôleur** "Contrôleur" 
>  - Il accede à la base de données pour récupérer l'offre d'emploi
>  - Si cette offre d'emploi est refusée, elle est supprimée et une notification est créée par l'interface de notification
>  - Si elle est acceptée, elle est publiée sur le site de l'entreprise et une notification est créée par l'interface de notification
## C : Ajout d'une candidature
![[Diagramme de sequence 3.png]]
> - L'utilisateur arrive sur le **contrôleur** "Contrôleur" 
> - Il consulte les offres d'emploi depuis la base de données
> - Il peut ensuite déposer une candidature , celle ci est crée en accédant au **créateur** "Créateur de candidature" , elle est intégrée dans la base de données par **l'expert** "candidature"
> - Ensuite, une notification est créée par l'interface de notification
# 2 : Diagramme d'état : cycle de vie d'une offre d'emploi
![[Diagramme d'état.png]]
>- La logique établie dans les diagrammes de sequences successifs est reprise. Il y a deux états finaux :
> 	- L'offre d'emploi est acceptée et est ajoutée sur le site de l'entreprise, elle est consultable librement
> 	- L'offre d'emploi est refusée et est supprimée
# 3 : Diagramme de classe 
![[Diagramme de classe|2000]]
> - Les méthodes et objets présentés dans les diagrammes precedents sont repris, tout est lié au contrôleur qui appelle chaque méthode sauf pour les objets "candidature" , "offre d'emploi" et "notification" , crées par leur créateur respectif
# 4 : Diagramme de classe du cahier des charges
![[diagramme.png]]