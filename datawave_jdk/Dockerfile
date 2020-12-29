FROM azul/zulu-openjdk-centos:8u252

LABEL pull="docker pull alerman/datawave-base-jdk" \
      run="docker run -it alerman/datawave-base-jdk" \
      description="Jboss base with Datawave customizations (Azul Zulu JDK, additional tools installed" \
      name="Jboss Base Image with DATAWAVE customizations" \
      maintainer="Adam Lerman"

USER root


RUN yum -y install deltarpm centos-release-sc && \
    chmod -R 777 /usr/lib/jvm/zulu-8/bin/* && \
    groupadd -r jboss -g 1000 && \
    useradd -u 1000 -r -g jboss -m -d /opt/jboss -s /sbin/nologin -c "JBoss User" jboss && \
    groupadd -r hadoop && \
    useradd -r -g hadoop -m -d /opt/datawave -s /bin/bash -c "DATAWAVE User" datawave && \
    chown -R datawave:hadoop /opt/datawave /opt/jboss && \
    chmod -R ug+rX,o-rx /opt/datawave /opt/jboss

ENV JAVA_VERSION=8 \
    JAVA_UPDATE=252 \
    JAVA_BUILD=1.8.0_252-b14 \
    JAVA_HOME=/usr/lib/jvm/zulu8
LABEL version="1.8.0_252"

RUN yum update -y && \
    yum install -y which less bind-utils net-tools lsof nethogs dstat strace htop iperf iperf3 socat iftop xmlstarlet saxon augeas bsdtar unzip && \
    yum -y erase deltarpm 

WORKDIR /opt/datawave
USER datawave
