# **STEP 4: Scenario rates**

This step interrogates the <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> database to retrieve the probabilities of occurrence of each of the scenarios selected by <a href=../step3 target="_blank">STEP 3</a>, including the whole epistemic uncertainty. In other words, for any given earthquake scenario, we obtain a distribution of the mean annual rates of occurrence from 1000 alternative models.

This step is automatized when using <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> v. 1.1 (i.e. when the target site is located in the Mediterranean area), and is parallelized on the regions of the tectonic regionalization where the selected scenarios are located: through a job array, one process for each involved region is executed on the computational nodes of the HCP cluster. Separate output files for each region are produced for each seismicity type, and merged at the end.

In case <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> v. 1.0 must be used (i.e. outside the Mediterranean), a specific code must be manually executed, producing a single output file for each seismicity type.

The final output is saved in the output folder `RATES` and will be used by <a href=../step6 target="_blank">STEP 6</a>.
