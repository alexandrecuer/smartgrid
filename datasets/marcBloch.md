---
layout: default
permalink: bloch.html
---
# collège Marc Bloch

![site](images/bloch.png)

[download dataset](emoncms-backup-2021-05-24.tar.gz)

collected from february to june 2021

environ 800 à 1000 élèves

une chaufferie desservant 5 à 6 sous-stations

puissance de la chaudière de tête : 350 KW

to unpack :

```
wget https://raw.githubusercontent.com/alexandrecuer/smartgrid/master/datasets/emoncms-backup-2021-05-24.tar.gz
tar -xvf emoncms-backup-2021-05-24.tar.gz
```
Historisation dans les flux déclenchée le 08/02/21

# sous-station Ouest

## les données physiques

label|	Feed Number|	StartTime<br>unixTimestamp<br>(s)|	interval<br>(s) | unit
--|--|--|--|--
température extérieure | 5	|1612789800	|300	| °C
consommation de la pompe 2 circuit Sud | 6	|1612789800	|300	| W
consommation de la pompe 2 circuit Nord | 23	|1612790700	|300	| W
température intérieure B101 salle de musique Nord | 8 | 1612790100 | 300 | °C
humidité relative B101 salle de musique Nord | 9 | 1612790100 | 300 | %
température intérieure B209 salle de technologie Nord | 11 | 1612790100 | 300 | °C
humidité relative B209 salle de technologie Nord | 12 | 1612790400 | 300 | %
température intérieure B216 salle de cours Sud | 14 | 1612790400 | 300 | °C
humidité relative B216 salle de cours Sud | 15 | 1612790400 | 300 | %
température intérieure B140 salle d'art plastique Sud | 17 | 1612790400 | 300 | °C
humidité relative B140 salle d'art plastique Sud | 18 | 1612790400 | 300  | %
température de départ circuit Sud | 19 | 1612790400 | 300  | °C
température de retour circuit Sud | 20 | 1612790400 | 300  | °C
température de départ circuit Nord | 21 | 1612790400 | 300  | °C
température de retour circuit Nord | 22 | 1612790400 | 300  | °C
température d'ambiance dans la sous-station | 24 | 1612790700 | 300  | °C


## Les timers

uniquement pour qualifier la qualité de la réception radio

label|	Feed Number|	StartTime<br>unixTimestamp<br>(s)|	interval<br>(s)
--|--|--|--
température extérieure | 4 | 1612789800 | 300
B101 salle de musique Nord | 7 | 1612790100 | 300
B209 salle de technologie Nord | 10 | 1612790100 | 300
B216 salle de cours Sud | 13 | 1612790400 | 300
B140 salle d'art plastique Sud | 16 | 1612790400 | 300
