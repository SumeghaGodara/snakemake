Snakemake Tutorial on Atmosphere Cloud
===

> [**Guide to Launching Atmosphere Instances**](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html)

> **We will be executing the same workflow [fastqc](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)--->[multiqc]()--->[trimmomatic]() as in [Basic Tutorial](https://snakemake2019.readthedocs.io/en/latest/smake_basic_tutorial.html) but, with tools being executed in singularity containers based on either Docker or Singularity builds**

- Dockerfiles
  + [fastqc](https://github.com/sateeshperi/fastqc_docker/blob/master/Dockerfile)
  + [multiqc](https://github.com/sateeshperi/multiqc_docker/blob/master/Dockerfile)
  + [trimmomatic](https://github.com/sateeshperi/trimmomatic_docker/Dockerfile)

# Login to CyVerse [Atmosphere](https://atmo.cyverse.org/application/images)

# Launch a tiny 't1' instance with the 'Snakemake2019' v1.0 base image

# Activate Conda

```bash
echo export PATH=$PATH:/opt/miniconda3/bin >> ~/.bashrc
```

- Then, run the following command (or start a new terminal session) in order to activate the conda environment:

```bash
source ~/.bashrc
```

- Add channels

```bash
conda config --add channels defaults
conda config --add channels conda-forge
conda config --add channels bioconda
```

- Try running the following UNIX command 'which', which returns the pathnames of the files (or links) which would be executed in the current environment:

```bash
which snakemake
```
> it should show the absolute path of snakemake as '/opt/miniconda3/bin/snakemake'

- Check if singularity is available in your $PATH and print version:

```bash
which singularity
singularity --version
```
> It should show the absolute path of singularity '/usr/local/bin/singularity'

# Download data

```bash
mkdir data
cd data/
curl -L https://osf.io/er5tb/download -o data.zip
unzip data.zip
rm data.zip
cd ..
```
> EXERCISE: write a snakemake rule to download data and unzip it as above

# Open Rstudio

```
echo http://$(hostname):8787/
```
> click on the link generated to open Rstudio in your browser and login with your CyVerse credentials.

![Rstudio](/img/rstudio_interface.png)

# Run snakemake

- Create Snakefile using text editor nano:

```bash
nano Snakefile
```
 and paste the code below we have from [Basic Tutorial](https://snakemake2019.readthedocs.io/en/latest/smake_basic_tutorial.html)

```python=
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
        "docker://sateeshperi/fastqc"    
    shell:
        "fastqc {input}"

rule run_multiqc:
  input:
    fastqc_output
  output:
    "multiqc_report.html",
    directory("multiqc_data")
  singularity:
    "docker://sateeshperi/multiqc"
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
    "docker://sateeshperi/trimmomatic"
  shell:
    "java -jar /tools/trimmomatic/trimmomatic-0.36.jar PE {input} {output} LEADING:2 TRAILING:2 \
     SLIDINGWINDOW:4:15 \
     MINLEN:25"    

rule clean:
  shell:
    "rm -f {fastqc_output} multiqc_report.html"     
```

- Execute Snakemake with

```bash
snakemake --use-singularity
```

> Snakemake will pull the containers and execute each rule individually in the containers specified

> Note how each singularity container is activated for each rule

# Generate Report

```bash
snakemake --report report.html
```

> **Note: It is advisable to delete your instance if you are not planning to use it in future to save valuable resources. However if you want to use it in future, you can suspend it. See [**Instance Maintenace**](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html#instance-maintenance) for more info**

---------------------------


**Snakemake2019 v1.0** [Atmosphere Image Specifications](https://atmo.cyverse.org/application/images/1687)
