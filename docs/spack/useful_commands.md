# **Useful Spack commands**

Below is a short list of some useful commands. For the complete list of Spack commands check the <a href=https://spack.readthedocs.io/en/latest/command_index.html target="_blank"> documentation</a> 

| Command                        |      Comment      |
|--------------------------------|---------------------------------------|
| `spack env create -d .`        | To create a new environment in the current folder |
| `spack env activate -p .`      | To activate an environment in the current folder |
| `spack env deactivate`         | To deactivate the environment |
| `spack list packagename`       | To see available packages that contain "packagename" on spack |
| `spack info packagename`       | To see which versions of a specific package are available |
| `spack add packagename`        | To add a new package (then do `spack concretize` and `spack install`) |
| `spack add packagename@x.x.x`  | To add a new package, where x.x.x defines a specific version  |
| `spack install`                | To install packages added to the environment |
| `spack load installed-package` | To load a previously installed package in the environment* |
| `spack find`                   | To see what packages are installed in the environment |
| `spack find --loaded`          | To see what packages are loaded in the environment |
| `spack find --paths`           | To see where packages are installed within the spack environment |
| `spack repo add /path/`        | To add a new repository (in addition to the default one from spack) |
