# **A. HADOOP en résumé**
### **Qu’est-ce que c’est ? et à quoi ça sert ?**

Hadoop c’est une technologie permettant de stocker et de manipuler de grandes volumétries de données structurées ou non.

Hadoop est un framework logiciel Open Source (l’intégration dans l’Apache Software Foundation s’est faite en 2008). Ce framework complet et autonome développé en Java permet de stocker et gérer des données. Mais Hadoop ne s’arrête pas là. Il permet aussi de lancer des traitements sur des clusters de machines. En cela, on peut voir Hadoop comme un système d’exploitation de données. Les enjeux d’Hadoop sont donc de pouvoir gérer de très forts volumes de données de manière distribuée tout en permettant de gérer des pannes de serveurs, des pertes données (sur disque dur) mais aussi et surtout de pouvoir distribuer intelligemment les traitements et données de manière dynamique sur d’autres serveurs.
##### **D’où ça vient et pourquoi cela fait le Buzz ?**
Hadoop provient de l’adaptation, par Doug Cutting et Michael J Caffarella, de thèses de Google sur le stockage et les calculs parallèles dans le cadre d’un projet de recherche pour Yahoo.Ces derniers ont créé Hadoop, une technologie Open Source et donc “gratuite”, alors que jusque là les technologies permettant d’analyser de grosses volumétries de données étaient très coûteuses.
##### **Techniquement, ça marche comment ?**
Techniquement c’est un système distribué, c’est-à-dire qui fonctionne sur plusieurs ordinateurs (un cluster) et qui est donc différent des bases de données “classiques” ne fonctionnant que sur un seul serveur.

Ce système est composé de trois  modules principaux :
- **HDFS** (Hadoop Distributed File System) qui est un système de fichiers (comme “mes documents”) distribué (les données sont découpées puis stockées sur plusieurs ordinateurs) qui permet de stocker les données sous leur format natif (png, word,txt, etc.). En gros : Un espace de stockage massif pour tous les types de données.
    
- **Map Reduce**, qui est un paradigme (modèle de programmation) se basant sur le principe du “diviser pour mieux régner” et permettant d’analyser les données stockées dans HDFS en utilisant le plus de serveurs en même temps. A cela s’ajoute tout un écosystème d’applications permettant de rajouter des fonctionnalités dans Hadoop (temps réel, alimentation, structuration des données, etc.) (En gros : Une immense puissance de calcul et de traitement)
- **YARN** afin de gérer les ressources du cluster Hadoop
#### **Quels sont les composant essentiels de HADOOP ?**

**Pour le stockage et la gestion de données** : Hive, Apache HBase, Cassandra, Sqoop, MongoDB, etc.
**Pour la programmation :** Apache Spark, Pig.
**Pour la gestion des données en mode flux (streaming) :** Apache Kafka, Apache Storm, Flume, Flink, Spark Streaming.
**Pour la gestion du cluster Hadoop :** Apache ZooKeeper, Tez, Apache Zeppelin, Oozie, Mesos
###### **Les principaux avantages ?**

- Tout l’écosystème Hadoop est Open Source et donc gratuit
- Hadoop est un système dit « scalable », s’il on a besoin de plus d’espace on peut soit améliorer les serveurs existants soit ajouter de nouveaux serveurs
- Il présente de bonnes performances pour les traitements de “gros” volumes de données
- Couplé à des applications comme Spark, il permet le temps réel
- Hadoop s’installe sur tous les types de serveurs, pas besoin de serveurs haut de gamme
- Abondance de la documentation sur Internet concernant le cœur d’Hadoop
- Possibilité de retrouver la notion de relationnel et le SQL pour les données structurées (avec des applications comme Hive)
- Possibilité d’intégrer une base NoSQL orientée colonnes
- Hadoop et son écosystème permet de répondre aux trois Vs (volume, vélocité, variété)

###### **Les inconvénients d’Hadoop ?**

