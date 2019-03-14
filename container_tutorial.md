Running Jobs in containers
===

# Running jobs in containers

[**CyVerse Atmosphere**](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html)

As an alternative to using Conda (see above), it is possible to define, for each rule, a docker or singularity container to use, e.g.,

```
fastqc_output = ["data/0Hour_001_1_fastqc.html", "data/6Hour_001_1_fastqc.html",
  "data/0Hour_001_2_fastqc.html", "data/6Hour_001_2_fastqc.html",
  "data/0Hour_002_1_fastqc.html", "data/6Hour_002_1_fastqc.html",
  "data/0Hour_002_2_fastqc.html", "data/6Hour_002_2_fastqc.html"]

rule all:
  input:
    "multiqc_report.html"
        
rule fastqc:
    input:
        "{filename}.fq.gz"
    output:
        "{filename}_fastqc.html",
        "{filename}_fastqc.zip"
    singularity:
        "docker://sateeshperi/fastqc_bioc"    
    shell:
        "fastqc {input}"

rule run_multiqc:
  input:
    fastqc_output
  output:
    "multiqc_report.html",
    directory("multiqc_data")
  singularity:
    "docker://sateeshperi/multiqc_bioc"
  shell:
    "multiqc data/"
```
When executing Snakemake with
```
snakemake --use-singularity
```
it will execute the job within a singularity container that is spawned from the given image. Allowed image urls entail everything supported by singularity (e.g., shub:// and docker://). 

```
Image Software:
		    - Miniconda 4.6.8
		    - Rstudio 1.1.453
		    - Singularity 2.6.1
		    - Snakemake 5.4.0
Conda tools:
		    - fastqc 0.11.8
		    - multiqc 1.6
		    - trimmomatic 0.38
		    - salmon 0.11.3
		    - trinity 2.8.4
R_Packages:
	        - "BiocGenerics"
	        - "S4Vectors"
	        - "knitr"
	        - "readr"
	        - "GenomicFeatures"
	        - "rjson"
	        - "tximport"
	        - "DESeq2"
	        - "magrittr"
	        - "ggplot2"
	        - "org.Hs.eg.db"
	        - "dplyr"
	        - "GO.db"
	        - "formatR"
	        - "caTools"
	        - "rprojroot"
	        - "rmarkdown"
	        - "AnnotationDbi"
	        - "clusterProfiler"
	        - "org.Mm.eg.db"
```