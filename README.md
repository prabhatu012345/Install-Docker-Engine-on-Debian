# Install-Docker-Engine-on-Debian
Official Documentation : https://docs.docker.com/engine/install/debian/
Prerequisites :

OS requirements
To install Docker Engine, you need the 64-bit version of one of these Debian versions:

Debian Bookworm 12 (stable)
Debian Bullseye 11 (oldstable)
Docker Engine for Debian is compatible with x86_64 (or amd64), armhf, arm64, and ppc64le (ppc64el) architectures.
# cat /etc/*release*

Uninstall old versions :
Docker Engine depends on containerd and runc. Docker Engine bundles these dependencies as one bundle: containerd.io. If you have installed the containerd or runc previously, uninstall them to avoid conflicts with the versions bundled with Docker Engine.

#  for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

Images, containers, volumes, and networks stored in /var/lib/docker/

Installation methods 

1. Install using the apt repository
   a. Set up Docker's apt repository.
     # Add Docker's official GPG key:
     sudo apt-get update
     sudo apt-get install ca-certificates curl gnupg
     sudo install -m 0755 -d /etc/apt/keyrings
     curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
     sudo chmod a+r /etc/apt/keyrings/docker.gpg

    # Add the repository to Apt sources:
    echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update
  b.  To install the latest version, run:
      sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  c. Verify that the installation is successful by running the hello-world image:
      sudo docker run hello-world

2. Install from a package 
   Follow the documentation

3. Install using the convenience script
   This is the easiest way to install docker engine on debian machine
curl -fsSL https://test.docker.com -o test-docker.sh
sudo sh test-docker.sh