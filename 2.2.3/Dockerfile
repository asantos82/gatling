#FROM java:openjdk-8-jre

# install gatling
#RUN mkdir -p /tmp/downloads
#RUN curl -sf -o /tmp/downloads/gatling-2.0.1.zip -L http://repo1.maven.org/maven2/io/gatling/highcharts/gatling-charts-highcharts/2.0.1/gatling-charts-highcharts-2.0.1-bundle.zip
#RUN mkdir -p /tmp/archive && cd /tmp/archive && unzip /tmp/downloads/gatling-2.0.1.zip
#RUN mkdir -p /opt/gatling && mv /tmp/archive/gatling-charts-highcharts-2.0.1/* /opt/gatling

#WORKDIR /data

# default command
#CMD ["/bin/bash"]


FROM java:8-jdk

MAINTAINER Denis Vazhenin <denis.vazhenin@me.com>

# working directory for gatling
WORKDIR /opt

# gating version
ENV GATLING_VERSION 2.2.3

# create directory for gatling install
RUN mkdir -p gatling

# install gatling
RUN apt-get -y update && \
  apt-get -y upgrade && \
  apt-get -y install wget && \
  mkdir -p /tmp/downloads && \
  wget -q -O /tmp/downloads/gatling-$GATLING_VERSION.zip \
  https://repo1.maven.org/maven2/io/gatling/highcharts/gatling-charts-highcharts-bundle/$GATLING_VERSION/gatling-charts-highcharts-bundle-$GATLING_VERSION-bundle.zip && \
  mkdir -p /tmp/archive && cd /tmp/archive && \
  unzip /tmp/downloads/gatling-$GATLING_VERSION.zip && \
  mv /tmp/archive/gatling-charts-highcharts-bundle-$GATLING_VERSION/* /opt/gatling/ && \
  rm -rf /tmp/*

# change context to gatling directory
WORKDIR  /opt/gatling

# set directories below to be mountable from host
VOLUME ["/opt/gatling/conf", "/opt/gatling/results", "/opt/gatling/user-files"]

# set environment variables
ENV PATH /opt/gatling/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV GATLING_HOME /opt/gatling

CMD ["/bin/bash"]

