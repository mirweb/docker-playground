FROM ubuntu:latest
LABEL maintainer="mirko@wils.tk"

ENV TERM linux
ENV DEBIAN_FRONTEND noninteractive

RUN set -ex; \
	apt-get update; \
	apt-get install -y \
		w3m w3m-img \
		lynx \
    links2 \
    elinks \
    iputils-ping dnsutils

CMD ["/bin/bash"]
    