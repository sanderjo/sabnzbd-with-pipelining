# Version: 0.0.2
FROM ubuntu:24.04

# Docker image with SABnzbd with PIPELINING

MAINTAINER Sander "superkoning@caiway.net"

ARG DEBIAN_FRONTEND=noninteractive

ENV HOME="/config"

RUN apt update -y && apt upgrade -y

RUN apt install -y python3-pip python3-setuptools git unrar par2 7zip 

# sabctools
RUN cd / && git clone https://github.com/mnightingale/sabctools.git && \
	cd sabctools/ && git checkout origin/feature/streaming_decoder && \
	python3 setup.py install

# sabnzbd
RUN cd / && git clone https://github.com/mnightingale/sabnzbd.git && \
	cd sabnzbd/ && git checkout origin/feature/pipelining && \
	sed -i '/^sabctools/d' requirements.txt && \
	python3 -m pip install -r requirements.txt -U --break-system-packages
	
CMD env LANG=en_US.UTF-8 python3 /sabnzbd/SABnzbd.py -l2 -b0 --server 0.0.0.0:8080

RUN echo 'Hi, I am in your container'

# ports and volumes
EXPOSE 8080
VOLUME /config /downloads /incomplete-downloads


# docker run -p 8080:8080 -v ~/config-sabnzbd-pipelining/:/config/ sanderjo/sabnzbd-pipelining



