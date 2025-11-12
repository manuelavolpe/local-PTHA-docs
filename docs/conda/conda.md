# **Setting a conda environment**

As an alternative to the <a href="../../spack/env_spack" target="_blank">Spack</a> package manager, here we provide a brief tutorial on how to install and create a dedicated conda environment. This can be a valid alternative in particular for the <a href="../../instruction/install">Mercalli cluster</a> hosted at the INGV. 


## **Installation**

The user can install conda in hes/his own personal user account. 
The following commands will allow to download and install miniconda anywhere in your account (suggested: /home/youraccount): 

```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```
and then
```
bash ~/Miniconda3-latest-Linux-x86_64.sh
```

After these two operations, please close and re-open terminal, or type the following command:

```
source ~/.bashrc
```

However, for further details about the installation procedure, please refer to <a href="https://www.anaconda.com/docs/getting-started/miniconda/install#linux-terminal-installer" target="_blank">this page</a> and follow the instruction for the Linux operating system.


## **Creation and activation of the environment**

Now, you can create the environment by using the specific requirements file available in the workflow project.
Open the terminal and move to the main folder of the project (where you cloned or dowloaded it from the gitlab repository) and type:

```
conda create --name pyptha_local --file requirements_conda.txt
```

The output will show you the progress of the download and the installation of all the necessary packages, ending with a message of succeeding and instructions on how to activate/deactivate the new environment.
Following these instructions, you can activate the environment by typing:

```
conda activate pyptha_local
```

Your prompt should now indicate that the environment is active as follow:

```
(pyptha_local) [tonini@mercalli cheese-ptha]$
```

Now you will be able to use the workflow.

???+ Note
	If the above instruction should not work or if you prefer creating manually creating the environment, the following commands should be enough for creating a new environment with all the necessary packages to run the local ptha workflow.

	```
	conda create --name pyptha_local  python=3.11.11
	conda install numpy matplotlib scipy geopy pyproj netcdf4 xarray cartopy fabric basemap scikit-learn h5py
	```
    
    IMPORTANT: it is strongly suggested to use python 3.11.11 and installing the other packages letting that conda found the correct version for all of them. This is needed in order to avoid problems with the operating system libraries compatibility. 

