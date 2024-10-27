
Une base de données permet de stocker et organiser un ensemble de données ou informations dans un même endroit (pas nécessairement physique).
### Introduction
#### Famille de base de donnée

- Les bases de données (SGBD-R )
- Les bases de données dépend d'une structure en arborescence  (contrainte 1 parent par noeud enfant)
- Les bases de données graphe (ou réseaux) élimine la contrainte d'une seul parent. Plusieurs enfants peut avoir plusieurs parents. Chaque Noeud peut être connecté. On utilise souvent dans dans la modélisation objet.
	![[La_donnée6.png]]

#### Les bases de donnée SGBD-R

1. **Modélisation**

![[La_donnée7.png]]![[La_donnée8.png]]![[La_donnée9.png]]![[La_donnée10.png]]

2. **L'Intégrité de la base de donnée**

La notion de contrainte d’intégrité référentielle (CIT ) est un système de protection de la base de donnée.
Il permet d'éviter la violation des bases de donnée et des schémas relationnels. Il empêche la suppression de donnée si celle ci n'est pas atomique. Si elle est composite il faudra donc supprimer la donnée de granularité inférieur. Le système CIT peux soit supprimer automatique toutes les données liées ou empêcher la suppression avec un message d'erreur en indiquant qu'il faut supprimer les données de granularité inférieur.

3. **L'indexation des tables**

Sans indexation le système de requêtage réalise la recherche de donnée de la façon suivante :
Si la donnée est à la 10000 position alors va itérer 10000 fois. Quand les tables ont des grands volume de donnée le traitement peut être gourmant en ressource et en temps.
![[La_donnée12.png]]
Parcours séquentiel sans index de la table (fullscan):  Dans ce cas de figure, la base de données devra lire exactement cinq enregistrements (lignes) pour pouvoir renvoyer la réponse (ici 51 300 km). Dans l’hypothèse où le concepteur de la base de données a créé un index sur le nom de planète, la base de données, au lieu de parcourir les enregistrements de la table, va naviguer dans la table d’index via une recherche dichotomique. Dans notre exemple précédent, on a trois étapes : 1. Création de l’index (table ou vecteur). La colonne Nom de planète est triée et l’on récupère ses identifiants pour pouvoir accéder à l’information dans la table contenant les données ultérieurement. 2. Par dichotomie, on coupe en deux parties égales la table d’index, et l’on regarde la valeur médiane (ici Neptune). Ce n’est pas le nom de planète recherché (Uranus), et plus intéressant, Uranus commençant par un U doit se trouver après Neptune (commençant par un N). On peut donc ignorer le premier bloc d’index (avant Neptune). 3. On recoupe en deux le bloc d’index restant (et ainsi de suite), jusqu’à trouver la donnée recherchée. Cela tombe bien, on trouve ici Uranus. Via la clé (ID=5) on peut maintenant trouver directement le bon enregistrement dans la table de données
![[La_donnée11.png]]
Il est important de placer les index sur des données qui n'ont pas une grosse fréquence de création et [suppression.La](http://suppression.La) structure d'index la plus courante  est la structure B-TREE.

4. **Le langage SQL pour le requêtage de base de données relationnelles**

Le langage SQL veut dire Structured Query Language (IBM 1 er version 1970).C'est une langue normalisé afin de d'agir sur une base de donnée relationnel (SGBD-R).

Le langage SQL comporte trois grandes typologies d’instructions :

* Le LMD (Langage de Manipulation de Données) qui permet d’interroger les données. Ce langage permet d’agir directement sur les données stockées.
* Le LDD ou DDL(Langage de Définition des Données) qui sert à contrôler les données et permet de créer/modifier/supprimer les structures physiques de la base de données comme les index/tables, etc
* Le LCD (Langage de Contrôle de Données) pour gérer notamment les utilisateurs/groupes et droits

**LMD :**
![[La_donnée13.png]]![[La_donnée14.png]]
Il existe le :
* Distinct (enlever les doublons)
* Les UNIONS de table
* les jointures de tables

![[La_donnée15.png]]
**Le LDD ou DDL**
![[La_donnée16.png]]![[La_donnée17.png]]![[La_donnée18.png]]

5. **La notions de transactions**

Lorsque l'on souhaite exécuter un script avec une requête de type LDD, on réalise une transaction avec la table . Lorsque que la transaction est validé alors la donnée est validé avec "COMMIT" . En revanche si par exemple on veut retourner en arrière on peux utilise "ROLLBACK". Par exemple on souhaite mettre à jour 100 lignes de la table. On veut que la procédure SQL balaye les 100 lignes puis met à jour la table sur les 100 lignes ou rien. Dans la procédure on peut utiliser un ROLLBACK dans le cas ou l'une des 100 lignes est en erreur.
Pour gérer également des conflits entre transaction de lecture et écriture dans la table il y a :

* Modes d'accès :
	* Read Only : Transaction de type lecture seule
	* Read Write : Transaction de type lecture/écriture
