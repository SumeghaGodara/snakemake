Intro to Workflows for Efficient Automated Data Analysis, using Snakemake
===
![logo](/img/smake_logo.png)

# Authors:
> [C. Titus Brown](titus@idyll.org)

> [Sateesh Peri](https://sateeshperi.github.io/)

```
No license; the below content is under CC0.
```

In this breakout session you'll learn about [snakemake](https://snakemake.readthedocs.io/en/stable/), a workflow management system consisting of a text-based workflow specification language and a scalable execution environment. You will be introduced to the Snakemake workflow definition language and how to use the execution environment to scale workflows to compute servers and clusters while adapting to hardware specific constraints. 

Snakemake is designed specifically for computationally intensive and/or complex data analysis pipelines. The name is a reference to the programming language Python, which forms the basis for the Snakemake syntax. 
>  You don't need to be an expert at Python to use Snakemake, but it can sometimes be very useful.

# Setup

**Working on binder**

We're going to use [mybinder.org](https://mybinder.org/) , a fantastic service that lets us run demonstrations and short workshops in the cloud! 

> **Click on the button below to open a pre-configured Binder file that is rendered via a Rstudio interface.**


----------> [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/sateeshperi/snakemake2019.git/master?urlpath=rstudio) <-----------


### Software we're going to use

We're going to be using [conda](https://conda.io/en/latest/) and [snakemake](https://snakemake.readthedocs.io/en/stable/), a well as packages from [bioconda](https://bioconda.github.io/). If you wanted to run all of this on your own computer, you'll need to follow the bioconda install instructions.

We'll be implementing a short read quality check and trimming pipeline, using [fastqc](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/), [trimmomatic](http://www.usadellab.org/cms/?page=trimmomatic), and [multiqc](https://multiqc.info/).

You can see the full set of installed software requirements [here](https://github.com/ctb/2019-snakemake-ucdavis/blob/master/binder/environment.yml), in a conda environment.yml file.

You could use this install file to run everything we're doing today on your laptop, with:

```
conda env create --file environment.yml -n smake
conda activate smake
```
# Introduction

[**Introduction**](https://snakemake2019.readthedocs.io/en/latest/introduction.html)

# Tutorial

[**Tutorial**](https://snakemake2019.readthedocs.io/en/latest/tutorial.html)

# Awesome

[**Awesome**](https://snakemake2019.readthedocs.io/en/latest/awesome.html)