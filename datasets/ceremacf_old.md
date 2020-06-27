---
layout: default
permalink: ceremacf_old.html
---

To unpack :
```
wget https://raw.githubusercontent.com/alexandrecuer/smartgrid/master/datasets/emoncms-backup-2018-03-29.tar.gz
tar -xvf emoncms-backup-2018-03-29.tar.gz
```

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
27 | RH_satellite_ECA
26 | temp_satellite_ECA
30 | millis recording
31 | temp_chateau
32 | RH_chateau
33 | temp1_satellite_GCM_SOA
34 | temp2_satellite_GCM_SOA
35 | RH_satellite_B_GCM_SOA
43 | TH_bureau_sebastienL
42 | temp2_bureau_sebastienL
41 | temp1_bureau_sebastienL
44 | _nbrexmit Node No1wireBus
47 | ReSynAck Node No1wireBus
52 | timeout GCM_SOA
49 | nbRST Node No1wireBus
50 | ReData Node No1wireBus
51 | ReFinAck Node No1wireBus
53 | ReSynAck GCM_SOA
54 | ReData GCM_SOA
55 | ReFinAck GCM_SOA
91 | Tcollecteur
86 | ReFinAck GREI_Sebastien
93 | Cellule_V3V_FER
85 | ReData GREI_Sebastien
64 | _millis GCM_SOA
94 | Cellule_V3V_OUV
68 | _millis GREI_Sebastien
66 | _millis chateau
79 | ReSynAck GCM_ECA
80 | ReData GCM_ECA
81 | ReFinAck GCM_ECA
84 | ReSynAck GREI_Sebastien
82 | nbTimeOut GCM_ECA
83 | nbTimeOut GREI_Sebastien
92 | Cellule_Pompe |10
75 | RcvPkts GCM_SOA
76 | Dropped GCM_SOA
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
