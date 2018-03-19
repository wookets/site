+++
title = "Docker"
description = "A getting started with docker guide"
author = "wookets"
date = 2018-03-18T13:17:54-05:00
weight = 20
draft = false
bref = "A getting started with docker guide"
toc = true
+++

### Overview

The official [docker website](https://www.docker.com/what-docker) gives you a good overview. More simply, docker also you to image your application and infrastructure and deploy it rapidly and repeatedly. This is done by creating an isolated environment (a container) that can run side-by-side with other containers on the same hardware. Think of containers as [Virtual Machines](https://en.wikipedia.org/wiki/Virtual_machine) but without the resource hoginess / slowness. 

### Setup

[Downlaod Docker](https://www.docker.com/community-edition#/download) from the [Docker Store](https://store.docker.com/). You'll want to just grab the [community edition](https://store.docker.com/editions/community/docker-ce-desktop-mac). 

Once it finishes downloading, you'll drag it into applications as you normally would with other OSX applications. Command + Spacebar "Docker" should give you the docker.app once it is done indexing. You can also open up the terminal and start using docker commands. 

![Docker OSX Install](http://cdn.wookets.com/images/docker/docker-osx-install.png "Docker OSX Install")

### Usage

Docker provides a decent GUI to interact with it on OSX via a flyout menu in the system tray in the upper-right corner. 

![Docker Menu Flyout](http://cdn.wookets.com/images/docker/docker-menu-flyout.png "Docker Logo Flyout")

Also installed is the [Docker command line](https://docs.docker.com/engine/reference/commandline/cli/), which is what will be the main interaction point with docker containers, starting and stopping, etc.

```bash
docker --version
```

Let's go for a [hello world container](https://docs.docker.com/docker-for-mac/).

```bash
docker run hello-world
docker run -d -p 80:80 --name webserver nginx
```



