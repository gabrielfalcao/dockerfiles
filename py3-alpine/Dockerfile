FROM python:3.6.5-alpine3.7
LABEL maintainer="team-integrations"

RUN echo http://nl.alpinelinux.org/alpine/v3.7/main > /etc/apk/repositories; \
    echo http://nl.alpinelinux.org/alpine/v3.7/community >> /etc/apk/repositories

# base libs for alpine to build most things
RUN apk --update --no-cache add \
    bash \
    bash-completion \
    build-base \
    ca-certificates \
    file \
    libffi-dev

# build image rendering libraries
RUN apk --update --no-cache add \
    freetype-dev \
    jpeg-dev \
    libjpeg-turbo-dev \
    libpng-dev \
    zlib-dev

# build coroutine-based concurrent software
RUN apk --update --no-cache add \
    libev-dev	\
    libevent-dev

# build xml processing libraries
RUN apk --update --no-cache add \
    libxml2-dev \
    libxslt-dev


# python3 only (easily switched to python 2)
RUN apk --update --no-cache add \
    python3 \
    python3-dev

# interactive shell and debugging tools
RUN apk --update --no-cache add \
    htop \
    python3 \
    python3-dev \
    readline-dev \
    vim
