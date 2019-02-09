FROM jtim/docker-docker-compose-jdk:18.09.1-ce-git-compose-1.23.1-openjdk-8u191

USER root

RUN apk add --no-cache curl tar bash procps

# Default to UTF-8 file.encoding
ENV LANG C.UTF-8

ARG MAVEN_VERSION=3.6.0
ENV USER_HOME_DIR="/home/bob-the-builder"

RUN mkdir -p /usr/share/maven /usr/share/maven/ref \
  && curl -fsSL http://apache.osuosl.org/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz \
    | tar -xzC /usr/share/maven --strip-components=1 \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven
ENV MAVEN_M2_DIRECTORY "$USER_HOME_DIR/.m2"

COPY settings.xml $MAVEN_M2_DIRECTORY/settings.xml
RUN mkdir $MAVEN_M2_DIRECTORY/repository
RUN chown -R $USERNAME:$USERNAME $USER_HOME_DIR

USER $USERNAME