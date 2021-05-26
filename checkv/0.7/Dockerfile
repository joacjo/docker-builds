
# base image: Ubuntu
FROM ubuntu:xenial

# File Author / Maintainer
LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="Checkv"
LABEL software.version="0.7"
LABEL description="This software provides CheckV for viral completeness and contamination estimating"
LABEL website="https://bitbucket.org/berkeleylab/checkv"
LABEL license="https://bitbucket.org/berkeleylab/checkv/LICENSE.txt"
LABEL maintainer="Joachim Johansen"
LABEL maintainer.email="joacjohansen@gmail.com"

ENV PATH=/miniconda/bin:${PATH} \
    LC_ALL=C

# Prepare directory structure
RUN mkdir /app && mkdir /appdownload && mkdir /database

# Install VAMB
RUN apt-get update --fix-missing \
    && apt-get install -y wget gcc pigz tar \
    && wget http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && bash Miniconda3-latest-Linux-x86_64.sh -p /miniconda -b \
    && rm Miniconda3-latest-Linux-x86_64.sh \
    && conda update -y conda \
    && conda install -c conda-forge -c bioconda checkv

