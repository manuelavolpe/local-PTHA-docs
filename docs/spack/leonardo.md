# **Instructions for Leonardo**

On leonardo @CINECA, Spack is already installed as a module, and the user just has to load it and then create and configure the environment:

1. load Spack:

    ```bash
    foo@bar:$ module load spack/0.19.1-d71
    ```

1. move to the desired folder and create and activate the environment with the following commands:

    ```bash
    foo@bar:$ cd /path-to-folder/
    foo@bar:$ spack env create -d spack_env_name
    foo@bar:$ spack env activate [-p] spack_env_name
    ```

    Note that the `-d` option will create the environment in the current folder, typically the `home` folder but can be a dedicated one [^footnote1]. The environment can be activated from any folder by adding the complete path to the command. The `-p` is just a flag to visualize the environment is active.

1. add Python and py-pip to the environment and install them

    ```bash
    foo@bar:$ spack add python py-pip
    foo@bar:$ spack -d install
    ```

    In this way, the (last) preferred version of Python will be installed. You can do `spack find` to see which packages have been installed.

    ???+ Tip
        In case you want to install a specific Python version, you can search and choose the preferred version through the commands
        ```bash
        foo@bar:$ spack info python
        foo@bar:$ spack add python@version
        ```

1. install Python packages needed to run the workflow in the environment

    ```bash
    foo@bar:$ pip install -r /path-to-software/cheese-ptha-master/requirements.txt
    ```

    The file `requirements.txt` is provided with the workflow. As an alternative, each Python package can be individually installed by the command `pip install package_name`.

    ???+ warning
        You could get the error `ModuleNotFoundError: No module named 'pip'`. If this is the case, you have to load py-pip before installing the Python packages
        ```bash
        foo@bar:$ spack load py-pip
        ```

The environment is ready. For any new session, of course, it must be activated by the commands

```bash
foo@bar:$ module load spack/0.19.1-d71
foo@bar:$ spack env activate [-p] ~/spack_env_name
```

**The same two lines should be inserted within the file `load_env.source`** (see the <a href=../../instructions/installation target="_blank"> installation instructions</a>).

[^footnote1]: Omitting such a flag is not allowed on Leonardo since the standard user does not have writing permission on the default Spack folder.
