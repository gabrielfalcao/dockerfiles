FROM debian:latest

ENV DEBIAN_FRONTEND  noninteractive
ENV PYTHONUNBUFFERED true
ENV VIRTUAL_ENV      /usr/local/virtualenv
ENV PATH             $VIRTUAL_ENV/bin:$PATH

MAINTAINER gabriel@nacaolivre.org

RUN apt-get update
RUN apt-get --yes --no-install-recommends install \
    gcc \
    g++ \
    wget \
    libssl-dev \
    libc6-dev \
    build-essential \
    git \
    make \
    python2.7 \
    time \
    curl \
    unzip \
    libffi-dev \
    mercurial \
    libxml2-dev \
    libxslt1-dev \
    libevent-dev \
    libev-dev \
  && rm -rf /var/lib/apt/lists/*

RUN wget http://nodejs.org/dist/v0.12.2/node-v0.12.2.tar.gz
RUN tar zxf node-v0.12.2.tar.gz
RUN cd node-v0.12.2 && ./configure && make && make install

CMD ["node"]