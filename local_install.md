# Local Setup instructions

- We recommend installing [**conda**](https://conda.io/en/latest/), an open source package management system and environment management system that runs on Windows, macOS and Linux.

- Download and install conda:

```bash
curl -O -L https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```
> Say “yes” to everything the installer asks, and accept default locations by pressing enter when it says “Miniconda3 will now be installed into this location”. (If the prompt looks like this “>>>”, then you are still within the installation process.)

- When the installation is complete and the regular prompt returns, run the following command (or start a new terminal session) in order to activate the conda environment:

```bash
source ~/.bashrc
```
- Next, enable various “channels” for software install, including bioconda:

```bash
conda config --add channels defaults
conda config --add channels conda-forge
conda config --add channels bioconda
```

- Next, download conda 'environment.yml' file, designed for this tutorial [here](https://github.com/sateeshperi/snakemake2019/blob/master/binder/environment.yml)

- Install tools in a new conda environment 'smake' using downloaded environment file

```bash
conda env create --file environment.yml -n smake
```
+ To activate the environment for tutorial
```bash
conda activate smake
```
- To deactivate environment after use
```bash
conda deactivate
```

- Singularity installation needs *sudo* permissions and instructions can be found [here](https://www.sylabs.io/guides/3.0/user-guide/quick_start.html#quick-installation-steps)
