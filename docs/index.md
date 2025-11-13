<base target="_blank">

# **Welcome to Local PTHA WaaS documentation**

Here is the documentation concerning the local Probabilistic Tsunami Hazard Analysis (PTHA) Workflow as a Service (WaaS).

The workflow aims at computing PTHA at a local scale for a given target site, starting from a regional hazard model, presently <a href=background/neamthm18 target="_blank">NEAMTHM18</a>, that is the long-term hazard model for the NEAM region (North-East Atlantic, Mediterranean and connected seas). One target site is allowed for the moment, future upgrades will allow processing more than one.

The execution, graphically represented by a block [diagram](images/PTHA_wf_diagram.drawio.png), is subdivided into 7 sequential steps, which are briefly described <a href=steps/overview target="_blank">here</a>.

The tsunami simulations are carried out exploiting the numerical GPU code Tsunami-HySEA. The present version requires the entire execution of the workflow on the same HPC cluster equipped with GPUs; future versions will allow sending the simulations to a remote cluster (equipped with GPUs), while executing all the other steps on a local cluster.

???+ info
    Some background details about local PTHA can be found <a href=background/l-ptha target="_blank">here</a>.

???+ warning
    Presently, the use of the following clusters is implemented:

        - Mercalli @INGV (job manager: PBS) 
        - Leonardo @CINECA (job manager: SLURM)
    More clusters could be added in the future.

## **Content**

- <a href=instructions/installation target="_blank">Installation Instructions</a>

- <a href=instructions/usage target="_blank">Usage Instructions</a>

- <a href=steps/overview target="_blank">Workflow description</a>
