# **The JSON input file**


JSON (JavaScript Object Notation) is an open standard file format that uses human-readable text. The data are written in key/value pairs, separated by a colon(:). Different key/value pairs are separated by a comma(,).

A template of the `workflow_input.json` is provided, where all the required keys are already defined and grouped as objects, i.e. collections of key/value pairs surrounded by a curly brace. Comments are disseminated all along the file for the sake of clarity, and featured by the key "\_comment".

Before running the workflow, the JSON input file should be appropriately filled, although some sections may be neglected, depending on which steps will be executed. In other words, not all the sections in the JSON file need to be filled from the beginning if the corresponding step is not expected to be executed, as each step can be turned on/off by setting `True/False` within the input file. On the other hand, each step needs the output of the previous steps.

As explained in the <a href=../installation target="_blank">installation instructions</a>, the template must be copied and renamed. All the fields will now be described.

!!! note ""
    SETTINGS

This first section is mandatory from the very beginning. The required information is:

- the (complete) path for the working folder (```json work_path ```)

- the (complete) path for the folder containing the workflow (```json workflow_dir ```)

- the (complete) path for the folder containing the topo-bathymetric grids ```json bathy_dir ```)

- the script (with path) activating the software environment to run the steps on the computational nodes of the HPC cluster.

!!! example
    ```json
    {
    "work_path": "/work/user/ptha/test",
    "workflow_dir": "/home/user/cheese-ptha-master",
    "bathy_dir": "/work/user/ptha/bathy",
    "env_file": "/work/user/ptha/load_env.source" 
    }
    ```

!!! note ""
    STEPS

Each workflow step can be turned on/off by setting them as `True/False`, depending on whether they must be executed. It is worth noting that the output of each step is generally an input for the next one (except for <a href=../../workflow_steps/step4 target="_blank">STEP 4</a>, whose output is required by <a href=../../workflow_steps/step6 target="_blank">STEP 6</a>, while <a href=../../workflow_steps/step5 target="_blank">STEP 5</a> needs <a href=../../workflow_steps/step3 target="_blank">STEP 3</a>). For example, only <a href=../../workflow_steps/step2 target="_blank">STEP 2</a> would be executed with the following setup, provided that <a href=../../workflow_steps/step1 target="_blank">STEP 1</a> has been previously done. 

!!! example
    ```json
    {
    "step1":    False,
    "step2":    True,
    "step3":    False,
    "step4":    False,
    "step5":    False,
    "step6":    False,
    "step7":    False
    }
    ```

!!! note ""
    POI_SELECTION

Given the target site, the closest Points of Interest (POIs) are selected from the regional hazard model <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> in <a href=../../workflow_steps/step1 target="_blank">STEP 1</a>, and then used in the analysis. First of all, the geographic area of the target site must be declared, choosing among Mediterranean Sea ("med"), North-East Atlantic Ocean ("nea"), or Black Sea ("black"). It is worth noting that the workflow is automatized only for target sites overlooking the Mediterranean Sea, while some manual operations are required when dealing with the other regions. Then, in the Mediterranean Sea three different strategies are possible to select the POI(s), prioritized as follows: 

1. if the high-resolution grid for the target site is available (and stored in the declared folder `bathy_dir`) its domain can be used to draw a rectangular region containing the coastline of interest, and the POIs included in that region are selected;

2. if the coordinates of the target site are given, they are used to build the rectangle and search for the POIs within it;

3. if none of the previous options are provided, the label(s) of the POI(s) from <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> must be directly indicated, as in the following example:

!!! example
    ```json
    {
    "domain": "med",
    "grdfile": " ",
    "lonlat": " ",
    "poinames": "med07706,med07712"
    }
    ```
The last option is mandatory outside the Mediterranean Sea.


!!! note ""
    REGIONAL MODEL

The default regional model is <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a>, and the related files are expected to be stored in a folder named "TSUMAPS1.x" depending on the version. Version 1.0 must be used for managing sites outside the Mediterranean Sea, while for the Mediterranean area an updated vesion 1.1 is available. The path in the example is referred to the cluster mercalli @INGV.

!!! example
    ```json
    {
    "folderMain": "/scratch/projects/cat/SPTHA/",
    "project_name": "TSUMAPS1.1"
    }
    ```

!!! note ""
    DISAGGREGATION

