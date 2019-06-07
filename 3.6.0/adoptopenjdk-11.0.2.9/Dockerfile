FROM jtim/docker-docker-compose-jdk:18.09.3-ce-git-compose-1.23.2-adoptopenjdk-11.0.2.9

USER root

RUN apt install curl tar procps

ARG MAVEN_VERSION=3.6.0
ENV USER_HOME_DIR="/home/bob-the-builder"

RUN mkdir -p /usr/share/maven /usr/share/maven/ref \
  && curl -fsSL https://repo.maven.apache.org/maven2/org/apache/maven/apache-maven/$MAVEN_VERSION/apache-maven-$MAVEN_VERSION-bin.tar.gz | tar -xzC /usr/share/maven --strip-components=1 \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven
ENV MAVEN_M2_DIRECTORY "$USER_HOME_DIR/.m2"

COPY settings.xml $MAVEN_M2_DIRECTORY/settings.xml
RUN mkdir $MAVEN_M2_DIRECTORY/repository
RUN chown -R $USERNAME:$USERNAME $USER_HOME_DIR

USER $USERNAME