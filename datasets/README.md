# kit of datasets collected from the field

All datasets are in emoncms format

All data stored in .dat file are 4 bytes (32 bits) float

To control metas if doubt, open the .meta file	
it contains 16 bytes	
- 4 bytes	Unused – deprecated
- 4 bytes	Unused – deprecated
- 4 bytes	Interval – unsigned integer
- 4 bytes	start time – unsigned integer


## [Allier habitat dataset](emoncms-backup-2019-08-19.tar.gz)

House|	label|	Feed Number|	StartTime<br>unixTimestamp<br>(s)|	StartTime<br>human |	interval<br>(s)	|unit
--|--|--|--|--|--|--
all	|Text	|1	|1520527800	|08/03/18	|300	|°C
all	|Wind speed m/s	|292	|1542630300	|19/11/18	|300	|m/s
témoin	|electricity consumption due to heating	|139	|1526549760	|17/05/18|	60	|W
témoin	|full electricity consumption	|137	|1526549700	|17/05/18	|60	|W
témoin	|T living room	|191	|1526978400	|22/05/18	|120	|°C
témoin	|T kitchen	|194	|1526978400	|22/05/18	|120	|°C
témoin	|T bathroom	|197	|1526978520	|22/05/18	|120	|°C
témoin	|T bedroom	|200	|1526978520	|22/05/18	|120	|°C
ITE	|electricity consumption due to heating	|145	|1526549880	|17/05/18	|60	|W
ITE	|other electricity consumptions	|141	|1526549820	|17/05/18	|60	|W
ITE	|T living room	|167	|1526978160	|22/05/18	|120	|°C
ITE	|T kitchen	|170	|1526978160	|22/05/18	|120	|°C
ITE	|T bathroom	|173	|1526978280	|22/05/18	|120	|°C
ITE	|T bedroom	|176	|1526978280	|22/05/18	|120	|°C
THERMACOTE	|electricity consumption due to heating	|151	|1526550060	|17/05/18	|60|	W
THERMACOTE	|other electricity consumptions	|147	|1526549940	|17/05/18	|60	|W
THERMACOTE	|T living room	|179	|1526978280	|22/05/18	|120	|°C
THERMACOTE	|T kitchen	|182	|1526978280	|22/05/18	|120	|°C
THERMACOTE	|T bathroom	|185	|1526978400	|22/05/18	|120	|°C
THERMACOTE	|T bedroom	|188	|1526978400	|22/05/18	|120	|°C
