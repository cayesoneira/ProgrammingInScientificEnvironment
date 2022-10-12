# A guide to the Hands-on session of Docker.
1. Share data between the host and containers

Use image: duartej/m1992-pyroot. Create some files inside the container and illustrate the different data sharing.

    In a running container, using docker cp
    When starting the container, binding a volume to the host 

2. Installing missing packages

Use image: rocker/binder. Install several R packages (Hmisc) in the container. 

    Use exec to enter to a terminal of the container, usually as `--user root`
    Not use the `--rm` option to avoid removing the container, and therefore whatever you did in there: remember once the container is closed, whatever you did in there (including the installation of new packages) disappears. 

Use image: m1992-python. Install missing packages permanently (astropy, healpy)

    Create/adapt the Dockerfile to incorporate the missing packages in the image

3. Detach mode

Containers can run interactively (then needs the `-it` options), and in detach mode, using the `-d` option. You can attach to a detached container with `attach` command.
You can detach an interactive container using the CRTL^P CTRL^Q sequence. 
4. Create a  jupyter notebook

Use image: jupyter/base-notebook:2022-08-01

    Create a running container binded to a local host folder
