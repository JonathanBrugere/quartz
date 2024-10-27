
### **Introduction**

La gouvernance de la donnée est un ensemble d'élément permettant de réguler la donnée dans le contexte qui lui est associé. Ce sont ces éléments qui définissent les lois que l'on impose afin d'organiser la donnée dans son écosystème.
Il existe 6 éléments :
![[La_donnée39.png]]
La gouvernance de donnée se réalise avec des équipes et des processus ainsi que des outils :
De ce que je comprend de la gouvernance de la donnée est que c'est une démarche qui vise à exploiter la valeur de la donnée au profit de l'entreprise. Pour cela plusieurs éléments composent cette démarche :
- **L'organisation :** Identifier  les différents rôles de la gouvernance de la donnée avec ces acteurs ainsi qu'identifier les domaines métiers de l'entreprise de la donnée. S'approprier les 6 piliers en image ci dessus .
- **Processus :** Définir les processus de la donnée, les flux de données, qui fait quoi , comment, ou , avec quoi, valide quoi ect..., Quel est le périmètre de notre donnée, identifier la données et ses sources ... (lignage, glossaire, métadonnée) --> Cartographie des données et des processus.
- **Moyen et mise en place technique :** Définir les outils techniques nécessaires pour la mise place de processus et déployer les solutions en fonction des processus à traiter et de l'organisation défini.

Il existe différents type d'outil :
- Les outils de gestion des métadonnées.
- Les outils de gestion de glossaire métier.
- Les outils de supervision.
- Les outils de lignage.
- Les outils de sécurité de données.

### L'équipe de la gouvernance de la donnée
Voici les différents rôles existant :

**Chief Data Officer** : il porte la stratégie de la donnée dans l'entreprise et il doit pouvoir garantir que les données sont défini, de confiance et utilisable à tout moment par les utilisateurs.
**Le Data Steward** : C'est un poste entre la technique et le fonctionnel. Il doit gérer et garantir l'intégrité de la donnée. Il doit donc s'assurer de la collecte , de la mise à disposition en passant par la documentation. Ce qui découle d'être garant de la qualité de l'information fournies. Une connaissance en architecture et outils technique utilisés.
**Le Data Owner** :  Il est garant de son périmètre de donnée. Cela peut être par métier. Il auront comme responsabilité l'état, la définition et la gestion de la donnée de son périmètre.
**Le Data Protection Officer :** Ce rôle a pour mission de garantir que les données collectées et échangées sont conformes à la législation et conforme aux lois (par exemple la GDPR).
**Le Data Architects :** ce rôle est aussi un rôle capital car outre le fait qu’il doive s’assurer de la cohérence globale des infrastructures data, il doit aussi s’assurer que les données circulent et sont échangées de manière fluide selon les besoins des utilisateurs.
**L'analyste de donnée/Le Data Analyst  :** Il est chargé d'analyser et de restituer (analytics) les données, collaborer avec les metiers afin de leur fournir les données nécessaires et d'en tirer des conclusions. Mise en place d'indicateur métier.
**Le Data Scientist :** Il analyse par modélisation les données près à l'emploi et tire des tendances et des prévisions
**Le Data Engineer :** Il est chargé de collecter, transformer et mettre en qualité (technique) les données. En général, il travaille conjointement avec le Data Scientist pour préparer les données à son intention

Il existe beaucoup de schéma sur les acteurs de la data et la gouvernance en général, en voici quelques exemples :
![[La_donnée40.png|400]]![[La_donnée41.png|400]]![[La_donnée43.png|400]]![[La_donnée42.png|400]]

### LES METADONNEES
Une métadonnée est une façon de d'écrire une information. C'est comme une étiquette permettant de qualifier sans ambiguïté l'information véhiculé. La métadonnée est à la donnée ce que l’étiquette est au produit.
La métadonnées est une double approche, à la fois technique comme fonctionnelle. Elle l'aborde sous le prisme technique (stockage , base de donnée, nom de table... mais également métier (le sens fonctionnelle de la donnée(facture, article...). L'intérêt de ce type de démarche  est de réconcilier ces deux visions complémentaire de la même donnée. La gestion de métadonnées via **le DATA CATALOG** est la solution à ceci.

La catalogue de donnée va donc faire converger la maitrise d'ouvrage (MOA) et la maitrise d'œuvre(MOE)
![[La_donnée44.png|500]]

Ces deux acteurs vont construire ensemble le Catalogue de donnée avec :

- le MOE  les Métadonnées techniques --> Définir la provenance de la donnée, usage ,temporalité, granularité, type, domaine...
- le MOA les Métadonnées métiers -->Définir un glossaire métier. C'est dictionnaire global de l'entreprise recueillant l'ensemble des métadonnées décrite d'un point vue fonctionnelle.

>[!Astuce]
Pour débuter un glossaire métier , on doit organiser les termes métiers. On parle alors de Taxonomie.
La taxonomie est une classification des données en catégories et sous-catégories. Elles sont ainsi ordonnées en structure hiérarchique puis compartimentées et enfin divisées en différents attributs.

Voici un exemple pas très sexy :
![[La_donnée45.png|500]]
Ou plus sexy pour la compréhension :
![[La_donnée46.png|500]]

La taxonomies/termes métier peuvent :

* être structurés sous forme de hiérarchies (une ou plusieurs hiérarchies selon les solutions/besoins) ou de liste. Dans ce cas, on parle plutôt de catégories ;
* avoir (éventuellement) une période de validité ;
* avoir des alias, synonymes ;
* proposer des exemples ;
* proposer des liens références ("voir aussi", "contient", "enfant", "parent", "ressources liées", etc.). Les liens peuvent être différents de la hiérarchie, néanmoins, dans certains cas ces deux notions peuvent se confondre ;
* être lié à des règles métier ;
* avoir une classification sécurisée ;
* être liés à d’autres facettes (catégories d’objets) comme les data set, attributs, systèmes, processus, projets, etc. pour décrire l’utilisation, l’importance, la dépendance ou le contexte. 
* avoir des acteurs avec des rôles et responsabilités clairement définis (Data owner , créateur, etc.). On touche ici un point essentiel de la gouvernance : la notion de responsabilité. Chaque donnée devient certifiée par des Data Owners ; ˇ être pilotés par un processus de validation et/ou d’enrichissement.
>[!Conclusion]
En gros, elle donne un langage commun et assure des niveaux de regroupement ou de détails partagés par tous les utilisateurs. La définition d’une taxonomie commune lève toute erreur de compréhension ou d’interprétation de la part des utilisateurs de la donnée.

>[!Exemple]
En taxonomie il existe une méthode pour faciliter la gestion du glossaire métier. 
En effet un indicateur est unique, par exemple le calcule du montant de la TVA. 
En revanche il existe différentes façon de calculer la TVA. Dans notre cas c'est en fonction du type de produit commandé. Nous allons donc pas créer autant de définition de TVA que de type de produit commandé. 
Pour éviter d'engorger les glossaires nous allons créer un modèle (policy) puis des termes. La policy = Montant de TVA et le terme (déclinaison) = Produit agricole. Dans cette combinaison policy/Terme la TVA ce calcule sur une base de 10%. On peut appliquer cela pour le calcule d'un indicateur comme l'efficience (suivant système ERP le calcul de l'efficience est le même sauf que la façon de le calculé est différent.
![[La_donnée47.png]]
