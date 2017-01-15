# élaboration de documents à l'aide de markdown et pandoc à partir des pages d'un wiki Github
## quelques précisions sur la syntaxe markdown

Le caractère pour-cent % sert à formatter la page de garde

On peut utiliser jusqu'à 3 lignes commencant par des caractères %, par exemple pour indiquer le titre du document, le nom du(des) auteur(s) ou la date de révision du document

Si l'une ou l'autre de ces informations doit être omise, laissez le caractère % suivi d'une ligne vide. Si le titre ou la définition des auteurs nécessitent plusieurs lignes de texte, on peut faire usage de lignes supplémentaires pour autant qu'elles débutent par un espace.

Notez finalement que l'on peut faire usage de styles et liens (techniques présentées plus bas) à l'intérieur des titres.

On peut utiliser plusieurs niveaux de titre en utilisant les caractères # (Titre de niveau 1), ## (Titre de niveau 2), etc, etc

Pour injecter des figures, il est nécessaire d'installer le logiciel github desktop

Markdown interprète toute ligne commencant par ! comme une figure

La syntaxe ![texte alternatif](URL_IMAGE "titre optionnel")

Pour numéroter les figures on utilise la syntaxe dérivée du LateX en fixant un label \label{nom_label} et en faisant une référence (cf figure \ref{emonfront})



