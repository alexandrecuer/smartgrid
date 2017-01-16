# élaboration de documents à l'aide de markdown et pandoc à partir des pages d'un wiki Github
## quelques précisions sur la syntaxe markdown

Pour des explications détaillées sur pandoc en français, on se référera au site suivant :

http://enacit1.epfl.ch/markdown-pandoc/

### page de garde
Le caractère pour-cent % sert à formatter la page de garde

On peut utiliser jusqu'à 3 lignes commencant par des caractères %, par exemple pour indiquer le titre du document, le nom du(des) auteur(s) ou la date de révision du document

Si l'une ou l'autre de ces informations doit être omise, laissez le caractère % suivi d'une ligne vide. Si le titre ou la définition des auteurs nécessitent plusieurs lignes de texte, on peut faire usage de lignes supplémentaires pour autant qu'elles débutent par un espace.

### niveaux de titres

On peut utiliser plusieurs niveaux de titre en utilisant les caractères # (Titre de niveau 1), ## (Titre de niveau 2), etc, etc

### clonage avec le logiciel github desktop

Ce logiciel permet de cloner l'intégralité du projet dans un répertoire de son ordinateur

Sous windows 10, ce répertoire est généralement C:\Users\nom_user\Documents\GitHub\smartgrid.wiki

On organise ensuite ce dossier comme on veut et gituhub desktop 

Si on est derrière un proxy, il faut le déclarer pour que github desktop puisse cloner correctement 

Pour celà, on ouvre un git bash et on lance la commande suivante, en remplaçant LOGIN, PASSWORD et YOUR.PROXY.SERVER par les paramètres convenant à son réseau :

~~~~~~~ { .bash }
git config --global http.proxy http://LOGIN:PASSWORD@YOUR.PROXY.SERVER:8080
~~~~~~~


### gestion de figures
Pour injecter des figures au sein du wiki, il est nécessaire d'installer le logiciel github desktop

Markdown interprète toute ligne commencant par ! comme une figure

Pour numéroter les figures on utilise la syntaxe dérivée du LateX en fixant un label \label{nom_label} à la suite du texte descriptif de l'image en les crochets succédant au ! 

On réalise ensuite les références dans le corps de texte de la manière suivante (cf figure \ref{nom_label})

~~~~~~~ { .markdown }
(cf figure \ref{mon_label_de_figure})
......bla bla bla.......
![ma_description \label{mon_label_de_figure}](mon_image.png)
~~~~~~~



### gestion des pages du wiki

Chaque page du wiki doit être terminée par ***

### export en pdf

On peut ensuite créer un pdf avec le logiciel pandoc. A noter qu'il faut avoir MiKTeX d'installé.

http://pandoc.org/

http://miktex.org/


Pandoc peut créer automatiquement une table des matières et tous les signets afférents avec l'option --toc

(cf document smart_grid_version_test_15_01_2017.pdf ci joint à la racine de ce dossier)
