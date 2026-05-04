Below are the details for the first 4 stops. 
City	Country	Venue	StoreID	Warehouses	Tent Store #	In-Venue Store #	Start Date	End Date
Tampa, FL	United States	Raymond James Stadium	NA-AA-434	2 (Memphis, local)	1	2	4/23/2026	4/28/2026
El Paso, TX	United States	Sun Bowl	NA-AA-422	2 (Memphis, local)	TBD	TBD	4/30/2026	5/3/2026
Stanford, CA	United States	Stanford Stadium	NA-AA-434	2 (Carson, local)	TBD	TBD	5/14/2026	5/19/2026
Las Vegas, NV	United States	Allegiant Stadium	NA-AA-422	2 (Carson, local)	TBD	TBD	5/21/2026	5/28/2026
 
After we met we discussed the store event bridge encoding schema.  Here’s the schema we propose:
 
<JWO Store ID>_<Tour>_<Stop>_<MerchNode>_#
 
JWO Store ID = NA-AA-422, NA-AA-434
Tour = BTS
Stop = Tampa, Stanford, ElPaso, LasVegas
MerchNode = warehouse, store
# = 1-10
 
e.g. for Tampa:
“NA-AA-434_BTS_TAMPA_WAREHOUSE_1”   Memphis warehouse location for Tampa merch
“NA-AA-434_BTS_TAMPA_WAREHOUSE_2”  Tampa local warehouse for verifying receipt of Memphis merch
“NA-AA-434_BTS_TAMPA_STORE_1”  presumptively “tent” store
“NA-AA-434_BTS_TAMPA_STORE_2”  presumptively “in-venue” store #1
“NA-AA-434_BTS_TAMPA_STORE_2”  presumptively “in-venue” store #2
 
