# Dockerizing Kannel: Dockerfile for building Kannel images
# Based on ubuntu:latest, this is the base for bearerbox and smsbox

# Format: FROM    repository[:version]
FROM ubuntu:precise

# Format: MAINTAINER Name <email@addr.ess>
MAINTAINER Jdub

RUN apt-get update && apt-get install -y \
    bison \
    wget \
    build-essential \
    libxml2-dev \
    libssl-dev

# Fetch Kannel version 1.4.4
RUN wget -q -O - http://kannel.org/download/1.4.4/gateway-1.4.4.tar.gz | tar -xzf - -C /opt

# Build Kannel
WORKDIR /opt/gateway-1.4.4
RUN ./configure --prefix=/usr --sysconfdir=/etc/kannel
RUN touch .depend
RUN make
RUN make install

# Cleanup build
WORKDIR /opt
RUN rm -Rf gateway-1.4.4

# Add config file
ADD kannel.conf /etc/kannel/kannel.conf

RUN mkdir -p /var/log/kannel
RUN mkdir -p /var/spool/kannel

# Setup volumes
VOLUME /var/log/kannel
VOLUME /var/spool/kannel

WORKDIR /usr/sbin
