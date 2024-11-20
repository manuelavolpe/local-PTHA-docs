# **General overview**

Here is a brief description of the steps that make up the workflow. Further details can be found in the specific dedicated pages.

<a href=../step1 target="_blank">STEP 1</a> -  Selection of the POI(s) &rarr; to select, from the <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> database, the offshore  Point(s) of Interest in front of the target site, using the extension of the local grid or the coordinates of the site of interest or directly the labels of the
desired POIs, if known.

<a href=../step2 target="_blank">STEP 2</a> - Scenario Dumping &rarr; to extract, from the <a href="The-regional-hazard-model-NEAMTHM18" target="_blank">NEAMTHM18</a> database, all of the earthquake scenarios and corresponding metadata that contribute to the tsunami hazard at the target site.

<a href=../step3 target="_blank">STEP 3</a> -  Scenario Selection &rarr; to select, from the dumped scenarios, a number of relevant scenarios significantly contributing to the tsunami hazard at the target site. Presently, the implemented procedure is a <a href=../../other/disaggregation target="_blank">disaggregation</a> from the total hazard, based on the mean model of the epistemic uncertainty. In the future, other approaches will be implemented, such as the <a href=../../other/sampling target="_blank">importance sampling</a>.

<a href=../step4 target="_blank">STEP 4</a> -  Scenario Annual Rates &rarr; to retrieve the annual rates of occurrence, including the whole epistemic uncertainty, for all of the scenarios obtained from the sampling procedure.

<a href=../step5 target="_blank">STEP 5</a> - Tsunami Simulations, &rarr;  to set up and execute, for each scenario, high-resolution numerical simulations of the tsunami generation, propagation and inundation on telescopic nested grids, using the <a href=../../background/Tsunami-HySEA target="_blank">Tsunami-HySEA</a> numerical code.

<a href=../step6 target="_blank">STEP 6</a> - Hazard aggregation &rarr;  to combine the output from each simulation with the scenario rates in order to calculate the hazard curves on a predefined set of MIH (Maximum Inundation Height) thresholds.

<a href=../step7 target="_blank">STEP 7</a> - Visualization &rarr; to produce hazard and inundation maps for selected average return periods (ARPs) for visualization.
