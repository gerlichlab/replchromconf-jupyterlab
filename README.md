# JupyterLab image for Takacs, Mylarshchikov et al.

This repository contains a definition file for a companion Apptainer/Singularity image to run scripts and notebooks in [gerlichlab/takacs_mylarshchikov_et_al](https://github.com/gerlichlab/takacs_mylarshchikov_et_al), as well as instructions how to download a prebuilt image, run JupyterLab, and execute scripts.

## How to run JupyterLab

### Locally
First, pull the Apptainer/Singularity image from Docker Hub:
```{bash}
apptainer pull oras://registry-1.docker.io/gerlichlab/replchromconf-jupyterlab:v0.2
```
It will download the image as a file `replchromconf-jupyterlab_v0.2.sif` in the current directory.

Next, launch JupyterLab with apptainer:
```{bash}
apptainer exec replchromconf-jupyterlab_v0.2.sif jupyter lab --ip 0.0.0.0 --port 8888
```
Follow the instructions in the terminal.

### On JupyterHub (CLIP HPC)
1. Choose "JupyterLab based on custom Singularity image" (if supported by JupyterHub).
2. Paste the path to the image file in sif format.
3. Press "Start".

## How to execute scripts
To execute scripts with conda environment in the image, a wrapper script is needed to activate the conda environment.

First, pull the Apptainer/Singularity image from Docker Hub:
```{bash}
apptainer pull oras://registry-1.docker.io/gerlichlab/replchromconf-jupyterlab:v0.2
```
It will download the image as a file `replchromconf-jupyterlab_v0.2.sif` in the current directory.

Next, create a wrapper script named `run.sh` with the following contents:
```{bash}
# active conda env in the container
source /srv/conda/etc/profile.d/conda.sh
conda activate notebook

# your code here
...
```

Finally, run the wrapper script with:
```{bash}
apptainer run replchromconf-jupyterlab_v0.2.sif /bin/bash run.sh
```

This approach works both locally and on HPC clusters with job schedulers, such as SLURM.

## Prebuilt images
Images are built using repo2docker internally at VBC using Jenkins as CI. Currently, only Apptainer/Singularity images are available.

### Public
The image is hosted on [DockerHub](https://hub.docker.com/repository/docker/gerlichlab/replchromconf-jupyterlab/general), latest tag v0.2 (Apptainer/Singularity image, not Docker!)

### Internal VBC
Internally, images are hosted on VBC Singularity registry: [Singularity image URL](https://singularity.vbc.ac.at/containers/1680).

Built images are available at: `/groups/gerlich/labinfo/Methods/singularity_images/`

## Perks
* All necessary packages preinstalled (except for OnTAD &mdash; have to build yourself)
* anywidget
* jupyterlab_materialdarker theme

## Development
Original [environment.yml](https://github.com/jupyterhub/repo2docker/blob/HEAD/repo2docker/buildpacks/conda/environment.yml) file. The `environment.yml` file in this repo is used after the original one.
