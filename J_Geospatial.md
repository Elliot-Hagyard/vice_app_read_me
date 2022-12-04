# Jupyterlab Datascience Notebook Geospatial

[![Project Supported by CyVerse](https://de.cyverse.org/Powered-By-CyVerse-blue.svg)](https://learning.cyverse.org/projects/vice/en/latest/) [![Project Status: WIP – Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active) [![license](https://img.shields.io/badge/license-BSD3-red.svg?style=flat-square)](https://opensource.org/licenses/BSD-3-Clause)

[Project Jupyter](https://jupyter.org/) Datascience Notebook with packages for processing, analyzing, and visualizing geospatial data and a few added packages for use in [CyVerse Discovery Environment](https://de.cyverse.org/)

Jupyter Lab Datascience image built from the [Datascience Notebook](https://hub.docker.com/r/jupyter/datascience-notebook) for [CyVerse VICE](https://learning.cyverse.org/vice/about/). Project Jupyter's base image requires a couple additional configuration files for it be compatible with CyVerse Kubernetes orchestration and iRODS data store.

## Developer Instructions

Launch in CyVerse with a [verified user account (free)](https://user.cyverse.org):

[![quicklaunch](https://img.shields.io/badge/Geosptial-latest-orange?style=plastic&logo=jupyter)](https://de.cyverse.org/apps/de/0bb01716-5d03-11ec-b195-008cfa5ae621)

### Packages

1. Jupyterlab Datascience:
    - includes libraries for data analysis from the Julia, Python, and R communities.
    Specifc information about the base images can be found [here](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html)
2. CyVerse Packages:
    - python, go, and iRODS icommands, GitHub cli, and CyberDuck CLI
3. Geospatial Specific
    - jupyterlab-geojson : extension for rendering GeoJSON\n
    - sidecar : context manager for jupyter
    - ipyvolume : 3d plotting for Python in the Jupyter notebook based on IPython widgets using WebGL.
    - itkwidgets : Interactive Jupyter widgets to visualize images, point sets, and meshes
    - jupyterlab_iframe : Open a site in a widget, or add a set of "quicklinks".
    - jupyter-leaflet: interactive maps in notebook.
    - jupyter-threejs : python / ThreeJS bridge for Jupyter Widgets.

To build and run the image locally

```
git clone https://github.com/cyverse-vice/jupyterlab-datascience
cd geospatial
docker build -t geospatial:latest .
docker run -it --rm -p 8888:8888 geospatial:latest
```

Unless you plan on making changes to this container, you should just use the existing launch button above.

You can build a new Docker container with additional dependencies from this Docker Hub image by using the FROM cyversevice/jupyterlab-scipy:latest at the beginning of your own Dockerfile.

To test the container locally

```
docker run -it --rm -p 8888:8888 -e REDIRECT_URL=http://localhost:8888 harbor.cyverse.org/vice/jupyter/geospatial:latest
```

To build your own container with a Dockerfile and additional dependencies, pull the pre-built image from DockerHub:

```
FROM harbor.cyverse.org/vice/jupyter/geospatial:latest
```

Follow the instructions in the [VICE manual for integrating your own tools and apps](https://learning.cyverse.org/vice/extend_apps/#building-an-app-for-your-tool).
