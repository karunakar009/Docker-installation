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




  