When a <a href=../../workflow_steps/disaggregation target="_blank"> disaggregation </a> procedure is required to select relevant scenarios for the target site, some parameters must be defined such as:

- the choice between a disaggregation on MIH (Maximum Inundation Height) intervals (i) or thresholds (t);

- in case of intervals, the MIH interval(s), expressed in m, where the disaggregation must be executed (it can be a single interval, e.g. 1-4, or a sequence of intervals, e.g. 1-4,4-8);

- in case of thresholds, the MIH value(s), expressed in m, where the disaggregation must be executed (it can be one or more values separated by comma, e.g. 1,4);

- the desired percentage of hazard reproduction for each interval/threshold.

For example, the following settings will select the scenarios by disaggregating the hazard to account for 90% of the total at 1 m and 4 m:

!!! example
    ```json
    {
    "disaggregation": True,
    "type": "t",
    "mih_int": " ",
    "mih_val": "1,4",
    "threshold": "90"
    }
    ```

!!! note ""
    SAMPLING

An alternative/complementary method for scenario selection is the <a href="../../workflow_steps/ampling" target="_blank"> importance sampling </a>.

???+ warning
    The  <a href=../../workflow_steps/sampling target="_blank"> importance sampling </a> has not been implemented yet, so it must be set as False

    ```plaintext
    {
    "sampling": False
    }
    ```

!!! note ""
    SIMULATION SETUP

Some parameters for the  <a href=../../workflow_steps/step5 target="_blank">tsunami simulations</a> must be defined, such as: 

- the number of levels of nested grids;

- an array defining the refinement ratio of the nesting from the coarsest to the finest grid (it is worth noting that with the simulation code <a href=../../background/Tsunami-HySEA target="_blank">Tsunami-HySEA</a>, a refinement ratio equal to a power of 2 is mandatory);

- the simulation length expressed in hours.

For example, if the simulations are carried out for 4 hours on a grid setup made of an outer grid spanning a regional domain at a resolution of 320 m, and 4 local-scale telescopic grids with increasing resolution equal to 160, 80, 20, and 5 m respectively, this section would be:


!!! example
    ```json
    {
    "nlevels": 5,
    "ref_ratio": [2, 2, 4, 4],
    "propagation": 4
    }
    ```

!!! note ""
    HAZARD

The <a href=../../workflow_steps/step6 target="_blank"> hazard aggregation </a> is implemented both in Python and MATLAB, and the user can choose the preferred language, also depending on the software installed on the cluster where the workflow is running. 

Moreover, this step is parallelized on the domain, through a horizontal decomposition of the highest resolution grid in "slices", which are then processed in parallel. The number of slices (i.e. the number of parallel processes) is computed at runtime, but the maximum allowed number must be declared here, as a trade-off between parallelism and manageability. 

Two additional parameters are

- the desired forecast time window, i.e the time period for which the probability of exceedance must be computed (a typical value is 50 years)
- a logical variable allowing to possibly write the hazard curves as a CSV table. 

For example:

!!! example
    ```json
    {
    "haz_code": "python",
    "nmaxslices": "20",
    "forecast_time": "50",
    "write_csv": True
    }
    ```

!!! note ""
    MAPS

The last step of the workflow is the <a href=../../workflow_steps/step6 target="_blank">visualization</a>, namely the production of hazard maps. The required parameter is the average return period(s) expressed in years (it can be one or more values separated by comma). For example:

!!! example
    ```json
    {
    "return_period": "2500,25000,250000,1000000"
    }
    ```

!!! note ""
    HPC

This section refers to the HPC cluster. In the present version, the entire execution of the workflow is performed on the same cluster, which is retrieved at runtime by a specific Python functionality. As a consequence, there is no need to fill out this section, unless the workflow is running on Leonardo @CINECA: in this case, the last 3 keys must be completed to be authorized to run by the job scheduler:

!!! example
    ```json
    {
    "cluster": " ",
    "username": " ",
    "leonardo_account": "test_account",
    "leonardo_partition": "boost_usr_prod",
    "leonardo_quality": "normal"
    
    ```

???+ warning
    Future versions will possibly allow to execute the workflow on a local cluster and then connect to a remote cluster for running the tsunami simulation, provided that values corresponding to the keys "cluster" and "username" are provided.

