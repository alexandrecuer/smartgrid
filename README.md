# élaboration de documents à l'aide de markdown et pandoc à partir des pages d'un wiki Github
## quelques précisions sur la syntaxe markdown

### page de garde
Le caractère pour-cent % sert à formatter la page de garde

On peut utiliser jusqu'à 3 lignes commencant par des caractères %, par exemple pour indiquer le titre du document, le nom du(des) auteur(s) ou la date de révision du document

Si l'une ou l'autre de ces informations doit être omise, laissez le caractère % suivi d'une ligne vide. Si le titre ou la définition des auteurs nécessitent plusieurs lignes de texte, on peut faire usage de lignes supplémentaires pour autant qu'elles débutent par un espace.

### niveaux de titres

On peut utiliser plusieurs niveaux de titre en utilisant les caractères # (Titre de niveau 1), ## (Titre de niveau 2), etc, etc

### gestion de figures
Pour injecter des figures au sein du wiki, il est nécessaire d'installer le logiciel github desktop

Markdown interprète toute ligne commencant par ! comme une figure

Pour numéroter les figures on utilise la syntaxe dérivée du LateX en fixant un label \label{nom_label} à la suite du texte descriptif de l'image en les crochets succédant au ! 

On réalise ensuite les références dans le corps de texte de la manière suivante (cf figure \ref{nom_label})

### gestion des pages du wiki

Chaque page du wiki doit être terminée par ***

### export en pdf

On peut ensuite créer un pdf avec le logiciel pandoc. A noter qu'il faut avoir MiKTeX d'installé.

Pandoc peut créer automatiquement une table des matière et tous les signets correspondant avec l'option --toc

(cf document smart_grid_version_test_15_01_2017.pdf ci joint à la racine de ce dossier)
