# **General overview**

Here is a brief description of the steps that form the workflow. More detailed explanations are available on the corresponding dedicated pages.

<a href=../step1 target="_blank">STEP 1 - Selection of the POI(s)</a> &rarr; aimed at selecting, from the <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> database, the offshore Point(s) of Interest in front of the target site, using the extension of the local grid or the coordinates of the site of interest or directly the labels of the desired POIs, if known (the options are mutually exclusive).

<a href=../step2 target="_blank">STEP 2 - Scenario Dumping</a> &rarr; aimed at extracting, from the <a href="The-regional-hazard-model-NEAMTHM18" target="_blank">NEAMTHM18</a> database, all the earthquake scenarios and corresponding metadata that contribute to the tsunami hazard at the target site.

<a href=../step3 target="_blank">STEP 3 - Scenario Selection</a> &rarr; aimed at selecting, from the dumped scenarios, a number of relevant scenarios significantly contributing to the tsunami hazard at the target site. Presently, the implemented procedure is a <a href=../../other/disaggregation target="_blank">disaggregation</a> from the total hazard, based on the mean model of the epistemic uncertainty. In the future, other approaches will be implemented, such as the <a href=../../other/sampling target="_blank">importance sampling</a>.

<a href=../step4 target="_blank">STEP 4 - Scenario Annual Rates</a> &rarr; aimed at retrieving the annual rates of occurrence, including the epistemic uncertainty, for the ensemble of scenarios obtained from the selection procedure.

<a href=../step5 target="_blank">STEP 5 - Tsunami Simulations</a> &rarr; aimed at setting up and executing, for each scenario, the high-resolution numerical simulations of the tsunami inundation on telescopic <a href=../../background/nested_grids target="_blank">nested grids</a>, using the <a href=../../background/Tsunami-HySEA target="_blank">Tsunami-HySEA</a> numerical code.

<a href=../step6 target="_blank">STEP 6 - Hazard aggregation</a> &rarr; aimed at combining the tsunami amplitude computed through the numerical simulations with the scenario rates, in order to calculate the hazard curves on a predefined set of MIH (Maximum Inundation Height) thresholds.

<a href=../step7 target="_blank">STEP 7 - Visualization</a> &rarr; aimed at producing hazard and inundation maps for selected average return periods (ARPs) for visualization, as well as exporting the hazard curves as *csv* tables for distribution.
