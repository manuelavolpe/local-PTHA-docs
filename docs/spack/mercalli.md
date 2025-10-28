# **Instructions for Mercalli**

On mercalli @INGV Spack is not installed, and the user has to do it locally in his/her own area.

Moreover, since Python 2.7 is in use by default, while a version >3.6 is required by Spack, a preliminary step must be executed to force Spack to use Python >3.6, in order to avoid getting this error message `Spack requires Python 3.6 or higher You are running spack with Python 2.7.5`.

0. add the following line to your `~/.bashrc` file:
    ```
    export SPACK_PYTHON=/soft/centos7/anaconda/2023.03/bin/python
    ```

1. in your home directory, run the following commands to download and configure Spack:
    ```
    git clone -c feature.manyFiles=true https://github.com/spack/spack.git
    . spack/share/spack/setup-env.sh
    ```

    ???+ tip
        To avoid running the same command every time you open a new terminal, you might want to add this line to your `~/.bashrc` file:
        ```
        . ~/spack/share/spack/setup-env.sh
        ```

1. create and activate the environment with the following commands:
    ```
    spack env create -d spack_env_name
    spack env activate [-p] ~/spack_env_name
    ```

    Note that the `-d` option will create the environment in the current folder (typically the `home` folder but can be a dedicated one), while omitting it will result in creating the environment in the default folder (`~/spack/var/spack/environments/`). The `-p` is just a flag to visualize the environment is active.

1. add Python and py-pip to the environment and install them
    ```
    spack add python py-pip
    spack -d install
    ```
    
    In this way, the (last) preferred version of Python will be installed. You can do `spack find` to see which packages have been installed.
    ???+ Tip
        In case you want to install a specific Python version, you can search and choose the preferred version through the commands
        ```
        spack info python
        spack add python@version
        ```

1. install Python packages needed to run the workflow in the environment
    ```
    pip install -r /path-to-software/cheese-ptha-master/requirements.txt
    ```

    The file `requirements.txt` is provided with the workflow.

    ???+ warning
        You could get the error `ModuleNotFoundError: No module named 'pip'`. If this is the case, you have to load py-pip before installing the Python packages
        ```
        spack load py-pip
        ```

The environment is ready. For any new session, of course, it must be activated by the command
```
spack env activate [-p] ~/spack_env_name
```

**The same line should be inserted within the file `load_env.source`** (see the <a href=../../instructions/installation target="_blank"> installation instructions</a>).