* Le niveau d'isolation
	* Read UNCOMMITED : c’est le niveau d’isolement le plus faible (voire quasi-inexistant). Une transaction peut en effet récupérer des modifications non encore validées ("commitées"). Cela autorisant ainsi des lectures incorrectes (au sens non validées).
	* Read COMMITED : : lorsqu’une transaction s’exécute avec ce niveau d’isolement, les données récupérées sont celles qui ont été validées avant le début de la requête (SELECT). On ne voit ainsi jamais les données non validées (commit) ou les modifications qui ont été validées pendant l’exécution de la requête par d’autres transactions simultanées.
	* REPEATABLE READ : ce niveau permet de garantir que les lectures effectuées par un SELECT ne seront pas modifiées, sauf si ce SELECT contient une clause WHERE permettant de sélectionner une plage de données.
	* SERIALIZABLE : il s’agit du niveau le plus strict et le plus sûr. Il garantit une indépendance parfaite entre toutes les transactions.

On peut réaliser un diagnostique :
![[La_donnée19.png]]
**Critère A.C.I.D d'une transaction**
![[La_donnée20.png]]
#### Les bases de donnée NoSQL (Not only SQL)

##### Introduction

Les bases de donnée NoSQL permettent de prendre en charge les données non structurés ou semi structuré. On interroge les données n'ont plus pas le langage normé SQL  mais par d'autres typologies de langage.
Comme **la plupart des bases de données distribuées**, NoSQL offre la possibilité de stocker les données sur différents serveurs en local ou en Cloud. Il s'agit d'un des principaux points forts de NoSQL. Le Cloud aide en effet à mettre à disposition des utilisateurs une plus grande quantité de serveurs, ceci à un prix relativement faible.
Idéales pour le stockage et l'analyse du Big Data, les bases de données NoSQL permettent aussi d'éviter un point de défaillance unique. Elles facilitent ainsi la réplication des données sur plusieurs serveurs. Cela offre la possibilité de diminuer la latence et la charge de travail des data centers pour les utilisateurs. Cette « disponibilité » de la donnée garantit au NoSQL toute sa performance et la possibilité d'une scalabilité horizontale.
De plus, les bases de données NoSQL sont capables de **prendre en charge les données non structurées et les données structurées** de la même façon. Cette capacité de NoSQL à s'adapter à tous les types de data lui confère sa grande flexibilité. Pour utiliser les données, le Data Scientist n'a plus besoin de les structurer, de les ranger puis de les extraire. Elles sont directement exploitables, ce qui aide à développer de façon agile et rapide des logiciels ou des applications web.

**Voici le comparatif avec une BDD relationnelle :**
![[La_donnée21.png]]
Si l’on y pose un œil pragmatique sur ces deux typologies de bases de données, la plus grande différence se situe surtout autour de la modélisation, ou plutôt de l’existence ou non de cette modélisation. L’absence de modélisation dans les bases NoSQL va, en effet, permettre de stocker tout type de données de manière beaucoup plus simple et efficace mais va affaiblir la gestion de la cohérence des données.

**Il existe plusieurs implémentation NoSQL :**

* Apache Cassandra (Colonne)
* MongoDB (Document)
* AWS Dynamo, Azure Cosmos DB (Clé-valeur) ,
* Apache HBase (Colonne) ˇ Neo4J (Graphe)

Les familles de bases NoSQL sont :
![[La_donnée22.png]]

##### Clé-Valeur :
Les **bases de données clé/valeur** ont pour principale caractéristique de stocker les données sous forme de paires clé/valeur. La clé représente ici une information numérique ou écrite sur la donnée tandis que la valeur représente la donnée elle-même. En d'autres termes, on labellise la valeur, c'est-à-dire la donnée, avec une clé.
Cela permet de prendre en charge de grands volumes de données en Cloud dans différents serveurs ainsi que des charges lourdes. Le stockage des données de forme couple clé/valeur rend également l'utilisation de la base de données plus rapide et plus flexible pour les développeurs.

![[La_donnée26.png]]

##### Colonne
Les bases de données orientées colonnes reposent essentiellement sur des colonnes. Elles sont basées sur le modèle BigTable de Google. En effet, les colonnes sont dynamiques en NoSQL et chaque ligne peut avoir un nombre différent de colonnes sans toutefois faire apparaitre la valeur NULL.
La **famille de colonne** (toutes les colonnes d'une table) est stockée dans le même fichier, avec un nombre fixe de lignes. À chaque fois que l'on veut appeler une ligne à une table, il n'est donc pas nécessaire de télécharger l'intégralité de la table. Il suffit de faire une requête sur une ligne et elle sera automatiquement extraite dans le Cloud.

![[La_donnée27.png]]![[La_donnée29.png]]![[La_donnée28.png]]

##### Document :
![[La_donnée23.png]]![[La_donnée24.png]]![[La_donnée25.png]]
##### Graphe :
Ces bases ont pour objectif de stocker les données en se basant sur la théorie des graphes. Elles s’appuient sur les notions de :

* noeuds qui ont chacun leur propre structure
* relations entre les noeuds
* propriétés (de noeuds ou de relations)

Ce modèle de stockage facilite la représentation du monde réel, ce qui le rend particulièrement bien adapté au traitement des données des réseaux sociaux et géographiques par exemple, et de toutes les données fortement connectées de manière générale.

![[La_donnée30.png]]![[La_donnée31.png]]![[La_donnée32.png]]
<https://www.illustradata.com/cat/recuperation-et-stockage/technologie-de-stockage/>
