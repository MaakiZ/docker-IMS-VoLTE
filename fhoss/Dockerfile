FROM debian:8
MAINTAINER Yan Grunenberger <yan@grunenberger.net>
ENV DEBIAN_FRONTEND noninteractive

RUN echo "deb [trusted=yes] http://archive.debian.org/debian jessie main non-free contrib" > /etc/apt/sources.list && \
    echo "deb-src [trusted=yes] http://archive.debian.org/debian jessie main non-free contrib" >> /etc/apt/sources.list && \
    echo "deb [trusted=yes] http://archive.debian.org/debian-security jessie/updates main non-free contrib" >> /etc/apt/sources.list

RUN apt-get update
RUN apt-get -yq dist-upgrade 
RUN apt-get -yq install git-core
RUN apt-get -qy install openjdk-7-jdk
RUN apt-get -qy install ant
RUN apt-get -qy install subversion
RUN mkdir -p /opt/OpenIMSCore
WORKDIR /opt/OpenIMSCore
RUN git clone --depth 1 --no-single-branch https://github.com/herlesupreeth/FHoSS.git FHoSS
WORKDIR /opt/OpenIMSCore/FHoSS
RUN JAVA_TOOL_OPTIONS=-Dfile.encoding=UTF8 ant compile deploy 
ENTRYPOINT ["/root/run.sh"]