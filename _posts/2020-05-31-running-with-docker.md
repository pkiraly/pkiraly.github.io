---
title:      Running QA catalogue with Docker
layout:     post
date:       2020-05-31 00:00:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

Now the QA catalogue (metadata-qa-marc) can be run with Docker. Once you have Docker on the machine, 
you can run the full end-to-end quality assessment process (including building the web user interface) with the following two commands:

1. download the docker image, create and launch a docker container (supposing your MARC files are in directory ~/data/marc)
```
docker run \
  -d \
  -v ~/data/marc:/opt/metadata-qa-marc/marc \
  -p 8983:8983 -p 80:80 \
  --name metadata-qa-marc \
  pkiraly/metadata-qa-marc
```

2. run all analyses on a file called rug01.export which is an alephseq file, in which there are fields defined at the Gent university library
```
docker container exec \
  -ti \
  metadata-qa-marc \
  ./metadata-qa.sh \
  --params "--marcVersion GENT --alephseq" \
  --mask "rug01.export" \
  --catalogue gent 
  all
```

The workflow looks something like this:

<img src="{{ site.url }}/img/qa-catalogue-on-docker.png" class="big" title="Docker workflow" alt="Docker workflow" />


<!-- more -->

## Very short introduction to Docker
This description is not meant to provide a detailed description of what Docker is. If you are new to this technology: it
is a virtualization technology, which enables to build and run a virtual machine inside your operating system but
independent of your existing environment. This special environment contains an operating system, and all the software
packages which are needed to accomplish the tasks this tool is aiming to fulfil. A number of tools are available in "dockerized"
version. The benefit is that you don't have to install all the dependencies which may or may not available for your
OS, everything is packaged to be ready to use. There are some concepts you have to know before starting.

* _host_: the machine within which Docker runs (your desktop machine, or a server)
* _image_: is the environment in a "frozen" state. You can download it, and deleted it after usage.
* _container_: the environment which is created from the image, and this is what actually runs the tasks. It can store data,
however when we stop the container all data generated during the session will be lost. You can create multiple containers from the same image, but every time you do it, it will start from a blank state.
* _volume_: a directory which is shared with the container. Volumes could guarantee that the data generated during the session
can persist.

To install Docker on your host, follow the manual at [https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/).

## Explanation of the commands

### Installing QA catalogue

The installation is a single command, and does not require other prerequisite than a running Docker service:

```
docker run \
  -d \
  -v ~/data/marc:/opt/metadata-qa-marc/marc \
  -p 8983:8983 -p 80:80 \
  --name metadata-qa-marc \
  pkiraly/metadata-qa-marc
```

It creates a container named `metadata-qa-marc` out of the image `pkiraly/metadata-qa-marc`. If the image is
not yet available in your machine, it downloads from the repository of Docker images called Docker Hub. The
container runs on the background. Within the container an Apacher HTTP server and an Apache Solr server
are launched.

Parameters
 * `-d`: runs the docker in the background (kind of as a service)
 * `-v ~/data/marc:/opt/metadata-qa-marc/marc`: it mounts your existing `~/data/marc` directory 
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

### Running commands in the container

```
docker container exec
  -ti \
  metadata-qa-marc \
  ./metadata-qa.sh \
  --params "--marcVersion GENT --alephseq" \
  --mask "rug01.export" \
  --catalogue gent 
  all
```

* `docker container exec`: executes a command on the container
* ` -ti`: interactive mode, it maps stdin and stdout channels between host and container. While the first command
does not tell you about what's going on behind, it does, the same way as you open a terminal window
* `metadata-qa-marc`: the name of the container
* `./metadata-qa.sh`: the script to execute. The working directory in the container is `/opt/metadata-qa-marc`, this script is available in this directory. You can specify different scripts or commends. For example if you want to log in into the container's shell issue `/bin/bash`. The rest of the parameters are the parameters of the `metadata-qa.sh` script.
* `--params "--marcVersion GENT --alephseq"`: general parameters passed to the underlying scripts which call the quality assessment tool. You can pass any parameters defined in [https://github.com/pkiraly/metadata-qa-marc](https://github.com/pkiraly/metadata-qa-marc). This time we passed the foollowing parameters
  * `--marcVersion GENT` means that we use the MARC21 fields defined in Gent catalogue,
  * `--alephseq` means that the source file's format is Alephseq 
* `--mask "rug01.export"`: the analysis should run on the files the mask selects. You can use the usual unix wildcards, such as `*.marcxml`
* `--catalogue gent`: this parameter is passed to the web interface configuration, and ensure that the interface shows the catalogue as the Gent university catalogue
* `all`: the analysis to run. `all` runs all the analyses. Other possible values
  * `validate`: run validation
  * `completeness`: run complreteness
  * `classifications`: run classification analysis
  * `authorities`: run authorities analysis
  * `tt-completeness`: run Thompson-Traill completeness analysis
  * `serial-score`: run serial score analysis
  * `functional-analysis`: run FRBR functional analysis
  * `prepare-solr`: prepare Solr indexes
  * `index`: index with Solr
  * `all-analyses`: run all above, except the index related ones
  * `all-solr`: run the indexing related ones (`prepare-solr` and `index`)

Depending on the size of your data and the performance of your machine the running time will be of different length. Since the metadata-qa.sh script is just a wrapper which calls other scripts, the process informs you which scripts and which parameters are called. Each scripts produce lengthy log files into the `/opt/metadata-qa-marc/_reports/metadata-qa` directory (which is available as the host's `~/data/marc/_reports/metadata-qa`, when I set the volume as ~/data/marc). The output of these processes are CSV files available at the container's `/opt/metadata-qa-marc/_output/metadata-qa/` (host's `~/data/marc/_output/metadata-qa`) directory, and two Solr indexes: `metadata-qa` and `metadata-qa_dev`. The production always use the first index, and the indexing process uses the later one. When it is finished, the two indexes are swapped. This way the service should not be stopped during the metadata analysis.

The top level output of the process will be available at http://YOUR-SERVER/metadata-qa.

### Uninstall QA catalogue

Since the launched container in the background, it will keep running untill the machine is on. To stop the container, issue the following command:

```
docker stop metadata-qa-marc
```

If you don't want to use this tool anymore, you can remove the container and the image by

```
docker rm metadata-qa-marc
docker rmi pkiraly/metadata-qa-marc
```

The image is based on another image (ubuntu, which provides the operating system version 18.04). You can remove it by:

```
docker rmi ubuntu:18.04
```

Note: if you use other Docker tools, there is chance that other images also based on Ubuntu, in that case Docker doesn't let you to remove this image, so it is a safe operation.

## Towards continous metadata quality assessment

Once you set up the process you can move towards continous metadata quality assessment. You have to implement two steps with a cron job (or another scheduler of your choice):

* extract catalogue records and/or download it to the machine
* run the metadata analyses

## Notes

I am not a Docker expert. If you are, and spot points to improve, do not hesitate to tell me. I am very curious how to make the image size smaller. The underlying software are under constant development, so you might expect new parameters, or even drastical changes in the structure of the image. I can promisse however that the command line interface changes will be always reflected in the project page: [https://github.com/pkiraly/metadata-qa-marc](https://github.com/pkiraly/metadata-qa-marc).
