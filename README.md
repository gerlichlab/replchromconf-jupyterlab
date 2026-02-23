# A custom version of Jupyterlab environment at the VBC (CLIP HPC) for ReplChromConf project

## Try me out
Try me out with Binder:
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/gerlichlab/replchromconf-jupyterlab/HEAD)

## Prebuilt Apptainer/Singularity images
### Public
[DockerHub](https://hub.docker.com/repository/docker/gerlichlab/replchromconf-jupyterlab/general) tag v0.2 (Apptainer/Singularity image, not Docker!)
### Internal VBC
[Singularity image URL](https://singularity.vbc.ac.at/containers/1680).

Built images are available at: `/groups/gerlich/labinfo/Methods/singularity_images/`

## Perks
* All necessary packages preinstalled (except for OnTAD &mdash; have to build yourself)
* anywidget
* jupyterlab_materialdarker theme

## Info
Original [environment.yml](https://github.com/jupyterhub/repo2docker/blob/HEAD/repo2docker/buildpacks/conda/environment.yml) file. The `environment.yml` file in this repo is used after the original one.
