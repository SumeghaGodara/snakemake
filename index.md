Reproducible Workflows using Snakemake and Singularity
===
![logo](/img/logos/rep_research_logo.png)

> **The Snakemake workflow management system is a tool to create reproducible and scalable data analyses and can be seamlessly scaled to server, cluster, grid and cloud environments, without the need to modify the workflow definition.**

> **Singularity is an open source-based container platform designed for scientific and high-performance computing (HPC) environments. Singularity supports Bring Your Own Environment (BYOE)—where entire Singularity environments can be transported between computational resources (e.g., users’ PCs) with reproducibility.**

+ Basic [**UNIX command-line**](http://linuxcommand.org/lc3_learning_the_shell.php) experience required. [Bootcamp](http://rik.smith-unna.com/command_line_bootcamp/?id=6oprpl4mlf4)
+ You don't need to be an expert at Python to use Snakemake, but it can sometimes be very useful.

> No license; the below content is available under CC0 general license.

> Author: [Sateesh Peri](https://twitter.com/perisateesh)

# Learning Objectives

-	**Environment Management** using [**conda**](https://conda.io/en/latest/) & [**bioconda**](https://bioconda.github.io/)
 + Set up and manage the project environment        
 + Understand conda environments


-	**Workflow Management** using [**Snakemake**](https://snakemake.readthedocs.io/en/stable/)
 + Move from separate scripts to connected analysis
 + Understand snakemake syntax                                                   
 + Understand the components of a Snakefile: rules, inputs, outputs, and actions
 + Understand snakemake wildcards and pattern rules                              
 + Understand how snakemake manages dependencies and outputs


- **Container Management** using [**Singularity**](https://www.sylabs.io/docs/)
 + Make your project self-sustainable and distributable
 + Understand what containers are                                                
 + Understand what Dockers are                                                   
 + Understand why Singularity                                                    
 + How to pull & run singularity containers                                      

# Introduction

> [**What...Why...How???**](https://snakemake2019.readthedocs.io/en/latest/introduction.html)

# Working on Binder

> Note: No support for '--use-singularity'

- We're going to use [mybinder.org](https://mybinder.org/), a fantastic service that lets us run demonstrations and short workshops in the cloud!

> **Click on this [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/sateeshperi/snakemake2019.git/binder?urlpath=rstudio) button to launch a pre-configured Binder file that is rendered via a Rstudio interface.**

- The binder is built using this 'conda' [environment.yml](https://github.com/sateeshperi/snakemake2019/blob/master/binder/environment.yml).

> [**Snakemake Tutorial using Binder**](https://snakemake2019.readthedocs.io/en/latest/smake_basic_tutorial.html)

# Working on Cloud

 > **To run snakemake jobs via [Singularity](https://singularity-hub.org/) / [Docker](https://hub.docker.com/) containers in the cloud, we recommend [Atmosphere](https://www.cyverse.org/atmosphere), CyVerse's cloud-computing platform which provides easy-to-use web-access to cloud resources and is designed to accommodate computationally and data-intensive tasks.**

![cloud_computing](/img/cloud_computing.png)

> [**1. Register for a free account on CyVerse**](https://user.cyverse.org/register)

> [**2. Guide to Launching Atmosphere Instances**](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html)

> [**3. Snakemake Cloud Tutorial on Atmosphere**](https://snakemake2019.readthedocs.io/en/latest/smake_cloud_tutorial.html)

 **Atmosphere / Jetstream Key Features:**

+ Access virtual machine images pre-configured with an operating system and software to help you do scientific computations in domain-specific tasks
+ Find and use tools with the intuitive self-service portal
+ Easily manage virtual machines
+ Publish your own software suites, create your own work environments, and run the software for community use
+ Access your data in the Data Store, including high-performance computing (HPC) and grid computing environments
+ Integrate with existing infrastructure components using API services
+ Easily generate and manage statistical reporting of user resources for total CPU hours and memory usages, total instances and applications launched by user, cloud monitoring, and on-demand intelligence resource allocation

> [**CyVerse**](https://www.cyverse.org/about) is a cyber-infrastructure initiative funded by the National Science Foundation’s Directorate for Biological Sciences to address the growing needs for highly configurable and customized computational infrastructure to support research efforts in data sciences.

+ [CyVerse Allocations Guide]()

> [**Jetstream**](https://jetstream-cloud.org/) is an [NSF/XSEDE] resource designed to promote and provide configurable cyberinfrastructure in the form of cloud computing to both novice and experienced users. Jetstream features a web-based user interface based on the popular Atmosphere cloud computing environment developed by CyVerse.

> [**1. Register for an account on XSEDE User Portal**](https://portal.xsede.org/web/xup/my-xsede?p_p_id=58&p_p_lifecycle=0&p_p_state=maximized&p_p_mode=view&saveLastPath=0&_58_struts_action=%2Flogin%2Fcreate_account)

+ [Jetstream Allocations Guide](https://portal.xsede.org/my-xsede?p_p_state=maximized&p_p_mode=view&saveLastPath=0&_58_struts_action=%2Flogin%2Flogin&p_p_id=58&p_p_lifecycle=0&_58_redirect=%2Fgroup%2Fxup%2Fjetstream-rapid-access)

# Working Locally

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

# Awesome

+ [Awesome list of Snakemake & Singularity resources](https://snakemake2019.readthedocs.io/en/latest/awesome.html)

# Credits

The content for this website has been compiled from tutorials put together by:

+ [Titus Brown](https://twitter.com/ctitusbrown) - Link to [Tutorial](https://github.com/ctb/2019-snakemake-ucdavis)

+ [Johannes Koster](https://twitter.com/johanneskoester) - Link to [Tutorial](https://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html)

+ [CyVerse](https://www.cyverse.org/about) -Link to [Container Camp](https://cyverse-container-camp-workshop-2019.readthedocs-hosted.com/en/latest/index.html)

> Please report new issues in [GitHub](https://github.com/sateeshperi/snakemake2019/issues)

# Coming Soon
![singularity_bot](/img/logos/singularity_bot.png)
+ Singularity modules in HPCs
+ Building containers from scratch
+ Version Control
+ Markdown
+ Did someone say *Kubernetes* !!!
