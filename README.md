![Rancher Logo](https://ranchermanager.docs.rancher.com/img/rancher-logo-horiz-color.svg) 
---
---

# Installing Rancher on a single Node using Docker

## Pre-requisites:
 - [Refer rancher pre-requisite](https://ranchermanager.docs.rancher.com/pages-for-subheaders/installation-requirements)

- [Please check K3s kubernetes pre-requisites](https://ranchermanager.docs.rancher.com/pages-for-subheaders/installation-requirements#k3s-kubernetes)

---

### Virtual Machine configuration used in this guide.

- 1 VM with 4 CPU and 8GB Ram

---

 ### In this tutorial we are dealing with ***K3s*** cluster. 

 Lightweight Kubernetes. Easy to install, half the memory, all in a binary of less than 100 MB. [Read more about K3s here](https://docs.k3s.io/)

---

## Let's begin with Installation and Setup.

Initially we will install the Docker in the system.(Skip this step if Docker is already present in the system)

### Docker Installation

- Install Docker and Check it's running in the system.

        sudo zypper install docker

- Start the docker daemon during boot:

        sudo systemctl enable docker

- Join the docker group that is allowed to use the docker daemon:

        sudo usermod -G docker -a $USER

- Restart the docker daemon:

        sudo systemctl restart docker

- Verify docker is running:

        docker version

### Rancher Installation

- Pull Rancher docker image and wait for UI to appear.

        docker run -d --restart=unless-stopped   -p 80:80 -p 443:443   --privileged   rancher/rancher:latest

    wait for few minutes to pull docker image and setup *k3s* kubernetes cluster in your system.

- Check docker image status

        docker ps -a

- Login to the Rancher UI
    (Default username is *admin*)

        - Open Browser
        - Goto https://localhost:443

- For login password

        docker logs  <container_id>  2>&1 | grep "Bootstrap Password:"

    Good Practice: Change password immediately.

After Login you will see cluster is being depoyed on the system, once it is ready you can play with fleet.

Want to know more about fleet stay connected...
### Play with Rancher...