- Solution Open Source/solution « jeune », avec une interface très épurée par défaut et pas forcément très « user friendly »
- Documentations principalement en anglais
- De nombreuses applications créées autour de Hadoop régulièrement dont bon nombre sont amenées à disparaître
- Documentation faible pour certaines applications gravitant autour de Hadoop
- Hadoop ne porte pas encore les contraintes ACID qui font la force des SGBDR
- Il est moins efficace que les systèmes classiques pour les faibles volumétries de données
- Compétences rares et donc chères
### B. Modules HADOOP en détails

**HDFS :**
Le service de stockage **HDFS** n’est ni plus ni moins qu’un système de gestion de fichiers distribué sur plusieurs machines (ou nœuds). L’immense avantage de HDFS est qu’il est totalement extensible et scalable par nature. Dans la terminologie HDFS, on retrouve les **DataNodes** qui contiennent les blocs de données et le **NameNode** qui joue en quelque sorte le rôle de chef d’orchestre du système de fichiers.
![[NameNode_DataNode.png]]
Le NameNode est en quelque sorte la pierre angulaire du système de fichiers et son unicité est aussi en quelque sorte son talon d’Achille. Bien souvent, on gère la notion de redondance et de tolérance de panne via un second NameNode répliqué, mais il existe heureusement d’autres manières de remédier à cette « faiblesse ».

![[Schéma fonctionnement HDFS.png]]

Dans le schéma ci-dessus, on constate par exemple deux grandes contraintes dues au fonctionnement de HDFS :

- Un fichier, quelle que soit sa taille, devra être stocké dans des blocs (qui sont par défaut dimensionnés à 128 Mo). Cela veut dire que, par exemple, si un fichier fait 129 Mo, le NameNode demandera le stockage de ce fichier sur 2 blocs (un de 128 Mo et un autre de 1 Mo). On se rend compte immédiatement que le dimensionnement de la taille des blocs aura un impact direct sur la quantité de stockage.
- La réplication des données (sur 3 DataNodes par défaut) a aussi un impact direct sur le volume de stockage, car si on reprend notre exemple précédent, il faudra prévoir en réalité 128 x 2 x 3 Mo soit 768 Mo d’espace disponible (par rapport à notre fichier initial de 129 Mo).

**MAPREDUCE**

Hadoop propose aussi son pendant en matière de traitement de données : **MapReduce**. Le composant MapReduce, tout comme HDFS, existe depuis le début d’Hadoop à tel point que ce service de parallélisation des traitements utilise pleinement HDFS et ne peut d’ailleurs pas fonctionner sans.

MapReduce fonctionne en deux phases qui sont, comme son nom l’indique, Map et Reduce. La phase de Map décompose/découpe les traitements pour les exécuter sur des nœuds du cluster séparés et de manière parallèle. Quant à la phase Reduce, elle agrège les données pour rendre un résultat unique.

![[Schéma fonctionnement MAPREDUCE.png]]

Comme on le voit dans le schéma ci-dessus, outre ce fonctionnement en deux phases, MapReduce a aussi une autre contrainte de fonctionnement car il ne fonctionne qu’avec des données au format kv (k comme clé, v comme valeur). Dans certains cas de figure, ce mode atteindra très vite ses limites

**YARN**

Yarn est venu par la suite. YARN libère MapReduce de sa fonction de négociateur de ressource. L’impact a un second effet très important, il est désormais possible d’utiliser une autre technologie que MapReduce pour les traitements sur le cluster (tels que Tez ou Spark) :

![[Hadoop YARN.png]]

# **B. L'écosystème  HADOOP**

![[Ecosystème Hadoop.png]]

###### **Systèmes d’exploitation, (Operating System (OS))**

Nativement hadoop est compatible Linux. Ce n’est que depuis la version hadoop 2.0 que l’on peut l’installer sur windows.
###### **Stockage des données**

