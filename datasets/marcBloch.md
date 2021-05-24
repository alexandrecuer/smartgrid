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

## les données physiques

label|	Feed Number|	StartTime<br>unixTimestamp<br>(s)|	interval<br>(s) | unit
--|--|--|--|--
température extérieure | 5	|1612789800	|300	|°C
consommation de la pompe 2 circuit Sud | 6	|1612789800	|300	|W
consommation de la pompe 2 circuit Nord | 23	|1612790100	|300	|W

## Les timers (uniquement pour qualifier la qualité de la réception radio)

label|	Feed Number|	StartTime<br>unixTimestamp<br>(s)|	interval<br>(s)
--|--|--|--
température extérieure | 4 | 1612789800 | 300
