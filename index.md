Intro to Workflows for Efficient Automated Data Analysis, using Snakemake
===
![logo](/img/smake_logo.png)

The Snakemake workflow management system is a tool to create reproducible and scalable data analyses. Workflows are described via a human readable, Python based language. They can be seamlessly scaled to server, cluster, grid and cloud environments, without the need to modify the workflow definition. Finally, Snakemake workflows can entail a description of required software, which will be automatically deployed to any execution environment.

>  You don't need to be an expert at Python to use Snakemake, but it can sometimes be very useful.

> No license; the below content is availalbe under CC0 general license.


### Author:
> [Sateesh Peri](https://twitter.com/perisateesh)

### Credits
The content for this website has been compiled from tutorials put together by:
+ [Titus Brown](https://twitter.com/ctitusbrown) - Link to [Tutorial](https://github.com/ctb/2019-snakemake-ucdavis)

+ [Johannes Koster](https://twitter.com/johanneskoester) - Link to [Tutorial](https://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html)

+ [CyVerse](https://user.cyverse.org/)

# Setup

This tutorial uses
	+ [**conda**](https://conda.io/en/latest/) for Environment Management
		+ [**bioconda**](https://bioconda.github.io/) Channel for packages
			+ [**fastqc**](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)
			+ [**trimmomatic**](http://www.usadellab.org/cms/?page=trimmomatic)
			+ [**multiqc**](https://multiqc.info/)
	+ [**Snakemake**](https://snakemake.readthedocs.io/en/stable/) for Workflow Management
    + [**Singularity**](https://www.sylabs.io/docs/) for Container Management

## Working on Binder

We're going to use [mybinder.org](https://mybinder.org/) , a fantastic service that lets us run demonstrations and short workshops in the cloud! 

> **Click on this [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/sateeshperi/snakemake2019.git/binder?urlpath=rstudio) button to launch a pre-configured Binder file that is rendered via a Rstudio interface.**

- The binder is built using this 'conda' [environment.yml](https://github.com/sateeshperi/snakemake2019/blob/master/binder/environment.yml).

> No support for '--use-singularity'

## Working on Cloud

To run snakemake jobs via Singularity/Docker containers in the cloud, we are going to use [**CyVerse Atmosphere**](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html) 

> Support for 'snakemake --use-singularity'
> >Support running Singularity (shub://) & Docker (docker://) containers

## Custom Install

We recommend [**conda**](https://conda.io/en/latest/), an open source package management system and environment management system that runs on Windows, macOS and Linux. 

Download conda [environment.yml](https://github.com/sateeshperi/snakemake2019/blob/master/binder/environment.yml) file, designed for this tutorial

Install tools in a new conda environment 'smake' using downloaded file

```
conda env create --file environment.yml -n smake
```
To activate the environment for tutorial
```
conda activate smake
```
TO deactivate environment after use
```
conda deactivate
```

Singularity installation needs 'sudo' rights and instructions can be found [here](https://www.sylabs.io/guides/3.0/user-guide/installation.html#installation)

> Singularity modules in HPCs

# [Introduction](https://snakemake2019.readthedocs.io/en/latest/introduction.html)

# [Basic Tutorial](https://snakemake2019.readthedocs.io/en/latest/basic_tutorial.html)

# [Atmosphere Cloud](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html)

# [Container Tutorial](https://snakemake2019.readthedocs.io/en/latest/container_tutorial.html)

# [Awesome](https://snakemake2019.readthedocs.io/en/latest/awesome.html)