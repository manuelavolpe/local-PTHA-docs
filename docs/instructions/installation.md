# **Installation**

The present version of the workflow requires the entire execution is carried out on the same (HPC) cluster, which must be equipped with GPUs in order to be able to run the tsunami simulations. 
Here is a table of the presently available clusters:

| INSTITUTE | CLUSTER |
|----------|------------|
| INGV | Mercalli |
| CINECA | Leonardo |

The hosting institute will provide instructions on how to connect to the cluster.

???+ Note
    Before installing, check that the software and data <a href=../requirements target="_blank">requirements</a> are satisfied.

Then, follow these instructions:

1. download the package from the master branch of the  <a href=https://gitlab.rm.ingv.it/cat/cheese-ptha target="_blank"> gitLab repository </a>  using the "Code" <a href=../../others/how-to-download target="_blank">button</a> on the top-right of the repository homepage and choosing the preferred compression format;

    ???+ warning
        The <a href=https://gitlab.rm.ingv.it/cat/cheese-ptha target="_blank"> gitLab repository </a>is private and can be accessed only by members. If you are not a member, please <a href="mailto:manuela.volpe@ingv.it" target="_blank">contact us</a>.

1. connect to the cluster and transfer the package to the preferred folder (hereinafter referred to as `/path-to-software/`);

1. unpack the archive: a folder `cheese-ptha-master` will be created, whose structure is illustrated in this [diagram](../images/folder_structure.png);

1. create/choose a working folder for IO (hereinafter referred to as `/path-to-wdir/`), possibly outside the workflow folder `cheese-ptha-master`, where all the outputs will be saved;

1. copy and rename the provided template for input files to your preferred location, for example in your working folder (but other locations can be chosen as well):

   ```bash
   foo@bar:$ cp /path-to-software/cheese-ptha-master/templates/workflow_input.json.template /path-to-wdir/workflow_input.json
   foo@bar:$ cp /path-to-software/cheese-ptha-master/templates/load_env.source.template /path-to-wdir/load_env.source
   ```

   Instructions on how to fill out the JSON file are provided on the dedicated <a href=../json_input target="_blank">page</a>, while the `load_env.source` file should be modified according to the preferred package and environment management system. We suggest <a href=../../spack/env_spack target="_blank">Spack</a> to build and configure the software environment, but a different package manager (e.g. conda) can be also used.

1. unpack the initial conditions for PS seismicity (see <a href=../../background/neamthm18 target="_blank">NEAMTHM18</a> for details) by typing:

   ```bash
   foo@bar:$ cd /path-to-software/cheese-ptha-master/inputs/SUBDUCTIONS_from_NEAMTHM18
   foo@bar:$ bunzip2 INIT_COND_PS.tar.bz2
   foo@bar:$ tar -xvf INIT_COND_PS.tar
   ```

   This operation can take a while and can be skipped at the beginning, but must be executed before running <a href=../../workflow_steps/step4 target="_blank">STEP 4</a> of the workflow.

   In case of target sites located along the North-Eastern Atlantic coast, outside the Mediterranean Sea, the same unpacking process must be carried out for the initial conditions of sources belonging to the Mid Atlantic Ridge and to the Caribbean arc:

   ```bash
   foo@bar:$ cd /path-to-software/cheese-ptha-master/inputs/MidAtlantic_from_NEAMTHM18 
   foo@bar:$ bunzip2 INIT_COND_PSMar.tar.bz2
   foo@bar:$ tar -xvf INIT_COND_PSMar.tar
   
   foo@bar:$ cd /path-to-software/cheese-ptha-master/inputs/Caribbean_from_NEAMTHM18 
   foo@bar:$ bunzip2 INIT_COND_PSSlip.tar.bz2
   foo@bar:$ tar -xvf INIT_COND_PSSlip.tar
   ```

1. create/choose a folder for the topo-bathimetric <a href=../../background/nested_grids target="_blank">grid files</a> (`/path-to-grids/`). Having this folder, and the grid files inside it, is not mandatory until the tsunami simulations are executed (<a href=../../workflow_steps/step5 target="_blank">STEP 5</a>), although the highest resolution grid can be optionally used for the selection of the Point(s) of Interest (POIs) in <a href=../../workflow_steps/step4 target="_blank">STEP 1</a>.
