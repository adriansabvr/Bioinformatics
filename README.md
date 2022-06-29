# Bioinformatics Container

[![Build tatus](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

This repository contains files and scripts necessary to create a bioinformatics container powered by docker
with useful libraries like:

- Biopython
- Openmm
- Pymol

## Features

- Building


## Docker Installation
Please, follow the official guide:
https://docs.docker.com/get-docker/

## Compilation (Image creation)

In order to compile the dockerfile, execute the following command:
```sh
docker build [path] -d [Dockerfile_Name] -t [Container_Name]
```

Example
```sh
docker build . -d Dockerfile.txt -t serv
```

## Execution (Container)

In order to execute the container is necessary to pass some arguments for a fully functional enviroment.
```sh
docker run -d -p [port] -v [host_shared_path]:/work [image_name]
```

Examples.

Minimal Execution
```sh
docker run  -d -p 8888:8888 -v /C/Users/vital/OneDrive/Escritorio:/work serv5
```

Execution with gpus
*Install the nvidia-container-toolkit:*
https://developer.nvidia.com/cuda-toolkit
```sh
docker run  -d -p 8888:8888 -v /C/Users/vital/OneDrive/Escritorio:/work --gpus all serv5
```

Fully Execution (Shared display)
*Install xserver:*
https://sourceforge.net/projects/vcxsrv/

First execute xserver from cmd
```sh
"C:\Program Files\VcXsrv\vcxsrv.exe" :0 -multiwindow -clipboard -nowgl -ac
```

then execute:
```sh
docker run  -d -p 8888:8888 -e DISPLAY=[host_ip:0] -v /C/Users/vital/OneDrive/Escritorio:/work --gpus all serv5
```

Example
```sh
docker run  -d -p 8888:8888 -e DISPLAY=[192.168.3.50:0] -v /C/Users/vital/OneDrive/Escritorio:/work --gpus all serv5
```
## Test
In this repository is included a test/tutorial notebook called AIO, use it to test the fully functional container. 

## Docker Hub
There is an image of this dockerfile already compiled in dockerhub, this is the recommended way to use it.

To download run the following commands:
```sh
docker pull 
```


## License

MIT

**Free Software, Hell Yeah!**
