FROM alpine:3.7

ENV LC_ALL       C.UTF-8
ENV LANG         C.UTF-8


#   ___  _       _
#  / _ \| |     (_)
# / /_\ \ |_ __  _ _ __   ___
# |  _  | | '_ \| | '_ \ / _ \
# | | | | | |_) | | | | |  __/
# \_| |_/_| .__/|_|_| |_|\___|
#         | |
#         |_|


# Alpine Setup
# ------------
RUN echo http://nl.alpinelinux.org/alpine/v3.7/main > /etc/apk/repositories; \
    echo http://nl.alpinelinux.org/alpine/v3.7/community >> /etc/apk/repositories

RUN apk update

# base libs for
RUN apk --update --no-cache add \
    bash \
    bash-completion \
    binutils-gold \
    build-base \
    ca-certificates \
    curl\
    file \
    freetype-dev \
    g++ \
    gcc \
    gnupg \
    jpeg-dev \
    libev-dev	\
    libevent-dev \
    libffi-dev \
    libjpeg-turbo-dev \
    libpng-dev \
    libstdc++ \
    libxml2-dev \
    libxslt-dev \
    libzmq \
    linux-headers \
    make \
    openssl-dev \
    zeromq \
    zeromq-dev \
    zlib \
    zlib-dev

# interactive shell and debugging tools
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
RUN apk --update --no-cache add \
    htop \
    vim \
    tree \
    rsync


# ______      _   _                   _____
# | ___ \    | | | |                 |____ |
# | |_/ /   _| |_| |__   ___  _ __       / /
# |  __/ | | | __| '_ \ / _ \| '_ \      \ \
# | |  | |_| | |_| | | | (_) | | | | .___/ /
# \_|   \__, |\__|_| |_|\___/|_| |_| \____/
#        __/ |
#       |___/

ENV PYTHONUNBUFFERED true

RUN apk --update --no-cache add \
    python3 \
    python3-dev \
    python3-tkinter

COPY ./python/get-pip.py /tmp/get-pip.py
RUN python3 /tmp/get-pip.py

RUN pip install -U pip
RUN pip install -U pipenv


#  _   _           _          ___ _____
# | \ | |         | |        |_  /  ___|
# |  \| | ___   __| | ___      | \ `--.
# | . ` |/ _ \ / _` |/ _ \     | |`--. \
# | |\  | (_) | (_| |  __/ /\__/ /\__/ /
# \_| \_/\___/ \__,_|\___| \____/\____/


ENV NODE_VERSION=v9.11.1

# For base builds
ENV NODE_CONFIG_FLAGS="--fully-static" DEL_PKGS="libstdc++" RM_DIRS=/usr/include


RUN for server in ipv4.pool.sks-keyservers.net keyserver.pgp.com ha.pool.sks-keyservers.net; do \
    gpg --keyserver $server --recv-keys \
      94AE36675C464D64BAFA68DD7434390BDBE9B9C5 \
      FD3A5288F042B6850C66B31F09FE44734EB7990E \
      71DCFD284A79C3B38668286BC97EC7A07EDE3FC1 \
      DD8F2338BAE7501E3DD5AC78C273792F7D83545D \
      C4F0DFFF4E8C1A8236409D08E73BC641CC11F4C8 \
      B9AE9905FFD7803F25714661B63B535A4C206CA9 \
      56730D5401028683275BD23C23EFEFE93C4CFFFE \
      77984A986EBC2AA786BC0F66B01FBB92821C587A && break; \
  done && \
  curl -sfSLO https://nodejs.org/dist/${NODE_VERSION}/node-${NODE_VERSION}.tar.xz && \
  curl -sfSL https://nodejs.org/dist/${NODE_VERSION}/SHASUMS256.txt.asc | gpg --batch --decrypt | \
    grep " node-${NODE_VERSION}.tar.xz\$" | sha256sum -c | grep ': OK$' && \
  tar -xf node-${NODE_VERSION}.tar.xz && \
  cd node-${NODE_VERSION} && \
  ./configure --prefix=/usr ${NODE_CONFIG_FLAGS} && \
  make -j$(getconf _NPROCESSORS_ONLN) && \
  make install

RUN npm upgrade -g npm
RUN npm install -g jslint jsonlint jsdoc yarn
