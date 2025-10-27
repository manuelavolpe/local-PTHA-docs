# **Requirements**

The following **software** is required: 

* Bash shell
* Preferred package manager (suggested: <a href=../../spack/env_spack target="_blank"> Spack</a>)
* Python3.x
* <a href=../../background/Tsunami-HySEA target="_blank">Tsunami-HySEA</a> code (MC version)

Optional software:

* MATLAB

The required input **data** are:

* input <a href=../json_input target="_blank">file</a> `workflow_input.json` in JSON format, containing all the settings and parameters: a template for such file is provided with the workflow (see  <a href=../installation target="_blank">installation instructions</a>);

* input file `load_env.source`, containing commands to activate the software virtual environment: a template for such file is provided with the workflow (see  <a href=../installation target="_blank">installation instructions</a>); 

* local telescopic grids + outer grid level at regional scale: a set of files, suitably formatted for the <a href=../../background/Tsunami-HySEA target="_blank">T-HySEA</a> code (netCDF format with extension .grd), named `SITENAME_grid-1.grd`, `SITENAME_grid1.grd` etc., from the coarsest to the finest resolution (<a href=../grids target="_blank">more details</a>). All these files must be located in the folder specified in the <a href=../json_input target="_blank">JSON input file</a> (`/path-to-grids/`) and must be available before running the tsunami simulations (<a href=../../workflow_steps/step5 target="_blank">STEP 5</a>); the finest grid, if available, can also be used to retrieve the Point of Interest (POI) closest to the target site from <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a>, but other strategies are possible (<a href=../../workflow_steps/step1 target="_blank">STEP 1</a>).

* regional hazard model for locations, mechanisms, sizes, and probabilities of occurrence of earthquake sources (here <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a>; v1.0 for target sites in the North-East Atlantic or Black Sea areas; v1.1 for target sites in the Mediterranean region); data are already available on the HPC clusters foreseen by the workflow;

???+ warning
    Presently, the use of v1.0 outside the Mediterranean Sea is not fully automatized and requires some manual operations.