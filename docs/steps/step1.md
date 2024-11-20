# **STEP 1: POI(s) selection**

This step aims to select, from <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> database, the POI(s) which fall within a rectangular area containing the coastlines around the target site. Such rectangular area can be built in two ways:

1. if the high-resolution inner grid is available and declared within the <a href=../../instructions/json_input target="_blank">JSON input file</a>, the grid domain is used to draw a rectangle whose sides are then expanded by $X$ kilometers perpendicularly ($X=10$ km by default);
<img src="../../images/Catania_map_POI.png"/>

2. if the key "grdfile" in the <a href="The-JSON-input-file" target="_blank"> input file</a> is empty while the coordinates of the target site are provided, the first rectangle is drawn by moving $\pm X^\circ$ from the site both vertically and horizontally ($X = 0.1^\circ$ by default) and then its sides are extended as before;

If both the keys "grdfile" and "lonlat" are empty, the labels of the POIs are expected to be given by the user in the last field "poinames". This third option is mandatory in case of POI(s) outside the Mediterranean Sea.
 
The outputs of this step are text files with labels (\_POI_name.txt) and coordinates (\_ts.dat) of the selected POI(s). The last one is formatted to make the <a href="Tsunami-HySEA" target="_blank">HySEA code</a> save the time series at the POIs when running the tsunami simulations (<a href="Tsunami-Numerical-Simulations" target="_blank">Step 5</a>).

