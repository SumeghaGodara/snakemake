Introduction
===
Why invest time in a workflow management system? 

A workflow management system (WMS) is a piece of software that sets up, performs and monitors a defined sequence of computational tasks (i.e. "a workflow"). Snakemake is a WMS that was developed in the bioinformatics community, and as such it has some features that make it particularly well suited for creating reproducible and scalable data analyses.

[**The Rationale**](https://hackmd.io/4useBM-tQHGGBg-i_2eAIw#)

![hate_research](img/hate_research.png)


**Snakemake is a workflow management system that helps you build pipelines between the scripts of your project.**

**Snakemake allows you to create a set of rules, each one defining a "step" of your analysis.** 

The rules need to be written in a file called "**Snakefile**". For each step you need to provide:

+ **Input** : Data files, scripts, executables or any other files.
+ **Expected output**. It's not required to list all possible outputs. Just those that you want to monitor or that are used by a subsequent step as inputs.
+ A **command** to run to process the input and create the output.

```
rule myname:
    input: ['myinput1', 'myinput2']
    output: ['myoutput']
    shell: 'Some command to go from in to out'
```

[**Snakemake Documentation**](https://snakemake.readthedocs.io/en/stable/index.html)

[**Snakemake Paper**](https://academic.oup.com/bioinformatics/article/28/19/2520/290322)