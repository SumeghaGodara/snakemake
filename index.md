Intro to Workflows for Efficient Automated Data Analysis, using Snakemake
===
![logo](/img/smake_logo.png)

**Snakemake is designed specifically for computationally intensive and/or complex data analysis pipelines. The name is a reference to the programming language Python, which forms the basis for the Snakemake syntax.**
>  You don't need to be an expert at Python to use Snakemake, but it can sometimes be very useful.

```
No license; the below content is under CC0.
```
### Author:
> [Sateesh Peri](https://twitter.com/perisateesh)

### Credits
The content for this website has been compiled from tutorials put together by:
+ [Titus Brown](https://twitter.com/ctitusbrown) - [Link to Tutorial](https://github.com/ctb/2019-snakemake-ucdavis)

+ [Johannes Koster](https://twitter.com/johanneskoester) - [Link to Tutorial](https://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html)

# Setup

## Working on Binder

We're going to use [mybinder.org](https://mybinder.org/) , a fantastic service that lets us run demonstrations and short workshops in the cloud! 

> **Click on the button below to open a pre-configured Binder file that is rendered via a Rstudio interface.**

===> [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/sateeshperi/snakemake2019.git/master?urlpath=rstudio) <===

**We're mostly going to work in the file editor and the terminal; to get started, open the terminal, and execute:**

```
PS1='$ '
```
to get a shorter prompt.

## Working on Cloud

[**CyVerse Atmosphere**](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html)


### Software we're going to use

We're going to be using [**conda**](https://conda.io/en/latest/), [**snakemake**](https://snakemake.readthedocs.io/en/stable/), packages from [**bioconda**](https://bioconda.github.io/) and [**singularity**](https://www.sylabs.io/singularity/). If you wanted to run all of this on your own computer, you'll need to follow the bioconda install instructions.

We'll be implementing a short read quality check and trimming pipeline, using [**fastqc**](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/), [**trimmomatic**](http://www.usadellab.org/cms/?page=trimmomatic), and [**multiqc**](https://multiqc.info/).

**Note: Singularity installation needs 'sudo' rights and instructions can be found [here](https://www.sylabs.io/guides/3.0/user-guide/installation.html#installation)**

You can see the full set of installed software requirements [here](https://github.com/sateeshperi/snakemake2019/blob/master/binder/environment.yml), in a conda environment.yml file.

You could use this install file to run everything we're doing today on your laptop, with:

```
conda env create --file environment.yml -n smake
conda activate smake
```
# [**Introduction**](https://snakemake2019.readthedocs.io/en/latest/introduction.html)

# [**Basic Tutorial**](https://snakemake2019.readthedocs.io/en/latest/basic_tutorial.html)

# [**Container Tutorial**](https://snakemake2019.readthedocs.io/en/latest/container_tutorial.html)

# [**Awesome**](https://snakemake2019.readthedocs.io/en/latest/awesome.html)