# **Instructions for Mercalli**

On Mercalli @INGV Spack is not installed, and the user has to do it locally in his/her own area. To this aim, please follow the most updated instructions provided in the <a href=https://spack-tutorial.readthedocs.io/en/latest/tutorial_basics.html#  target="_blank"> official documentation </a>.

<!--this is a comment-->
<!--Moreover, since Python 2.7 is in use by default, while a version >3.6 is required by Spack, a preliminary step must be executed to force Spack to use Python >3.6, in order to avoid getting this error message `Spack requires Python 3.6 or higher You are running spack with Python 2.7.5`.

0. add the following line to your `~/.bashrc` file:
    ```
    export SPACK_PYTHON=/soft/centos7/anaconda/2023.03/bin/python
    ```

1. in your home directory, run the following commands to download and configure Spack:
    ```
    git clone -c feature.manyFiles=true https://github.com/spack/spack.git
    . spack/share/spack/setup-env.sh
    ```-->

???+ Tip
    To avoid running the same command every time you open a new terminal, you might want to add the following line to your `~/.bashrc` file:
    ```bash
    . ~/spack/share/spack/setup-env.sh
    ```

Once Spack is installed, the environment can be created and configured:

1. move to the desired folder and create and activate the environment with the following commands:

   ```bash
   foo@bar:~$ cd /path-to-folder/
   foo@bar:~$ spack env create -d spack_env_name
   foo@bar:~$ spack env activate [-p] spack_env_name
   ```

    Note that the `-d` option will create the environment in the current folder, while omitting it will result in creating the environment in the default folder (`~/spack/var/spack/environments/`). The environment can be activated from any folder by adding the complete path to the command. The `-p` is just a flag to visualize the environment is active.

1. add Python and py-pip to the environment and install them

   ```bash
   foo@bar:~$ spack add python py-pip
   foo@bar:~$ spack -d install
   ```

    In this way, the (last) preferred version of Python will be installed. You can do `spack find` to see which packages have been installed.

    ???+ Tip
        In case you want to install a specific Python version, you can search and choose the preferred version through the commands
        ```bash
        foo@bar:~$ spack info python
        foo@bar:~$ spack add python@version
        ```

1. install Python packages needed to run the workflow in the environment

   ```bash
   foo@bar:~$ pip install -r /path-to-software/cheese-ptha-master/requirements.txt
   ```

   The file `requirements.txt` is provided with the workflow.

The environment is ready. In case of problems, check the <a href=../../others/troubleshooting_spack target="_blank"> troubleshooting guide</a>. If the issue is not tracked there, please <a href="mailto:manuela.volpe@ingv.it" target="_blank"> notify</a>.

For any new session, of course, it must be activated by the command

```bash
foo@bar:~$ spack env activate [-p] /path-to-folder/spack_env_name
```

**The same line should be inserted within the file `load_env.source`** (see the <a href=../../instructions/installation target="_blank"> installation instructions</a>).
