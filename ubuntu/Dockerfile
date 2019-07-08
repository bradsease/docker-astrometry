FROM ubuntu:latest

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
    libcfitsio-dev \
    make \
    build-essential \
    wget && \
    #
    pip install --no-cache-dir numpy astropy && \
    #
    wget http://astrometry.net/downloads/astrometry.net-0.78.tar.gz && \
    tar xvzf astrometry.net-0.78.tar.gz && \
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
