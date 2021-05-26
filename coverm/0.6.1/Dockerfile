
# base image: Ubuntu
FROM ubuntu:xenial

# File Author / Maintainer
LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="coverM"
LABEL software.version="0.6.1"
LABEL description="This software provides coverM for calculating MAG and contig abundance"
LABEL website="https://github.com/wwood/CoverM"
LABEL license="https://github.com/wwood/CoverM/LICENSE.txt"
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
    && conda install -c conda-forge -c bioconda coverm \
    && conda install seqtk 


