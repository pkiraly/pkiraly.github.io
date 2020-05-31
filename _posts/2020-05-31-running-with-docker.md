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

Parameters
 * `d`: runs the docker in the background (kind of as a service)
 * `-v ~/data/gent:/opt/metadata-qa-marc/marc` it mounts your existing `~/data/gent` directory 
 to `/opt/metadata-qa-marc/marc` in the container (within the Docker environment)
