# La donnée

**Qu'est ce qu'une donnée ?**
La donnée regroupe un nombre important de concept. Pour définir ce qu'est une donnée on peut se fier au schéma ci dessous.
![[Schéma de la donnée.PNG]]
#### Les propriété de la donnée

>[!Les propriétés d'exposition de la donnée]
>Ce sont les propriétés qui permettent d'afficher ou de présenter ta donnée
 >- Le format : date (américain..),les nombres(virgule ou point..),monétaire,expression régulière( Code semi structuré code IBAN,Numéro secu...)
 >- La localisation et internationalisation (impact la valeur de la donnée)

>[!Les propriétés structurelles de la donnée]
>Ce sont les propriétés structurelles qui définissent l’organisation de cette donnée ou l’organisation dans laquelle elle se trouve. Tel que : 
>- La granularité (dans quel niveau d'information nous sommes agrégé ou non(atomique)
>- La structure de la donnée :
>	- Structurés (tableau en 2 dimension, universelle au traitement de base de donnée)
>	- non structurées (image, texte,vidéos) il est difficile de l'analyser avec les méthodes traditionnelle et pourtant il représente 80% du flux de donnée des entreprises.On appelle cela le Dark Data. Ils nécessitent des IA pour l'analyse de texte
>	- semi structuré(XML(\*1), JSON(\*2) sont des structures qui permettre de qualifier la donnée. Ils vont avoir une structure propre et [constante.Il](http://constante.Il) permettent de stocker des arborescences, nomenclature par exemple)
>- Les mesures et la dispersion
> 	- Les mesures correspond à l'analyse des données (moy,medianne, quartil,etendu,écart type,mode,fréquence, interclasse)
> - La dispersion correspond aux lois de distributions



>[!Les propriétés fonctionnelles de la donnée]
 > Les propriétés fonctionnelles qui décrivent son sens et sa valeur métier.
 > - Contexte : Dans quel contexte la donnée est utilisé
> - La sensibilité de la l'information CID : Confidentialité/Intégrité/Disponibilité


>[!Les propriétés physiques de la donnée]
 >Les propriétés qui permettent de décrire son support physique
 > - type de donnée --> Octet, image {matrice pixel 2 ou 3 dimensions},la vidéo {succession d'image),nombre decimale, date, texte {UTF,ISO8859)
> - Le domaine --> la catégorie du type de donnée , par exemple la température est un domaine qui regroupe un nombre décimal de nature liée à la température
> - La variabilité --> Permet de donnée une perspective de la donnée tel que les dates calendaires, les groupes d'individu ect ect On met donc en perspective les données avec des variables quantitative (kg par rapport kg normal par exemple) ou catégoriel (niveau 1 2 3 , homme /femme )
 
*Exemple de typologie de donnée physique :* 
![[La_donnée1.png]]![[La_donnée2.png]]

#### Typologie de donnée semi-structuré

**CSV**

Lire un fichier CSV avec Pandas avec Python :
![[La_donnée3.png]]
**XML(\*1) :**

Le XML (Extensible markup langage ) est né dans les années 1990 et propose en effet de décrire des données via des balises qui sont nommées entre des chevrons (< et >). Le principe est plutôt simple : chaque balise englobant des données doit être terminée par son alter ego fermant (avec un slash /) . Il est ainsi possible d’encapsuler à l’infini des balises entre elles, et il est aussi possible de créer des attributs pour chaque balise (cf. ci-dessous, la balise possède l’attribut nom qui a pour valeur "ma famille").
![[La_donnée4.png]]

On appelle chaque balise un nœud, chaque nœud pouvant posséder d’autres nœuds et des attributs, ce qui amène à d’infinies possibilités de stockage de l’information. La structure des fichiers pouvant être totalement différente d’un fichier à un autre, il est particulièrement important de pouvoir décrire sa grammaire. C’était le rôle original des fichiers ( DTD Document type definition) mais depuis 2001 (W3C) on utilise plutôt son successeur le XML Schema (extension XSD ). Ces fichiers décrivent la structure de l’arbre de stockage.
Pour naviguer dans ces arborescence ont utilise des outils que l'on appelle PARSER . Il existe deux façons :

* **Le (DOM document object model )** : quand un programme ou une API utilise cette méthode statique, elle lit intégralement le fichier XML pour le mettre en mémoire. La navigation ensuite est rapide mais l’efficacité de cette méthode est malheureusement inversement proportionnelle à la taille du fichier XML. Ce qui peut poser d’énormes problèmes lors de la lecture de très gros fichiers.
* **Le (SAX Simple API for XML )** : au lieu de charger en mémoire tout le document XML, SAX permet après son initialisation de capturer des événements, c’est donc une méthode dynamique. Par exemple, quand le programme a besoin d’ouvrir et fermer une balise pour récupérer une donnée bien précise.

**JSON(2) :**
Le format JSON (Java script object Notation ) est un format de stockage et d’échange qui a le vent en poupe depuis quelques années. Il doit certainement son succès grandissant à son intégration native dans JavaScript, évitant ainsi l’utilisation de parser externe. Mais il est aussi très intéressant car il permet, comme XML, de stocker des données hiérarchiques tout en limitant de manière drastique le poids du fichier grâce à un mode de balisage allégé.
![[La_donnée5.png]]
Le format JSON est de plus en plus utilisé car il est très vraiment très simple et léger comme on vient de le voir, mais aussi parce qu’il s’intègre de manière native à JavaScript.
