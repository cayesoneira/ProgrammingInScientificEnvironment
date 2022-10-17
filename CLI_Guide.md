# CLI Commands:
## Docker
### Functions
- `build`: creation of image from a Dockerfile.
- `push`: push a local image to a registry.
- `pull`: pull an image from the registry into the local.
- `kill`: kill one or more running containers.
- `run`: run a command in a new container.
- `exec`: run a command in an existing container.
- This is the correct syntax to bind a mount: `sudo docker run -it -v /home/cayesoneira/CayeVolume:/gate duartej/m1992-pyroot /bin/bash`
### Options
## Bash
### Functions
- `pwd`: print working directory; shows the path of the current folder.
- `mkdir`
- `mv`
- `cp`
- `rm`
- `mdir`
- `cat`: see the content of a text file.
- `wget <url>`: get some file from a url.
- `unzip`
- `sed`: editor de flujo de texto, se utiliza con opciones que permiten reemplazar palabras, etc.
- `awk`: permite filtrar de un texto palabras, pero también números, etc.
- `cut`:
- `$()`: 
# CLI solved examples:
- Find all text files (.txt extension) smaller than 10 KB and that start with letter "a" inside a directory (included subdirectories):

      find . -type f -name '*.txt' -name 'a*' -size -10k
- 
