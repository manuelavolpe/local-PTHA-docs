# **STEP 2: Scenario dumping**

This step executes a first screening of the potential scenarios, by extracting from the <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> database all the earthquake scenarios (and corresponding metadata) which contribute to the tsunami hazard at the target site, i.e. at each selected offshore POI.

This step is automatized when using <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> v. 1.1 (i.e. when the target site is located in the Mediterranean area), and is parallelized on the regions of the tectonic regionalization: through a job array, one process for each region (and for each POI) is executed on the computational nodes of the HCP cluster. If scenarios affecting the POI are found in the region, separate output files are possibly produced for each seismicity type.

For each POI, a separate output folder is created named `DUMPING_POIname`.

In case <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> v. 1.0 must be used (i.e. outside the Mediterranean), a specific code must be manually executed, producing a single output file.

The output of this step serves as input for the following <a href=../step3 target="_blank">STEP 3</a>.
