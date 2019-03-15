Reproducible Workflows using Snakemake and Singularity
===
![logo](/img/tutorial_logo.png)

- **The Snakemake workflow management system is a tool to create reproducible and scalable data analyses.**

- **Workflows are described via a human readable, Python based language. They can be seamlessly scaled to server, cluster, grid and cloud environments, without the need to modify the workflow definition.**

- **Snakemake workflows can entail a description of required software, which will be automatically deployed to any execution environment.**

> Basic UNIX command-line experience required.

> You don't need to be an expert at Python to use Snakemake, but it can sometimes be very useful.

> No license; the below content is available under CC0 general license.

### Author:
> [Sateesh Peri](https://twitter.com/perisateesh)

### Credits
The content for this website has been compiled from tutorials put together by:

+ [Titus Brown](https://twitter.com/ctitusbrown) - Link to [Tutorial](https://github.com/ctb/2019-snakemake-ucdavis)

+ [Johannes Koster](https://twitter.com/johanneskoester) - Link to [Tutorial](https://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html)

+ [CyVerse](https://www.cyverse.org/about)

# Learning Objectives

	+ Understand snakemake syntax
	+ Understand the idea of containers
	+

- This tutorial is designed to introduce 'building reproducible workflows' using:
	+ [**conda**](https://conda.io/en/latest/) and [**bioconda**](https://bioconda.github.io/) for **Environment Management**

	+ [**Snakemake**](https://snakemake.readthedocs.io/en/stable/) for **Workflow Management**

	+ [**Singularity**](https://www.sylabs.io/docs/) for **Container Management**

# [Introduction](https://snakemake2019.readthedocs.io/en/latest/introduction.html)

# Working on Binder

> Note:  No support for '--use-singularity'

- We're going to use [mybinder.org](https://mybinder.org/), a fantastic service that lets us run demonstrations and short workshops in the cloud! 

> **Click on this [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/sateeshperi/snakemake2019.git/binder?urlpath=rstudio) button to launch a pre-configured Binder file that is rendered via a Rstudio interface.**

- The binder is built using this 'conda' [environment.yml](https://github.com/sateeshperi/snakemake2019/blob/master/binder/environment.yml).

> [**Basic Tutorial using Binder**](https://snakemake2019.readthedocs.io/en/latest/basic_tutorial.html)

# Working on Cloud

> Support for '--use-singularity' (shub://) & (docker://) containers

- To run snakemake jobs via [Singularity]() / [Docker]() containers in the cloud, we recommend [**Atmosphere**](https://www.cyverse.org/atmosphere), CyVerse's cloud-computing platform which provides easy-to-use web-access to cloud resources and is designed to accommodate computationally and data-intensive tasks.

> [**1. Register for a free account on CyVerse**](https://user.cyverse.org/register)

> [**2. Guide to Launching Atmosphere Instances**](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html)

> [**3. Container Tutorial using Atmosphere**](https://snakemake2019.readthedocs.io/en/latest/container_tutorial.html)

- *Atmosphere Key Features:*

	+ Access virtual machine images preconfigured with an operating system and software to help you do scientific computations in domain-specific tasks

	+ Find and use tools with the intuitive self-service portal

	+ Easily manage virtual machines

	+ Publish your own software suites, create your own work environments, and run the software for community use

	+ Access your data in the Data Store, including high-performance computing (HPC) and grid computing environments

	+ Integrate with existing infrastructure components using API services

	+ Easily generate and manage statistical reporting of user resources for total CPU hours and memory usages, total instances and applications launched by user, cloud monitoring, and on-demand intelligence resource allocation

> **[**CyVerse**](https://www.cyverse.org/about) is a cyber-infrastructure initiative funded by the National Science Foundation’s Directorate for Biological Sciences to address the growing needs for highly configurable and customized computational infrastructure to support research efforts in data sciences.**

# Custom Install

> We recommend [**conda**](https://conda.io/en/latest/), an open source package management system and environment management system that runs on Windows, macOS and Linux.

- Download and install conda:

```
curl -O -L https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```
> Say “yes” to everything the installer asks, and accept default locations by pressing enter when it says “Miniconda3 will now be installed into this location”. (If the prompt looks like this “>>>”, then you are still within the installation process.)

- When the installation is complete and the regular prompt returns, run the following command (or start a new terminal session) in order to activate the conda environment:

```
source ~/.bashrc
```
- Next, enable various “channels” for software install, including bioconda:

```
conda config --add channels defaults
conda config --add channels conda-forge
conda config --add channels bioconda
```

- Next, download conda 'environment.yml' file, designed for this tutorial [here](https://github.com/sateeshperi/snakemake2019/blob/master/binder/environment.yml)

- Install tools in a new conda environment 'smake' using downloaded environemnt file

```
conda env create --file environment.yml -n smake
```

- To activate the environment for tutorial
```
conda activate smake
```

- To deactivate environment after use
```
conda deactivate
```
> To run jobs in containers:

- Singularity installation needs **sudo** permissions and instructions can be found [here](https://www.sylabs.io/guides/3.0/user-guide/installation.html#installation)

> Singularity modules in HPCs


# [Awesome](https://snakemake2019.readthedocs.io/en/latest/awesome.html)