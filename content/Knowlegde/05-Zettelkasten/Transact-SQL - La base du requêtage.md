---
tags:
  - "#SQL"
  - langageprogramation
---
# SQL Serveur

**Création d'une requête mono table**
**==Select==** \* pour toute la table ou nom de la colonne
**==From==** table de recherche
**==Where==** condition attribut colonne = ' ' , >,<,=!
**==and==** condition
\*\*
**Création d'une jointure**
Le but est de créer un lien entre une table 1 et une table 2 voir 3, 4...
**==Select==** \* pour toutes les colonnes ou Nomdelatable.Nomattribut,  Nomdelatable.Nomattribut,  Nomdelatable.Nomattribut
**==From==** Tablederecherche1 **==as==** TDR1, Tablederecherche2 **==as==** TDR2
**==Where==** (mettre l'élément de la jointure entre les tables) TDR1.id = TDR2.id
**==and==** autres conditions

**La négation**
Je veux rechercher l'ensemble des logements qu'il ne propose pas du ski comme activité.
Si on utilise comme condition Activité <> 'Ski" alors on nous affichera des logements proposant du ski car un logement peut avoir plusieurs Nuplets dont 1 proposant du ski mais pas les autres. Il y a donc une notion d'ensemble. On cherche donc 'il ne doit pas avoir d'activité ski parmi le logement.
On utilise la formulation suivante :

**==Select==** \* ou attribut
**==From==** Logement
**==Where not exists==** ( ==select '' From== Activité
**==Where==** code = codelogement                       --> (lien de jointure)
**and** Activité = 'ski')
ou
**==Where code not in==** (==select== codelogement  ==From== Activité
**==Where==** Activité = 'Ski')

**Les agrégats**
On utilise les agrégats (groupage de nuplets en fonction d'un attribut) pour faire des calculs sur une sélection.
Voici la liste des agrégats :

* [AVG()](https://sql.sh/fonctions/agregation/avg) pour calculer la moyenne sur un ensemble d’enregistrement
* [COUNT()](https://sql.sh/fonctions/agregation/count) pour compter le nombre d’enregistrement sur une table ou une colonne distincte
* [MAX()](https://sql.sh/fonctions/agregation/max) pour récupérer la valeur maximum d’une colonne sur un ensemble de ligne. Cela s’applique à la fois pour des données numériques ou alphanumérique
* [MIN()](https://sql.sh/fonctions/agregation/min) pour récupérer la valeur minimum de la même manière que MAX()
* [SUM()](https://sql.sh/fonctions/agregation/sum) pour calculer la somme sur un ensemble d’enregistrement

Si on on utilise un agrégats il faut utiliser un groupage. Il s'écrit : Group By
Ex :
```
SELECT client, SUM(tarif)
FROM achat
GROUP BY client
```
Voici le résultat :

|     |     |
| --- | --- |
| client | SUM(tarif) |
| Pierre | 262 |
| Simon | 47  |
| Marie | 38  |

On peut rajouter à la fin Having agregat  et une comparaison ex: Having count(\*) > 2. Cela met une condition non pas sur les nuplets mais sur le groupement réalisée de nuplets.

**Les vues :**
Nous pouvons créer des vues pour faciliter l'écriture des requetes, avec la fonction Create view nomdelavue puis requête classique.
exemple :
CREATE VIEW _view\_name_ AS
		SELECT _column1_, _column2_, ...
		FROM _table\_name_
		WHERE _condition_;
		

Select \* ou attribut
From View\_name
where ...

**Si la jointure classique ne prend pas les valeur NUL**
Utiliser left ou right outer join
exemple :
```
SELECT *
FROM Logemennt LEFT OUTER JOIN Activité
  ON (Logement.id = Activité.id)
```
On renverra les valeurs 'null' si existante et donc on les prends quand même en compte.

**LA FONCTION CASE**
```
SELECT id, nom, marge_pourcentage, prix_unitaire, quantite,
    CASE
      WHEN marge_pourcentage=1 THEN 'Prix ordinaire'
      WHEN marge_pourcentage>1 THEN 'Prix supérieur à la normale'
      ELSE 'Prix inférieur à la normale'
    END
FROM `achat`
```
la commande “CASE … WHEN …” permet d’utiliser des conditions de type “si / sinon” (cf. if / else)

**Order BY**
Permet de trier les attribut choisi colonne par colonne et descendant ou ascendant pour les valeurs
```
SELECT colonne1, colonne2, colonne3
FROM table
ORDER BY colonne1 DESC, colonne2 ASC
```

ISNULL(Champs, valeur de replacement) ex isnull(qté,0) ou Coalesce(qté,0)
