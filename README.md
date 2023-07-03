# Docker Installation


Get the detailed information about the installation from the below-mentioned websites of **Docker**.

[Docker](https://docs.docker.com/)

## Installation on Debain based Operating Systems.

### Set up the Docker repository:

> Download the GPG key for docker

```bash

wget -O - https://download.docker.com/linux/ubuntu/gpg > ./docker.key

gpg --no-default-keyring --keyring ./docker.gpg --import ./docker.key

gpg --no-default-keyring --keyring ./docker.gpg --export > ./docker-archive-keyring.gpg

sudo mv ./docker-archive-keyring.gpg /etc/apt/trusted.gpg.d/

```


> Add the docker repository

```bash

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

```

> Update the repository

```bash

sudo apt update

```


> Install Docker packages.

```bash

# Install a particular version
sudo apt install -y docker-ce=5:20.10.7~3-0~ubuntu-$(lsb_release -cs)

# Or install the latest version
sudo apt install docker-ce
```


> Add user to docker group
```bash
# Restart the machine once the user is added to the docker group
sudo usermod -aG docker $USER
```

> Check the installation
```bash

# node:alpine image will download.
docker pull node:alpine
```


## Instalaltion on Fedora Operating System

> Uninstall the old versions
```bash
sudo dnf remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
```

### Setup the repository
```bash
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo

```

### Install docker engine.
```bash
# Install the latest version
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Install a specific version
dnf list docker-ce --showduplicates | sort -r
```

### Start the docker engine
```bash
# Start
sudo systemctl start docker

# Enable
sudo systemctl enable docker.service
sudo systemctl enable containerd.service

```

### Create a group for docker
```bash
# Create a group
sudo groupadd docker

# Add current user to docker group
sudo usermod -aG docker $USER

```

### Run the hello-world sample app
```bash
docker run hello-world
```

## Installation on CentOS Operating System

> Uninstall the old version
```bash
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

> Install the yum-utils package 

```bash

sudo yum install -y yum-utils

```


### Set up the Docker repository:

> Add the repository

```bash

sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

> Install docker and containerd

```bash

sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```


### Start and enable the Docker service

> Start docker

```bash

sudo systemctl start docker

```


> Enable docker start at boot

```bash

sudo systemctl enable docker

```


> Disable docker start at boot

```bash

sudo systemctl disable docker

```


> Check docker service

```bash

sudo systemctl status docker

```


> Add user to docker group
```bash

# Restart the machine once the user is added to docker group
sudo usermod -aG docker $USER
```


> Check the installation
```bash

# hello-world image will be downloaded
docker run hello-world
```
