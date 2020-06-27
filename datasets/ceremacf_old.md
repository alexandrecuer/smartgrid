---
layout: default
permalink: ceremacf_old.html
---

My very first dataset, collected from january 2017 to july 2019

A lot of gaps in the data

To unpack :
```
wget https://raw.githubusercontent.com/alexandrecuer/smartgrid/master/datasets/emoncms-backup-2018-03-29.tar.gz
tar -xvf emoncms-backup-2018-03-29.tar.gz
```
## heating systems
feed number|label|interval (s)
--|--|--
15 | T circ cellule |10
12 | T ext est |10
13 | T ext ouest |10
14 | T circ nord |10
11 | T ext hallssol |10
10 | Text_sud |10
9 | Text_cellule |10
8 | Text_nord |10
16 | circ_sud |10
17 | circ_ssolhall |10
18 | circ_est |10
19 | circ_ouest |10
91 | Tcollecteur |10
92 | Cellule_Pompe |10
93 | Cellule_V3V_FER |10
94 | Cellule_V3V_OUV |10
95 | Nord_Pompe |10
96 | Nord_V3V_FER |10
97 | Nord_V3V_OUV |10
98 | Sud_Pompe |10
99 | Sud_V3V_FER |10
100 | Sud_V3V_OUV |10
101 | SSHall_Pompe |10
102 | SSHall_V3V_FER |10
103 | SSHal_V3V_OUV |10
104 | Est_Pompe |10
105 | Est_V3V_FER |10
106 | Est_V3V_OUV |10
107 | Ouest_Pompe |10
108 | Ouest_V3V_FER |10
109 | Ouest_V3V_OUV |10
110 | node:chaudiere:EtatC1 |10
111 | node:chaudiere:Consigne |10
112 | node:chaudiere:ConsigneC1 |10
113 | node:chaudiere:EtatC2 |10
114 | node:chaudiere:ConsigneC2 |10
115 | VAN_pr_atm |10
116 | VAN_T_int |10
117 | VAN_HR_int |10
118 | VAN_Text |10
119 | VAN_HR_ext |10
120 | VAN_UV |10
121 | VAN_ray_sol |10
122 | VAN_precip |10
123 | VAN_vitesse_vent |10
124 | node:chaudiere:EtatC3 |10
125 | node:chaudiere:ConsigneC3 |10
126 | VAN_precip_mmh |10

## offices

Most recordings were done when trying to debug the tcp client of the ethersia library

### ECA
heated through circuit cellules
feed number|label|interval (s)
--|--|--
26 | temp_satellite_ECA |30
27 | RH_satellite_ECA |30
30 | millis recording |30
79 | ReSynAck GCM_ECA |30
80 | ReData GCM_ECA |30
81 | ReFinAck GCM_ECA |30
82 | nbTimeOut GCM_ECA |30

### chateau
heated through circuit Est/Ouest
feed number|label|interval (s)
--|--|--
31 | temp_chateau |30
32 | RH_chateau |30
66 | _millis chateau |30

### SOA
heated through circuit cellules
feed number|label|interval (s)
--|--|--
33 | temp1_satellite_GCM_SOA |30
34 | temp2_satellite_GCM_SOA |30
35 | RH_satellite_B_GCM_SOA |30
52 | timeout GCM_SOA |30
53 | ReSynAck GCM_SOA |30
54 | ReData GCM_SOA |30
55 | ReFinAck GCM_SOA |30
64 | _millis GCM_SOA |30
75 | RcvPkts GCM_SOA |30
76 | Dropped GCM_SOA |30

### GREI
heated through circuit cellules
feed number|label|interval (s)
--|--|--
41 | temp1_bureau_sebastienL |30
42 | temp2_bureau_sebastienL |30
43 | TH_bureau_sebastienL |30
68 | _millis GREI_Sebastien |30
83 | nbTimeOut GREI_Sebastien |30
84 | ReSynAck GREI_Sebastien |30
85 | ReData GREI_Sebastien |30
86 | ReFinAck GREI_Sebastien |30

### 1 wire bus
feed number|label|interval (s)
--|--|--
44 | _nbrexmit Node No1wireBus |30
47 | ReSynAck Node No1wireBus |30
49 | nbRST Node No1wireBus |30
50 | ReData Node No1wireBus |30
51 | ReFinAck Node No1wireBus |30
