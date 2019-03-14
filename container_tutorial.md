Running Jobs in containers
===

We will be executing the same workflow (fastqc--->multiqc--->trimmomatic) as in [Basic Tutorial](https://snakemake2019.readthedocs.io/en/latest/basic_tutorial.html) but, with each tool being executed in singularity containers [^2] based on either Docker or Singularity builds

> [**Guide to Launching Atmosphere Instances**](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html)


1. Login to CyVerse [Atmosphere](https://atmo.cyverse.org/application/images)

2. Launch a medium 'm1' instance with the 'DCG-UNR-RNAseq' v3.0 base image [^1]

3. Activate Conda

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
snakemake
```
4. Test singularity 

Singularity 2.6.1 is pre-installed and should be available in this image

Test installation by
```bash
singularity --version
```
5. Download data

6. Create 'Snakefile' with the code below

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

7. Executing Snakemake with
```
snakemake --use-singularity
```

Snakemake will pull the containers and execute each rule individually in the containers specified

8. Generate Report
```bash
snakemake --report report.html
```

---------------------------

[^1]: DCG-UNR-RNAseq v3.0 Atmosphere Image Specifications

Software:
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






[^2]: A container image is an encapsulated, portable environment that is created to distribute a scientific analysis or a general function. Containers help with reproducibility of such content as they nicely package software and data dependencies, along with libraries that are needed.