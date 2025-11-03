# **The disaggregation procedure**

This procedure selects, among all of the scenarios retrieved from <a href=../../steps/step2 target="_blank">STEP 2</a>, the most relevant ones for the target site, i.e. the scenarios that  most significantly contribute to the tsunami hazard at each offshore POI, within predefined MIH (Maximum Inundation Heights) intervals or thresholds and fixing the desired percentage of hazard reproduction. It is based on the mean model of the epistemic uncertainty. For example, we may want a list of those scenarios accounting for 95% of the total hazard within the 1-4 m MIH range, or for MIH > 1 m (more intervals or more thresholds are allowed).

For each selected POI, the algorithm first ranks all the contributing scenarios for a given intensity, or intensity interval, according to their relative importance for the target site, measured as their relative contribution to the offshore hazard curve in terms of mean annual rates. Then, the scenarios are collected up to the desired “degree of accuracy” to which the local hazard should be approximated, defined in terms of the resemblance of the offshore hazard curve calculated using only the selected scenarios with respect to the original one.

For example, suppose that, for a given POI, a disaggregation procedure targeting the 95% of accuracy is desired, which means that with the selected scenarios the 95% of the hazard curve is well reproduced. If four MIH thresholds are chosen ()

For each POI, a separate output folder is created named `DISAGGREGATION_POIname`. Then, the lists are merged removing duplicates, and the net list of scenarios is saved in a new folder `DISAGGREGATION`.
