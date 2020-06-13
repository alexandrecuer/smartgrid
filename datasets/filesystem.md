---
layout: default
permalink: filesystem.html
---
# kit of datasets collected from the field

All datasets are in emoncms format

A single dataset consists of 2 files :
- a .meta file
- a .dat file

All data stored in .dat file are 4 bytes (32 bits) float

To control metas if doubt, open the .meta file	
it contains 16 bytes	
- 4 bytes	Unused – deprecated
- 4 bytes	Unused – deprecated
- 4 bytes	Interval – unsigned integer
- 4 bytes	start time – unsigned integer

You may need an editor to perform such a manual check. On a linux OS, [Hexditor](http://flying.guy.chez-alice.fr/HexditorFr.php) is a cool choice :-)

most sets can be restored on an EmonPI

# python library

