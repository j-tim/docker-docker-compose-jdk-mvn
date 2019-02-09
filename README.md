# Jtim custom Gitlab CI build image with Docker, Docker-compose, OpenJDK 8u191 and Maven 3.6.0

## Supported tags and respective Dockerfile links

### Latest version

* Docker version: 18.09.1-ce-git
* Docker compose: 1.23.1
* Open JDK: 8u191
* Maven: 3.6.0

Since version `18.05.0-ce-git-compose-1.21.2-openjdk-8u171-maven-3.5.4` this image is not running as root anymore!

* `18.09.1-ce-git-compose-1.23.1-openjdk-8u191-maven-3.6.0`, `maven-3.6.0`, `3.6.0`, [(latest)](https://github.com/j-tim/docker-docker-compose-jdk-mvn/blob/master/3.6.0/Dockerfile)

* `18.05.0-ce-git-compose-1.21.2-openjdk-8u171-maven-3.5.4`, `maven-3.5.4`, [(3.5.4)](https://github.com/j-tim/docker-docker-compose-jdk-mvn/blob/master/3.5.4/Dockerfile)

### Deprecated images

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
```

## Related images

* [https://hub.docker.com/r/jtim/docker-docker-compose](https://hub.docker.com/r/jtim/docker-docker-compose)
* [https://hub.docker.com/r/jtim/docker-docker-compose-jdk](https://hub.docker.com/r/jtim/docker-docker-compose-jdk)