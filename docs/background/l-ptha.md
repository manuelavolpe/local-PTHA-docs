# **Local-scale PTHA**

Probabilistic Tsunami Hazard Analysis (PTHA) quantifies the likelihood of exceeding a specified measure of tsunami inundation at a given location within a given time interval. It provides scientific guidance for decision-making regarding coastal engineering and evacuation planning.

PTHA considers a discretization of the total hazard into many potential scenarios together with an evaluation of the probability of each scenario. Site-specific (i.e. local) PTHA, with an adequate discretization of source scenarios, combined with high-resolution inundation modeling, requires tens to hundreds of thousands of moderately intensive numerical simulations.

In recent years, more efficient GPU-based High-Performance Computing (HPC) facilities, together with efficient GPU-optimized shallow water type models for simulating tsunami inundation, have made regional and local long-term hazard assessment feasible.

The present tool allows for assessing local PTHA at a given target site by exploiting the NEAM Tsunami Hazard Model 2018 or <a href=../neamthm18 target="_blank">NEAMTHM18</a> (<a href=https://doi.org/10.3389/feart.2020.616594 target="_blank">Basili et al., 2021</a>) as a starting point. In principle, different regional models could be used, although this capability is not implemented yet.

A description of the PTHA procedure applied to the town of Catania on the Eastern coast of Sicily can be found in [Gibbons et al. (2020)](https://doi.org/10.3389/feart.2020.591549).
