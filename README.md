# Docker-installation
## Install Docker Engine on Ubuntu
## Prerequisites
## OS requirements

To install Docker Engine, you need the 64-bit version of one of these Ubuntu versions:

* Ubuntu Noble 24.04 (LTS)
* Ubuntu Mantic 23.10 (EOL: July 12, 2024)
* Ubuntu Jammy 22.04 (LTS)
* Ubuntu Focal 20.04 (LTS)

Docker Engine for Ubuntu is compatible with x86_64 (or amd64), armhf, arm64, s390x, and ppc64le (ppc64el) architectures.

## Uninstall old versions
Before you can install Docker Engine, you need to uninstall any conflicting packages.

Distro maintainers provide unofficial distributions of Docker packages in APT. You must uninstall these packages before you can install the official version of Docker Engine.

The unofficial packages to uninstall are:
* docker.io
* docker-compose
* docker-compose-v2
* docker-doc
* podman-docker

  Moreover, Docker Engine depends on containerd and runc. Docker Engine bundles these dependencies as one bundle: containerd.io. If you have installed the containerd or runc previously, uninstall them to avoid conflicts with the versions bundled with Docker Engine.
  

Run the following command to uninstall all conflicting packages:
~~~
 for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg
~~~

apt-get might report that you have none of these packages installed.
Images, containers, volumes, and networks stored in /var/lib/docker/ aren't automatically removed when you uninstall Docker. If you want to start with a clean installation, and prefer to clean up any existing data, read the uninstall Docker Engine section.


## Installation methods

You can install Docker Engine in different ways, depending on your needs:

* Docker Engine comes bundled with Docker Desktop for Linux. This is the easiest and quickest way to get started.

* Set up and install Docker Engine from Docker's apt repository.

* Install it manually and manage upgrades manually.

* Use a convenience script. Only recommended for testing and development environments.

  ## Install using the apt repository

  Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.
  1.Set up Docker's apt repository.

~~~
  # Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
~~~

2.Install the Docker packages.

To install the latest version, run:
~~~
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
~~~
3.Verify that the Docker Engine installation is successful by running the hello-world image.

~~~
sudo docker run hello-world
~~~
This command downloads a test image and runs it in a container. When the container runs, it prints a confirmation message and exits.

You have now successfully installed and started Docker Engine.



Tip

Receiving errors when trying to run without root?

The docker user group exists but contains no users, which is why you’re required to use sudo to run Docker commands. Continue to Linux postinstall to allow non-privileged users to run Docker commands and for other optional configuration steps.




  
