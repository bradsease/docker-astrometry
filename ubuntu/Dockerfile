from ubuntu:latest

RUN apt-get update && apt-get install -y \
    python \
    python-pip \
    zlib1g-dev \
    netpbm \
    libnetpbm10-dev \
    libjpeg-dev \
    libpng-dev \
    libcairo2-dev \
    libcairo2  \
    swig \
    libbz2-dev \
    libcfitsio-dev && \

    apt-get install -y --no-install-recommends \
    make \
    build-essential \
    wget && \

    pip install --no-cache-dir numpy astropy && \

    wget http://astrometry.net/downloads/astrometry.net-0.78.tar.gz && \
    tar xvzf astrometry.net-0.78.tar.gz && \
    cd astrometry.net-* && \
    export INSTALL_DIR="/" && \
    make && make extra && make install && \

    cd .. && rm -rf astrometry.net* && \
    apt-get remove -y wget make build-essential && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/*
