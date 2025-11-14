# **STEP 5: Tsunami simulations**

This step requires NVIDIA GPUs, in particular V100 or A100 cards (other architectures are expected to be supported in the future), to run the tsunami numerical simulations on <a href=../../background/nested_grids target="_blank">nested topo-bathymetric grids</a>, using the <a href=../../background/thysea target="_blank">Tsunami-HySEA</a> code (MC version), for each scenario selected by <a href=../../steps/step5 target="_blank">Step 3</a>. The typical number of sources to be modeled is $O(10^3-10^5)$.

Before starting, the "SIMULATION SETUP" section within the <a href=../../instructions/json_input target="_blank">JSON input file</a> must be completed, and the topo-bathymetric grids must be available in the folder declared at the beginning of the JSON file. Moreover, if the workflow is running on Leonardo@CINECA, the last 3 lines in the "HPC" section of the JSON file must be filled as well.

Simulations are carried out separately for each seismicity type, and different templates of the parameter files are provided within the folder `templates`. In brief, when executing this step, a new output folder called SIMULATIONS is created, and

* the simulation setup is prepared
* simulations are launched (i.e. submitted to the queue)
* post-processing is performed.

Depending on the HPC cluster, the simulations are grouped in packages made by as many simulations as GPUs on each computational node. In other words, each job is submitted on one single node and executes in parallel a number of simulations equal to the number of GPUs per node. Specifically, jobs made by 8 simulations are submitted on Mercalli@INGV (8 GPUs/node) and jobs made by 4 simulations are submitted on Leonardo@CINECA (4 GPUs/node). This choice represents a trade-off between an optimal usage of the computational resources and the control of the failures in case of node crashes. It is worth noting that each simulation will run in parallel on a single GPU, provided that computational nodes are available.

???+ Warning
    On Leonardo@CINECA a limit of 1000 simultaneous jobs per user is allowed. This means that if the total number of simulations overcomes 4000, then not all the simulations can be submitted in one shot and some manual operations are needed to execute them in multiple runs, for example by separating each seismicity type, provided that you have less than 4000 scenarios for each of them. The issue will be solved by allowing the use of more than one node per each job.

For each simulation, the maximum tsunami wave amplitude at each point in the highest resolution grid is saved, which is then converted into flow-depth (i.e. the water height on land) through a post-processing operation, transparent to the user, performed within the same job. Additionally, the tsunami time series at the selected POIs are also saved for further use.

It is worth noting that the simulations are organized in separate folders, one for each seismicity type and, inside that, one for each scenario.

???+ Tip
    It's a good practice to check at the end of this step if all the simulations succeeded, since some failures, due to node crashes or other technical issues, can always occur. One possible way to do that is to count the number of files `*_flowdepth.nc` in the simulation folders, which must be equal to the number of scenarios if one site (i.e. one grid nesting) is being considered, or in general equal to the number of scenarios $\times$ number of sites.