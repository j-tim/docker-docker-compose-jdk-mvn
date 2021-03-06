# Jtim custom Gitlab CI build image with Docker, Docker-compose, OpenJDK 8u252 and Maven 3.6.3

## Supported tags and respective Dockerfile links

### Java 11 (latest)

* Docker version: 20.10.5
* Docker compose: 1.28.6
* Open JDK: 11.0.10_9
* Maven: 3.6.3

Other available development tools:

* Git: 2.25.1
* Jq: jq-1.6
* Pack: 0.18.0+git-e00ee4a.build-2328

### Java 8

* Docker version: 20.10.2
* Docker compose: 1.28.0
* Open JDK: 8u252
* Maven: 3.6.3

Other available development tools:

* Git: 2.26.2
* Jq: jq-master-v20200428-28-g864c859e9d
* Pack: 0.16.0+git-e0f6c50.build-1898

## Supported versions

### Java 11

* `20.10.5-compose-1.28.6-adoptopenjdk-11.0.10_9-maven-3.6.3`, `20.10.5-compose-1.28.6-adoptopenjdk-11-maven-3.6.3`, `maven-3.6.3`, `3.6.3`, [(latest)](https://github.com/j-tim/docker-docker-compose-jdk-mvn/blob/master/3.6.3/adoptopenjdk-11.0.10_9/Dockerfile)

### Java 8

* `20.10.2-compose-1.28.0-openjdk-8u252-maven-3.6.3`, [(openjdk-8u252-maven-3.6.3)](https://github.com/j-tim/docker-docker-compose-jdk-mvn/blob/master/3.6.3/openjdk-8u252/Dockerfile)

## Running as non root

Since version `18.05.0-ce-git-compose-1.21.2-openjdk-8u171-maven-3.5.4` this image is not running as root anymore!

### Deprecated images

* `18.09.1-ce-git-compose-1.23.1-openjdk-8u191-maven-3.6.0`, `maven-3.6.0`, `3.6.0`, [(latest)](https://github.com/j-tim/docker-docker-compose-jdk-mvn/blob/master/3.6.0/Dockerfile)
* `18.05.0-ce-git-compose-1.21.2-openjdk-8u171-maven-3.5.4`, `maven-3.5.4`, [(3.5.4)](https://github.com/j-tim/docker-docker-compose-jdk-mvn/blob/master/3.5.4/Dockerfile)
* `18.01.0-compose-1.18.0-openjdk-8u151-maven-3.5.2`, `maven-3.5.2`, `3.5.2`, [(3.5.2)](https://github.com/j-tim/docker-docker-compose-jdk-mvn/blob/master/3.5.2/Dockerfile)  
* `17.07-compose-1.16.1-openjdk-8u131-maven-3.5.0`, `maven-3.5.0`, `3.5.0`, [(3.5.0)](https://github.com/j-tim/docker-docker-compose-jdk-mvn/blob/master/3.5.0/Dockerfile)  
* `17.04-compose-1.12.0-openjdk-8u121-maven-3.3.9`, `maven-3.3.9`, [(3.3.9)](https://github.com/j-tim/docker-docker-compose-jdk-mvn/blob/master/3.3.9/Dockerfile)  

## Pull the image 

```shell
docker pull jtim/docker-docker-compose-jdk-mvn
```

## How to use the Gitlab Build image

.gitlab-ci.yml

```
stages:
  - maven

maven-docker-job:
  image: jtim/docker-docker-compose-jdk-mvn:18.09.1-ce-git-compose-1.23.1-openjdk-8u191-maven-3.6.0
  stage: maven
  services:
    - docker:dind
  script:
    - whoami
    - docker -v
    - docker-compose -v
    - java -version
    - mvn -v
    - git version
    - jq --version
    - pack --version
```

You don't need to set these variables in your pipeline we already set them in the Docker images:

```yml
variables:
  DOCKER_HOST: tcp://docker:2375
  DOCKER_DRIVER: overlay2
  DOCKER_TLS_CERTDIR: ""
```

## Related images

* [https://hub.docker.com/r/jtim/docker-docker-compose](https://hub.docker.com/r/jtim/docker-docker-compose)
* [https://hub.docker.com/r/jtim/docker-docker-compose-jdk](https://hub.docker.com/r/jtim/docker-docker-compose-jdk)