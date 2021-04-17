# Ankit Agarwal
## __Gitlab_ Commands, Most Used_

[![N|Solid](https://img.stackshare.io/service/5545/9pAwHBR0.jpg)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)


- [About Gitlab](#about-docker)
- [Register for Docker ID](#register-for-docker-id)
- [Container Creation](#container-creation)


uigiougiugf
ihviukviuvuivui
kjvhjukvukvuikv



- [Basic Commands](#basic-commands)
- [Everyday use](#everyday-use)
- [Processing files and data](#processing-files-and-data)
- [System debugging](#system-debugging)
- [One-liners](#one-liners)
- [Obscure but useful](#obscure-but-useful)
- [macOS only](#macos-only)
- [Windows only](#windows-only)
- [More resources](#more-resources)
- [Disclaimer](#disclaimer)



# About Gitlab
GitLab is a web-based DevOps lifecycle tool that provides a Git-repository manager providing wiki, issue-tracking and continuous integration and deployment pipeline features, using an open-source license, developed by GitLab Inc. The software was created by Ukrainian developers Dmitriy Zaporozhets and Valery Sizov.    

# Docker Container Creation
## The Container
### Register for Docker ID
Your Docker ID becomes your user namespace for hosted Docker services, and becomes your username on the Docker Forums. To create a new Docker ID:

1. Go to the Docker Hub signup page.
2. Enter a username that is also your Docker ID.
3. Your Docker ID must be between 4 and 30 characters long, and can only contain numbers and lowercase letters.
4. Enter a unique, valid email address.
5. Enter a password. Note that the password must be at least 9 characters.
6. Complete the Captcha verification and then then click Sign up.
7. Docker sends a verification email to the address you provided.
8. Verify your email address to complete the registration process.

**Note:** You cannot log in with your Docker ID until you verify your email address.
For Signup process refer the official website. [https://docs.docker.com/docker-id/]

### Container Creation 
To create a container with ubuntu version 18.04 run the following command.
Command: docker run --name <Container Name> OS:Tag
* <Container Name>: You can use any name you want, this is more for our reference as it's easy to remember a container with a name than a container ID. (In our case I'm calling it as Gitlab as I'm creating this container for Gitlab)
* OS: The OS is nothing but the OS type that you want (It should also be available on the Docker hub). In our case we are using Ubuntu OS.
* Tag: This is the version defined on the docker hub. (In our case we are using version 18.04)
```
$ docker run -d -it --name Gitlab ubuntu:18.04
```

----

### Start the Container and login to it
To start the container run the following command.
Command: docker start <Container Name>
Command: docker exec <Container Name> bash
```
$ docker exec 
```




