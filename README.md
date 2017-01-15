# élaboration de documents à l'aide de markdown et pandoc à partir des pages d'un wiki Github
## quelques précisions sur la syntaxe markdown

Le caractère pour-cent % sert à formatter la page de garde

On peut utiliser jusqu'à 3 lignes commencant par des caractères %, par exemple pour indiquer le titre du document, le nom du(des) auteur(s) ou la date de révision du document

Si l'une ou l'autre de ces informations doit être omise, laissez le caractère % suivi d'une ligne vide. Si le titre ou la définition des auteurs nécessitent plusieurs lignes de texte, on peut faire usage de lignes supplémentaires pour autant qu'elles débutent par un espace.

Notez finalement que l'on peut faire usage de styles et liens (techniques présentées plus bas) à l'intérieur des titres.

On peut utiliser plusieurs niveaux de titre en utilisant les caractères # (Titre de niveau 1), ## (Titre de niveau 2), etc, etc

Pour injecter des figures, il est nécessaire d'installer le logiciel github desktop

Markdown interprète toute ligne commencant par ! comme une figure

la syntaxe est la suivante ![]()

Pour numéroter les figures on utilise la syntaxe dérivée du LateX en fixant un label ![description \label{nom_label}](nom_image.png) et en faisant une référence

Emoncms (cf figure \ref{emonfront}) est totalement orienté objet et son architecture logicielle repose sur un port PHP recevant tout le trafic entrant pour l’orienter vers divers modules de traitement, en vue d’un enregistrement dans des flux de données, ou de visualisation.