- **HDFS (Hadoop Distributed File System)** : C’est le Système de stockage de fichiers  distribué de Hadoop. Il permet de stocker au format natif n’importe quel objets (image, vidéo, fichiers  texte etc…) en faisant porter la charge sur plusieurs serveurs.
- **HBASE** : Base NoSQL orientée colonnes. Le stockage à proprement parler reste du HDFS mais hbase apporte une surcouche de stockage qui permet de bénéficier des avantages des bases orientées colonnes, à savoir les colonnes dynamiques (deux individus d’une même table n’ont pas forcément les même colonnes, les valeurs null ne sont pas stockées) et l’historisation à la valeur et non-plus à la ligne (suppression des doublons, quand une valeur change seule la valeur concernée est historisée et non toute la ligne).
- **Metastore de HIVE** : Le metastore de Hive apporte le côté base de données relationnelle dans Hadoop. Il permet de stocker la structure des tables et des bases de données créées via hive ou un autre framework SQL (impala, spark etc…..). Les données restent stockées en hdfs mais le metastore apporte une surcouche qui permet de connaître leurs structures et de retrouver cette notion de ‘tables’ connu en décisionnel et d’utiliser le SQL.
###### **Gestionnaires de ressources**

- **Yarn (Yet Another Resource Negotiator)** :  Il s’occupe de la gestion et de l’allocation des ressources (CPU, Ram etc..) aux différentes applications (mapreduce, spark, impala etc…) lancées sur le cluster.
- **Mesos** : Projet Apache plus récent que Yarn, c’est aussi un système de gestion de ressource de clusters. Il va permettre de gérer et de partager de manière fine, souple et dynamique des ressources entre différents clusters, pour diverses applications.

###### **Récupération des données**

- **Apache Flume** : C’est un système distribué permettant de récupérer des logs de plusieurs sources, de les agréger et de les pousser dans HDFS. Il est fiable, flexible, assez intuitif et porté par toutes les distributions Hadoop.
- **Apache Storm** : Système distribué qui permet la récupération et le traitement en temps réel, il ajoute des capacités de traitements de données à Hadoop.
- **Spark Streaming** : Librairie de spark permettant la récupération et le traitement de donnée en temps réel. (requiert l’installation de spark, voir plus loin)
- **Kafka** : Système distribué de messagerie pour l’agrégation de log, le traitement en temps réel et le monitoring. Développé par linkedin et écrit en scala.
- **Flink** : Il fournit un framework de traitements distribué en mémoire. Très similaire à spark sauf que son coeur est en java (vs scala) et qu’il a été conçu nativement pour le temps réel.
- **Apache Sqoop** : Ce projet permet de faire le lien entre un système de gestion de base de données relationnel (SGBDR) et HDFS.
###### **Moteurs d’interrogation et de manipulation des données** 

- **MapReduce** : Framework open source java, permettant la manipulation des données dans un environnement distribué. Il est composé de deux étapes principales.
- L’étape de map qui va permettre d’effectuer des actions là ou sont stockées les données et fournir en sortie une liste de clés valeurs.
- L’étape de reduce qui va regrouper les résultats des map en fonctions de clés et effectuer les actions  finales ( les actions sur les valeurs?).

Les étapes de map et de reduce lisent  les données et écrivent leurs résultats sur disque , cela rend le processus stable mais lent.

- **Impala** : Moteur SQL distribué mis en place et proposé par Cloudera. Il s’appuie sur le metastore de hive pour connaître le format des données. Il va 20 fois plus que vite que MapReduce mais n’est pour l’instant qu’un complément car il n’offre pas encore toutes les fonctionnalités de mapreduce (sérialisation notamment)
- **Apache Drill** : Moteur SQL open source développé initialement par MapR  et maintenant porté par la fondation Apache permettant d’explorer les données stockées dans un cluster Hadoop ou dans des bases NoSQL. Apache Drill permet d’exécuter des requêtes sans avoir à définir un schéma de données, ce qui offre une grande flexibilité aux utilisateurs.
- **Apache Tez** : Moteur SQL distribué initié par Hortonworks qui vise à remplacer mapreduce notamment au niveau de Hive.
- **Spark** : Projet  permettant la manipulation des données dans un environnement distribué. Il peut aussi bien faire les traitements sur disque ou tout en mémoire. Il va 10 fois plus vite que mapreduce sur disque et 100 fois plus vite en mémoire. Il est enrichi de librairies notamment MLiB qui contient des algorithmes parallélisés de machine learning, GraphX pour les algorithmes de graphes, SparkSQL pour notamment se connecter au metastore de Hive. Spark peut se plugger sur la majorité des systèmes distribués (NoSQL, Hadoop, MPP …). Il peut fonctionner en mode standalone ou être géré par un gestionnaire de ressources tel que Yarn ou Mesos. Il permet nativement de coder en scala, java ou python.
- **Hive** : Hive est donc composé d’un metastore et d’un driver. Ce dernier va permettre de prendre en entrée du SQL et de générer du map reduce pour manipuler des données dont on connaît la structure.
- **Pig** : Moteur permettant de manipuler tous types de données avec un langage beaucoup plus intuitif que le java mapreduce. Il est beaucoup utilisé pour tous les process ETL (extraction transformation de données), il permet d’aller plus loin que le SQL. Une fois exécuter le code Pig génère du mapreduce.
- **Mahout** : Librairie java contenant des algorithmes de machine learning déjà codé en map reduce. Son développement est ralenti au profit de la librairie Mlib de Spark
###### **Ordonnanceurs**

