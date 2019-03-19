Reproducible Workflows using Snakemake and Singularity
===

 ![](/img/logos/rep_research_logo.png)
> **The Snakemake workflow management system is a tool to create reproducible and scalable data analyses and can be seamlessly scaled to server, cluster, grid and cloud environments, without the need to modify the workflow definition.**

> **Singularity is an open source-based container platform designed for scientific and high-performance computing (HPC) environments. Singularity supports Bring Your Own Environment (BYOE)—where entire Singularity environments can be transported between computational resources (e.g., users’ PCs) with reproducibility.**

+ Basic [**UNIX command-line**](http://linuxcommand.org/lc3_learning_the_shell.php) experience required. [Bootcamp](http://rik.smith-unna.com/command_line_bootcamp/?id=6oprpl4mlf4)
+ You don't need to be an expert at Python to use Snakemake, but it can sometimes be very useful.

> No license; the below content is available under CC0 general license.

> Author: [Sateesh Peri](https://twitter.com/perisateesh)

# Learning Objectives

-	**Workflow Management** using [**Snakemake**](https://snakemake.readthedocs.io/en/stable/)
 + Move from separate scripts to connected analysis
 + Understand snakemake syntax                                                   
 + Understand the components of a Snakefile: rules, inputs, outputs, and actions
 + Understand snakemake wildcards and pattern rules                              
 + Understand how snakemake manages dependencies and outputs


-	**Environment Management** using [**conda**](https://conda.io/en/latest/) & [**bioconda**](https://bioconda.github.io/)
 + Set up and manage the project environment        
 + Understand conda environments


- **Container Management** using [**Singularity**](https://www.sylabs.io/docs/)
 + Make your project self-sustainable and distributable
 + Understand what containers are                                                
 + Understand what Dockers are                                                   
 + Understand why Singularity                                                    
 + How to pull & run singularity containers                                      


- **Cloud Computing**
 + Launch and work on remote instances (virtual machines) with pre-built images
 + Understand advantages / disadvantages of cloud computing
 +

# Introduction

> [**What...Why...How???**](https://snakemake2019.readthedocs.io/en/latest/introduction.html)

# Snakemake Intro Tutorial using Binder

- **Note:**
  + No setup necessary
  + Does not support 'Singularity' container execution

> **Click on this [![](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/sateeshperi/snakemake2019.git/binder?urlpath=rstudio) button to launch a Binder rendered as Rstudio interface pre-configured with conda and Snakemake.**

- [MyBinder](https://mybinder.org/) is a fantastic service that lets us run demonstrations and short workshops in the cloud!
- The binder is built using this 'conda' [environment.yml](https://github.com/sateeshperi/snakemake2019/blob/master/binder/environment.yml).

> [**Click here for Introductory Snakemake Tutorial using Binder**](https://snakemake2019.readthedocs.io/en/latest/smake_basic_tutorial.html)

# Snakemake Tutorial on Cyverse Cloud

> **Note:**
  + Requires access to [CyVerse Atmosphere]()
  + Supports 'Singularity' container execution

![](/img/cloud_computing.png)

> [**Click here for a guided tutorial on Running Snakemake jobs using Singularity Containers in Atmosphere**](https://snakemake2019.readthedocs.io/en/latest/smake_cyverse.html)

## Tutorial on Jetstream cloud

# Working Locally

> **Click [here](https://snakemake2019.readthedocs.io/en/latest/local_install.html) for local setup instructions.**
> > Requires Administrator privileges 

# Awesome

+ [Awesome list of Snakemake & Singularity resources](https://snakemake2019.readthedocs.io/en/latest/awesome.html)

# Credits

The content for this website has been compiled from tutorials put together by:

+ [Titus Brown](https://twitter.com/ctitusbrown) - Link to [Tutorial](https://github.com/ctb/2019-snakemake-ucdavis)

+ [Johannes Koster](https://twitter.com/johanneskoester) - Link to [Tutorial](https://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html)

+ [CyVerse](https://www.cyverse.org/about) - Link to [Container Camp](https://cyverse-container-camp-workshop-2019.readthedocs-hosted.com/en/latest/index.html)

> Please report new issues in [GitHub](https://github.com/sateeshperi/snakemake2019/issues)

# Coming Soon

+ Singularity modules in HPCs
+ Building containers from scratch

 ![](/img/logos/minion.png)
+ Version Control
+ Markdown
+ Did someone say *Kubernetes* !!!
