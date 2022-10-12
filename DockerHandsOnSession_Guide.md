# A guide to the Hands-on session of Docker.
This session is done in Windows. Soon I will move to Ubuntu. In *italics* are written the questions, afterwards there is my answer.

## 1. Share data between the host and containers

*Use image: duartej/m1992-pyroot. Create some files inside the container and illustrate the different data sharing: in a running container, using docker cp and when starting the container, binding a volume to the host.*

### Binding volumes:
- Before anything, I create two directories in `\C:`, one is called **VolumenDeCaye** and the other **CopiasDeCaye**. We will use them to not mix the different parts of the exercise.
- First of all, we open the Powershell as admin using right click.
- We open Docker Desktop to turn on the Docker Engine.
- We download the latest version of the image:

        docker pull duartej/m1992-pyroot
- We can make sure it is downloaded:

        docker images
- Now we can run the image binding a volume given a path (to know the absolute path of a directory we can use `tree <file>`) and also adding `/bin/bash` to enter the terminal inside the container and create some files we can see copied outside of it.

        docker run -v C:\VOLUMENDECAYE:/gate -it --rm duartej/m1992-pyroot:latest /bin/bash
- Note that the bars are inverted according to the OS: at the host the OS is Windows, but inside the container we are working with Linux distributions.
- We can create now a sample file to check if the volume is correctly created (working in the terminal inside the container):
        
        touch kk.txt
- And check it is there with `ls` (list).
- Now we can exit the terminal inside the container: `CTRL+P, CTRL+Q`.
- If we wanted to get inside the container again it is enough to copy the name of the container and write:

        docker attach <name of the container>
### Using the `cp` command:
- Now, using the same container we created, we can copy some files, again, we need two paths:

        docker cp ecstatic_ramanujan:/gate C:\COPIASDECAYE
- If we check our folder `CopiasDeCaye` we can see it has a copy of the `gate` directory inside.
---
## 2. Installing missing packages
We create a new folder called **ArchivoDockerDeCaye** in `\C:` where we will save the dockerfile that was given in the moodle. It has no extension (there is an explicit option to chose no extension when saving the document) and it is called **Dockerfile**, but the name is pointless. Also we need Xming to be on and not blocked by the Windows firewall.

*Use image: rocker/binder. Install several R packages (Hmisc) in the container.*
- We pull the new image, run it prepared to be a jupyter notebook (`-p 8888:8888 -v gate:/gate` is precisely to do that), 

        docker pull rocker/binder
        
        
        docker run -p 8888:8888 -v gate:/gate rocker/binder     
- Now open the notebook in the browser with the given url, create a new R notebook and use the R syntax to install the package `Hmisc` writing and running in that notebook:

        install.packages("Hmisc")
*Use exec to enter to a terminal of the container, usually as `--user root`.*
- Back in the terminal of the host, in a new window, we write (remember to not stop or kill the container!):
        
        docker exec --user root fervent_mclaren <command to enter>
*Use image: m1992-python. Install missing packages permanently (astropy, healpy).*
- We build the image `m1992-python` from the dockerfile. When we know the abolute path we write:

        docker build C:\ARCHIVODOCKERDECAYE
- We run it and use the terminal to install those packages.
        
        docker run -it 027f9d7572af
        
        FALTA EL COMANDO QUE HAY QUE METER EN LA TERMINAL DEL CONTAINER PARA QUE INSTALE ESO. YA INTENTÉ CASI TODAS LAS OPCIONES COMUNES DE PYTHON3 Y DE LINUX, ETC.
*Create/adapt the Dockerfile to incorporate the missing packages in the image.*
- We just find the following lines in the dockerfile:

        ...
            description="Docker image for M1992-Python with main scientific libraries"

        # -- Update and get needed packages
        USER root
        RUN apt-get update && apt-get install -y \
                python3-numpy \
                python3-matplotlib \
                python3-scipy \
                python3-pandas \
                # astropy \
                # healpy \
            && rm -rf /var/lib/apt/list/*

        # Avoid the kernel crashing likely due to the PID reaping problem
        ...
- And simply add to the list the needed libraries:
        
        ...
            description="Docker image for M1992-Python with main scientific libraries"

        # -- Update and get needed packages
        USER root
        RUN apt-get update && apt-get install -y \
                python3-numpy \
                python3-matplotlib \
                python3-scipy \
                python3-pandas \
                python3-astropy \
                python3-healpy \
            && rm -rf /var/lib/apt/list/*

        # Avoid the kernel crashing likely due to the PID reaping problem
        ...
---
## 3. Detach mode
*Containers can run interactively (then needs the `-it` options), and in detach mode, using the `-d` option. You can attach to a detached container with `attach` command. You can detach an interactive container using the CRTL^P CTRL^Q sequence.*
- We enter the interactive mode to use Python3 running the command we used before and it attachs us automaticaly:

        docker run -it 027f9d7572af
- But if run it in detach mode we do not get into the terminal of the container:

        docker run -it -d 027f9d7572af
- But we could attach whenever we want to use Python inside the container again:

        docker attach wonderful_wilbur
---
## 4. Create a  jupyter notebook

Use image: jupyter/base-notebook:2022-08-01

## Some extra tips (some of them are repeated).
- With `CTRL+C` we can stop a process in the terminal.
- With `CTRL+P, CTRL+Q` we can exit the inside terminal of the container and come back to the host terminal.

Create a running container binded to a local host folder
