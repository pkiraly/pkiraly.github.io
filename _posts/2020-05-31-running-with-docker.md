---
title:      Running with Docker
layout:     post
date:       2020-05-31 00:00:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

Now the QA catalogue (metadata-qa-marc) can be run with Docker. Once you have Docker on the machine, 
you can run the quality assessment, build Solr, and build the web based user interface with the following commands

```
# downloads the docker image, create and launch a docker container.
# Your MARC files are in directory ~/data/gent
docker run -d \
           -v ~/data/gent:/opt/metadata-qa-marc/marc \
           -p 8983:8983 -p 80:80 \
           --name metadata-qa-marc \
           pkiraly/metadata-qa-marc
# run all analysis on a file called rug01.export which is an alephseq file, in which
# there are fields defined in the Gent university library
docker container exec -ti metadata-qa-marc \
           ./metadata-qa.sh \
           --params "--marcVersion GENT --alephseq" \
           --mask "rug01.export" \
           --catalogue gent 
           all
```
<!-- more -->

## Very short intro to Docker
This description is not ment to provide a detailed description of what Docker is. If you are new to this technology: docker
is a virtualization technology, which enables to build and run a virtual machine inside within your operating system 
independent of your existing environment. This special environment contains an operating system, and all the software
packages which needs to accomplish the task this tool is aiming for. A number of tools are available in "dockerized"
version. The benefit is that you don't have to install all the dependencies which may or may not available for your
OS, everything is packaged to be ready to use. There are some concepts you have to know before starting.

* host: the machine within wich Docker wuns (your desktop machine, or a server)
* image: is the environment in a "frozen" state. You can download it, and deleted it after usage.
* container: the environment which is created from the image, and this is what actually runs the tasks. It can store data,
however when we stop the container all data generated during the session will be lost. You can create multiple containers from the same image, but every time you do it, it will start from a blank state.
* volume: a directory which is shared with the container. Volumes could guarantee that the data generated during the session
can persist.

## Explanation of the commands 
```
docker run -d -v ~/data/gent:/opt/metadata-qa-marc/marc -p 8983:8983 -p 80:80 \
             --name metadata-qa-marc pkiraly/metadata-qa-marc
```

It creates a container named `metadata-qa-marc` out of the image `pkiraly/metadata-qa-marc`. If the image is
not yet available in your machine, it downloads from the repository of Docker images called Docker Hub. The
container runs on the background. Within the container an Apacher HTTP server and an Apache Solr server
are launched.

Parameters
 * `d`: runs the docker in the background (kind of as a service)
 * `-v ~/data/gent:/opt/metadata-qa-marc/marc`: it mounts your existing `~/data/gent` directory 
 to `/opt/metadata-qa-marc/marc` in the container (within the Docker environment). This directory
 is used as an input/output communication between the host and the container. You should store the
 MARC files (in binary, MARCXML or Alephseq format). You can add any directory from the host, but
 be careful not to change the container directory
 * `-p 8983:8983`: it maps the host port 8983 to the container port 8983 (<host port>:<container port>),
 so that if you check http://localhost:8983,
 what you will access is the container's Apache Solr instance. If you also have a running Solr, you should
 change the first port number, such as 8984:8983, otherwise Docker will not start.
 * `-p 80:80`: another port forwarding, this time it is the web server's port. Same rule applies here:
 if you have a running webserver, change the host port
 * `--name metadata-qa-marc`: give a name to the container. It will be helpful for other container commands.
 * `pkiraly/metadata-qa-marc`: this is the name of the image. If you do not have it, docker will download it
 automatically.

```
docker container exec -ti metadata-qa-marc \
           ./metadata-qa.sh \
           --params "--marcVersion GENT --alephseq" \
           --mask "rug01.export" \
           --catalogue gent 
           all
```

* `docker container exec`: executes a command on the container
* ` -ti`: interactive mode, it maps stdin and stdout channels between host and container. While the first command
does not tell you about what's going on behind, it does, the same way as you open a terminal window
* `metadata-qa-marc`: the name of the container you execute the command
