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

electric heating !!

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


## [Cerema Clermont-Ferrand boiling room](emoncms-backup-2020-04-22.tar.gz)

hot water circuits !! collected during winter 2019-2020 before COVID 19 spreading in Europe

3 circuits monitored :
- cellules
- north
- south

circuit |label |	Feed Number
--|--|--
cellules|indoor temperature|56 (45)
cellules|power consumption in W|66
north|indoor temperature|48
north|power consumption in W|68
south|indoor temperature|51
north|power consumption in W|70
all|outdoor temperature|18
all|global solar radiation in W/m2|21

all power calculated with constant flow rates, using the water heat capacity : 1162.5 Wh/m-3/K

circuit |label |	Feed Number
--|--|--
cellules|pump on/off | 26
cellules|3-way valve closing | 27
cellules|3-way valve opening | 28
north|pump on/off | 32
north|3-way valve closing | 33
north|3-way valve opening | 34
south|pump on/off | 37
south|3-way valve closing | 38
south|3-way valve opening | 39

circuits temperatures in °C |	Feed Number
--|--
T initial cellules | 25
T return cellules | 29
T initial north | 31
T return north | 35
T initial south | 36
T return south | 40

circuit | flow rate in m3/h
--|--
cellules | 5.19
north | 6.5 
south | 4.2
East | 1.38
West | 1.1
Hall basement | 2.6
