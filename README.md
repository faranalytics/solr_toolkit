# Solr Toolkit

Tools and notes for running a Solr instance.

## Introduction

This repository contains utility functions for working with Solr and notes for running Solr in Docker.

## Solr In Docker on Fedora

### Install Docker

#### Uninstall previous Docker installations.

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

sudo dnf -y install dnf-plugins-core

sudo dnf-3 config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
```

### Run Solr in Docker using Docker Compose

#### Create a docker-compose.yml file.

```yml
version: "3"
services:
  solr:
    image: solr:8.11.4
    ports:
      - "8983:8983"
    volumes:
      - data:/var/solr
    command:
      - solr-precreate
      - gettingstarted
volumes:
  data:
```
#### Use Docker Compose to run a Solr Server.

```bash
sudo docker compose up -d
```

### Docker Volumes

#### List Docker volumes.

```bash
sudo ls -la /var/lib/docker/volumes
```

### Docker Commands

#### Start docker.

```bash
sudo systemctl start docker
```

#### List all images.

```bash
sudo docker image ls -a
```

#### List all containers.

```bash
sudo docker container ls -a
```

#### Remove all containers, images, and volumes.

```bash
sudo docker container rm -f $(sudo docker container ls -qa); sudo docker image rm -f $(sudo docker image ls -qa); sudo docker volume rm -f $(sudo docker volume ls)
```

## References
- `https://solr.apache.org/guide/solr/latest/deployment-guide/solr-in-docker.html`
- `https://docs.docker.com/engine/install/fedora/`