- **Oozie** : Il permet d’ordonnancer et de lancer tous types d’applications (spark, impala, shell, hive, pig ….) dans l’écosystème Hadoop.
- **Airflow :** Outil open source développé par airbnb qui permet d’ordonnancer des jobs shell en intégrant nativement la notion de flux.
- **Jenkins** :  Permet d’ordonnancer et de scheduler des job shell
###### **Interfaces et coordinations**

- **Zookeeper** : Zookeeper permet de mettre en œuvre la coordination des services de l’écosystème et leur synchronisation dans un environnement distribué. Seul les administrateurs peuvent être amené à interagir avec lui.
- **Hue** : Interface web qui permet d’accéder directement aux principaux modules (hive, pig, sqoop, spark, impala, etc……). Nativement on peut accéder aux modules en ligne de commandes. Hue apporte une interface commune et agréable d’utilisation.


###### **Composants HADOOP en détails**
Hive
Hive est une technologie d’accès au stockage de données HDFS à des fins analytiques (Data Warehouse) dans Hadoop. Hive est donc en quelque sorte une passerelle d’accès aux données via le langage SQL. Dit autrement, cette technologie donne l’illusion d’une base de données relationnelle (SGBDR) sur Hadoop/HDFS.
En réalité, Hive ne stocke rien (à part des métadonnées), ce n’est donc pas une base de données. À l’origine, Hive a été développé par Facebook et utilise pleinement HDFS pour l’accès aux données. Ce qui rend Hive très apprécié est qu’il propose un langage d’interrogation assez proche du SQL (norme ANSI- 92) : le **HiveQL**. L’une des forces de HiveQL est de permettre aux développeurs d’intégrer des fonctions Map et Reduce directement à leurs requêtes (UDF : _User Defined Function_).
HBase
HBase (Apache) est une base de données NoSQL qui a pour particularité de stocker les données en colonnes et non en lignes comme dans le cas de bases de données relationnelles.

Caractéristiques :

ˇ     Base NoSQL

ˇ     Stockage Colonne

ˇ     Architecture Maître-Esclave

ˇ     Interrogation : service REST, Java API, Shell/CLI, AVRO/THRIFT (Python, etc.)

Sqoop

Sqoop est un outil qui permet de gérer les transferts de données dans Hadoop/HDFS (via import/export) à partir de ou vers une autre base de données relationnelle.

Caractéristiques :

ˇ     Ce n’est pas une base de données mais plutôt un Utilitaire de transport de données.

ˇ     Import/export vers des bases de données relationnelles et Hadoop (HDFS/Hive/HBase).

ˇ     Permet de créer des Jobs de transport et de fusionner des sources.

Cassandra

Cassandra est une base de données NoSQL conçue pour gérer des très forts volumes de données tout en assurant une très haute disponibilité.

  

Caractéristiques :

ˇ     Base NoSQL

ˇ     Stockage Colonne

ˇ     Architecture sans Maître

ˇ     Langage d’interrogation : CQL (_Cassandra Query Language_)

MongoDB

MongoDB est une base de données conçue pour stocker et gérer des documents. Caractéristiques :

Base NoSQL

Stockage orienté Document (BSON: Binary JSON)/identifié par un UUID