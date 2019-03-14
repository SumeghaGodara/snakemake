Running Jobs in containers
===

# Running jobs in containers [^1]

[**CyVerse Atmosphere**](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html)


#### Activate Conda

```
echo export PATH=$PATH:/opt/miniconda3/bin >> ~/.bashrc
```

Then, run the following command (or start a new terminal session) in order to activate the conda environment:

```
source ~/.bashrc
```

Add channels

```
conda config --add channels defaults
conda config --add channels conda-forge
conda config --add channels bioconda
```

Try running a program pre-installed on this instance:

```bash
fastqc
```



As an alternative to using Conda (see above), it is possible to define, for each rule, a docker or singularity container to use, e.g.,

```python
fastqc_output = ["data/0Hour_001_1_fastqc.html", "data/6Hour_001_1_fastqc.html",
  "data/0Hour_001_2_fastqc.html", "data/6Hour_001_2_fastqc.html",
  "data/0Hour_002_1_fastqc.html", "data/6Hour_002_1_fastqc.html",
  "data/0Hour_002_2_fastqc.html", "data/6Hour_002_2_fastqc.html",
  "data/0Hour_001_1.pe.qc_fastqc.html", "data/0Hour_002_1.pe.qc_fastqc.html",
  "data/6Hour_001_1.pe.qc_fastqc.html", "data/6Hour_002_1.pe.qc_fastqc.html",
  "data/0Hour_001_2.pe.qc_fastqc.html", "data/0Hour_002_2.pe.qc_fastqc.html",
  "data/0Hour_001_2.pe.qc_fastqc.html", "data/0Hour_002_2.pe.qc_fastqc.html"]

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

rule trim_reads:
  input:
    "{filename}_1.fq.gz",
    "{filename}_2.fq.gz"
  output:
    "{filename}_1.pe.qc.fq.gz",
    "{filename}_1.se.qc.fq.gz",
    "{filename}_2.pe.qc.fq.gz",
    "{filename}_2.se.qc.fq.gz"
  singularity:
    "docker://fjukstad/trimmomatic"
  shell:
    "java -jar /tools/trimmomatic/trimmomatic-0.36.jar PE {input} {output} LEADING:2 TRAILING:2 \
     SLIDINGWINDOW:4:15 \
     MINLEN:25"    

rule clean:
  shell:
    "rm -f {fastqc_output} multiqc_report.html"     
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





[^1]: A container image is an encapsulated, portable environment that is created to distribute a scientific analysis or a general function. Containers help with reproducibility of such content as they nicely package software and data dependencies, along with libraries that are needed.