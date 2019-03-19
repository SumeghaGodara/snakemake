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

# Open Rstudio

- Type the following in your terminal to display a link to Rstudio web-server for your isntance's $(hostname)
```
echo http://$(hostname):8787/
```
> click on the link generated to open Rstudio in your browser and login with your CyVerse credentials.
![](/img/rstudio_interface.png)

# Run snakemake

- Create a new text file (`File`, `New File`, `Text file`) and and paste the code below we have from [Snakemake Basic Tutorial](https://snakemake2019.readthedocs.io/en/latest/smake_basic_tutorial.html)

```python
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

rule clean:
  shell:
    "rm -f {fastqc_output} multiqc_report.html"     
```

- - Save the file as `Snakefile`and execute Snakemake in your terminal by:

```bash
snakemake --use-singularity
```

> **Snakemake will pull the containers and execute each rule individually in the containers specified**

# Visualize Workflow

```bash
snakemake --dag | dot -Tpng > dag.png
```
- Click on the dag.png image in FIle Explorer and open in web-browser

# Generate Report

```bash
snakemake --report report.html
```

> **EXERCISE**: Write a snakemake rule to download data and unzip it (as we did earlier using bash commands) and save it to your workflow.

# Coming Soon

> **In the next tutorial, we will learn how to build a Dockerfile for 'Trimmomatic app' from scratch and add it as a rule to our workflow. Stay Tuned !**

![](/img/logos/minion.gif)

> **Note: It is advisable to delete your instance if you are not planning to use it in future to save valuable resources. However if you want to use it in future, you can suspend it. See [**Instance Maintenace**](https://snakemake2019.readthedocs.io/en/latest/Atmosphere_Cloud.html#instance-maintenance) for more info**

---------------------------

**Snakemake2019 v1.0** [Atmosphere Image Specifications](https://atmo.cyverse.org/application/images/1687)
