FROM ubuntu:latest

ARG VERSION=0.78

RUN export TZ=America/New_York && \
    export DEBIAN_FRONTEND="noninteractive" && \
    apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    zlib1g-dev \
    netpbm \
    libnetpbm10-dev \
    libjpeg-dev \
    libpng-dev \
    libcairo2-dev \
    libcairo2  \
    swig \
    libbz2-dev \
    libcfitsio-dev \
    sextractor \
    make \
    build-essential \
    wget && \
    #
    ln -s /usr/bin/python3 /usr/bin/python && \
    #
    pip3 install --no-cache-dir numpy astropy && \
    #
    wget http://astrometry.net/downloads/astrometry.net-${VERSION}.tar.gz && \
    tar xvzf astrometry.net-${VERSION}.tar.gz && \
    cd astrometry.net-* && \
    export INSTALL_DIR="/" && \
    sed -i 's/-march=native/-march=x86-64/g' util/makefile.common && \
    make && make extra && make install && \
    #
    wget -r -nd -np -P /data/ "data.astrometry.net/4100/index-4112.fits" && \
    solve-field /examples/apod2.jpg && \
    #
    cd .. && rm -rf astrometry.net* && \
    apt-get remove -y wget make build-essential && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /examples && \
    rm /data/index-4112.fits

WORKDIR /work

ENTRYPOINT [ "solve-field" ]
