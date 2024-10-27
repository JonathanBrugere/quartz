# Statistique R
## Introduction
Les statistiques sont l'interface entre l'homme les nombres

**La variable aléatoire :**
Quantitative --> on la mesure ; discrète : nombre limité de mesure , continu : nombre de mesure très grand ou infini
Qualitative --> non mesure par somme ou autre ; Ordonnée : associé une valeur a un critère (trouble --> 1), non ordonné : Valeur non numéraire , Binaire 1 ou 0 (Cancer --> 1 pour oui)

La loi de variable aléatoire correspond à la liste des probabilités que chacune des valeurs peut prendre

## Les premiers pas

**Importer fichier :**
définir le répertoire et le lien : nomfictifdufichierfictif <- read.csv2("lien avec des antislash")
Lecture de donnée : str(nomdufichierfictif)
**ou**
setwd("D:/mooc")
smp <- read.csv2("smp1.csv")

Variable aléatoire :
**Quantitative** ->
discrète = nombre limité résultat possible
continue = nombre illimité ou très grand nombre de résultat possible
**Qualitative ->**
ordonnée (niveau de satisfaction (code en 1 2 3...)

Représentation graphique : fonction table(nomdufichier$nomdelacolonne pour agréger) calculer le nombre des detenu en fonction de l'agregation voulu.

**Barplot**(table(...)) --> diagramme baton
**Pie**(table(...) --> diagramme circulaire
**Hist**(nomfichier$variable) --> utiliser pour des variable discrètes
		hist(nomfichier$variable, col="grey",main="",xlab="age"
		col = couleur
		xlab =nom abcisse
**Boxplot**(nomdufichier$variable,xlab="nomdelavariable" -->boite àmoustache.
A l'intérieur il y a 50% des données puis 25 et 25 en exterieur. Il y a des valeurs extrème egalement à la fin .
**Boxplot**(nomdufichier$variable,ylab="nomdelavariable",xlab="nomdelavariable"
**Plot**(nomdufichier$variableX,nomdufichier$variableY)
**Jitter** est une fonction qui permet de decaler les points de dispersion s'il sont identique.
![[Mes documents/_resources/Statistique_R.resources/image.png]]
Pour représenter une évolution temporel de la variable aléatoire on peut utiliser le diagramme temporel
![[Mes documents/_resources/Statistique_R.resources/image.1.png]]
library (glots)
**Plotmeans**(nomfichier$variable~nomdufichier$variable qui représente le temps,gap=0,barcol="black")e temps
diagramme en fagot représente chaque évolution des individus. On l'écrit :
**interaction.plot**(nomdufichier$variabletemps,variableindiquant les sujet, variable à représenter
![[./_resources/Statistique_R.resources/image.2.png]]
test : hist(smp1$age,main = "1er histo de jojo",col = "blue")
boxplot(smp1$rs)
plot(smp1$age,smp1$n.enfant)
plot(jitter(smp1$age),jitter(smp1$n.enfant))

**Mesure de position et de dispersion**
Position : moyenne/médiane. Si la moyenne est différente de la médiane c'est que la distribution est symétrique. Médiane --> 50% de la valeur sont en dessus et en dessus.
Dispersion : Quartiles/écart type
La mesure de dispersion est un complément de la mesure de position

![[Mes documents/_resources/Statistique_R.resources/image.3.png]]
Summary(smp1)
Library(PrettyR)
Describe(smp1)

![[Mes documents/_resources/Statistique_R.resources/image.4.png]]
#langageprogramation

