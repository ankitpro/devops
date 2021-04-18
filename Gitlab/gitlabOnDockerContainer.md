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

### Create a container with an existing docker image
To create a container with an existing image we first need a container created or downloaded locally.
In our case I already have an image create with the name "ubuntu_with_gitlab".
Command: docker run -d -it --name <container name> <docker image name>
```
docker run -d -it --name cont1 ubuntu_with_gitlab
275a8b15e3358c82118b4d8014784e85dbf4520536cb2657427f002f2983be6d

````

----

Now that the container is docker conatiner is created let's try to install Gitlab on it.
But before that we got to start the container and get inside the container.

### Start the container created above and get inside the terminal of the container.
```
$ git exec -it cont1 bash
root@275a8b15e335:/#
```

# Gitlab Installation on Docker Container
## Step 1 Installing the Dependencies
Before we can install GitLab itself, it is important to install some of the software that it leverages during installation and on an ongoing basis. Fortunately, all of the required software can be easily installed from Ubuntu’s default package repositories.

Since this is our first time using apt during this session, we can refresh the local package index and then install the dependencies by typing:

```
root@275a8b15e335:/# sudo apt update
root@275a8b15e335:/# sudo apt install ca-certificates curl openssh-server postfix -y
```

You will likely have some of this software installed already. For the postfix installation, select Internet Site when prompted. On the next screen, enter your server’s domain name to configure how the system will send mail.


## Step 2 — Installing GitLab
Now that the dependencies are in place, we can install GitLab itself. This is a straightforward process that leverages an installation script to configure your system with the GitLab repositories.

Move into the /tmp directory and then download the installation script:

```
root@275a8b15e335:/# cd /tmp
root@275a8b15e335:/tmp# curl -LO https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh
```

Run the installer after verifing the script.
```
root@275a8b15e335:/tmp# sudo bash /tmp/script.deb.sh
```

The script will set up your server to use the GitLab maintained repositories. This lets you manage GitLab with the same package management tools you use for your other system packages. Once this is complete, you can install the actual GitLab application with apt:

```
root@275a8b15e335:/tmp# sudo apt install gitlab-ce
```

This will install the necessary components on your system.

## Step 3 — Adjusting the Firewall Rules
Before you configure GitLab, you will need to ensure that your firewall rules are permissive enough to allow web traffic. If you followed the guide linked in the prerequisites, you will have a ufw firewall enabled.

View the current status of your active firewall by typing:

```
root@275a8b15e335:/tmp# sudo ufw status
```

```
Output:

```


Step 4 — Editing the GitLab Configuration File
Before you can use the application, you need to update the configuration file and run a reconfiguration command. First, open Gitlab’s configuration file:

```
root@275a8b15e335:/tmp# sudo nano /etc/gitlab/gitlab.rb
```
Near the top is the external_url configuration line. Update it to match your domain. Change http to https so that GitLab will automatically redirect users to the site protected by the Let’s Encrypt certificate:

```
##! For more details on configuring external_url see:
##! https://docs.gitlab.com/omnibus/settings/configuration.html#configuring-the-external-url-for-gitlab
external_url 'https://example.com'
```

Next, look for the letsencrypt['contact_emails'] setting. This setting defines a list of email addresses that the Let’s Encrypt project can use to contact you if there are problems with your domain. It’s a good idea to uncomment and fill this out so that you will know of any issues:

```
letsencrypt['contact_emails'] = ['sammy@example.com']
```

Save and close the file. Run the following command to reconfigure Gitlab:

```
root@275a8b15e335:/tmp# sudo gitlab-ctl reconfigure
```

This will initialize GitLab using the information it can find about your server. This is a completely automated process, so you will not have to answer any prompts. The process will also configure a Let’s Encrypt certificate for your domain.

