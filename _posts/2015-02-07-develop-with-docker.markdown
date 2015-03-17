---
author: ian_mcxa
comments: true
date: 2015-02-07 18:49:56+00:00
layout: post
slug: develop-with-docker
title: Develop on OSX with Docker
thumbnail: /images/guide-images/docker.png
categories:
- General
- Guides
tags:
- development
- docker
- linux
- osx
- virtualbox
- virtualization
---

![](/images/guide-images/docker.png)

### What is Docker, and why use it on your Hackintosh/Mac?


OSX is a great platform for software development. However, sometimes you need linux specific applications to run or at least to test your software. Traditionally, you would do this by creating virtual machines with Virtualbox and running full on linux environments for your applications.

This can be done much more efficiently with Docker. Docker deploys a minimal linux environment on your machine and then creates containers for any applications you need to deploy. These containers are separate at the application level, so they don't conflict with each other. Another benefit is that you can configure say, a webserver on your hackintosh through docker, and then you can simply copy that container to your linux server and initialize it.


### How to install


Docker has a helper application for OSX called boot2docker. It starts up a minimal virtual environment from which to start up docker containers.



	
  * Download [boot2docker here](https://github.com/boot2docker/osx-installer/releases). You'll want the .pkg

	
  * Run the docker installer.




### Running Docker


Once you start boot2docker, you can use docker just as if you were running it on a linux box. To start and stop boot2docker use the following commands


<blockquote>boot2docker start

boot2docker stop</blockquote>


Now that you have boot2docker running you can initialize containers to work from. To start up an Ubuntu image, enter the following command.


<blockquote>

> 
> sudo docker run -t -i ubuntu:14.04 /bin/bash
> 
> 
</blockquote>




This will download an Ubuntu 14.04 image and run it in docker.  the _-t -i _options will drop you into a terminal window for that docker container. You can then treat the terminal as if it were running on a native Ubuntu install complete with apt-get and networking.




It is also possible to port forward from your native machine to your container by using the _-p _option. For example:





<blockquote>

> 
> sudo docker run -p 8080:80 -t -i ubuntu:14.04 /bin/bash
> 
> 
</blockquote>




This would forward port 80 in your container to port 8080 on your mac. If you start a webserver in your container, you could view it in your browser by going to http://localhost:8080.




You can exit the container at any time by typing _exit_. The to stop the container simply run





<blockquote>

> 
> docker stop
> 
> 
</blockquote>




For other distributions and use cases visit the [Docker Hub](https://registry.hub.docker.com/). This is a repository with loads of applications and distributions pre-configured. All you have to do is type the run command and they will download and run. For more information on Docker and how to use it check out the [Docker user guide](http://docs.docker.com/userguide/).
