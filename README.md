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



## Installation on CentOS 8 Operating System


> Install the yum-utils package 

```bash

sudo yum install -y yum-utils

```


### Set up the Docker repository:

> Add the repository

```bash

sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

```


> Update the repository

```bash

sudo yum update -y --nobest

```


> Install docker and containerd

```bash

sudo yum install docker-ce docker-ce-cli containerd.io --nobest --allowerasing

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

# node:alpine image will be downloaded
docker pull node:alpine
```
