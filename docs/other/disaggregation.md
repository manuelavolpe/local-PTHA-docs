# **The disaggregation procedure**

This procedure finds, among all of the scenarios retrieved from <a href=../../steps/step2 target="_blank">STEP 2</a>, the most relevant ones for the target site, i.e. the scenarios that contribute most significantly to the tsunami hazard at each POI, within predefined MIH (Maximum Inundation Heights) intervals or thresholds and fixing the desired percentage of hazard reproduction. It is based on the mean model of the epistemic uncertainty. For example, we may want a list of those scenarios accounting for 95% of the total hazard within the 1-4 m MIH range, or for MIH > 1 m (more intervals or more thresholds are allowed).

For each selected POI, the algorithm first ranks all the scenarios contributing to a given intensity, or intensity interval, according to their relative importance for the site of interest, measured as their relative contribution to the local offshore hazard curve in terms of mean annual rates. Then, the scenarios are taken up to the desired “level of accuracy” to which the local hazard should be approximated, defined in terms of the resemblance of the hazard curve calculated at the POI using the selected scenarios with respect to the original one. 

A separate output folder is created, named `DISAGGREGATION_POIname`, for each POI. Then, the lists are merged removing duplicates, and the net list of scenarios is saved in a new folder `DISAGGREGATION`.