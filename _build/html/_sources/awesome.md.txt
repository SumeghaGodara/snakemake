Awesome
===

## Thinking about workflows - a strong(er) argument

what do (snakemake) workflows do for me?

A laundry list:

- declarative vs procedural specification
  - allows analysis of workflow graph, parallelization
  - allows declaration of specific software needed, for later tracking
  - can compare workflows more easily, in theory (=> reproducibility)
  - can rerun failed steps
- tracks dependencies on files
  - allows rerunning just the bits that need to rerun
- reusability, in theory
- different conda environments for each step
  - allows pinning of software versions
  - allows use of potentially incompatible software

For me, the main reason to use snakemake is that it lets be sure that my workflow completed properly. snakemake tracks which commands fails, and will stop the workflow in its tracks! This is not something that you usually do in shell scripts.

### Dealing with complexity

Workflows can get really complicated; [here](https://github.com/spacegraphcats/2018-paper-spacegraphcats/blob/master/pipeline-base/Snakefile), for example, is one for our most recent paper. But it's all just using the building blocks that I showed you above!

If you want to see some good examples of how to build nice, clean, simple looking workflows, check out [this RNAseq example](https://github.com/snakemake-workflows/rna-seq-star-deseq2).

### Go forth and Workflow!

# Reproducibility Toolkit

![](/img/rep_toolkit.svg)

# [Snakemake Carpentry Lesson](https://hpc-carpentry.github.io/hpc-python/)

# [CyVerse Container Camp](https://singularity-tutorial.github.io/)

### Awesome list of workflow-management systems

+ [Snakemake Wrapper Repository](https://snakemake-wrappers.readthedocs.io/en/stable/index.html)
+ [curated list of awesome pipeline toolkits](https://github.com/pditommaso/awesome-pipeline)


