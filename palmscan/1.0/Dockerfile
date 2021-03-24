# Palmscan
# https://github.com/rcedgar/palmscan
# v1.0

# base image: Ubuntu
FROM ubuntu:xenial

# File Author / Maintainer
LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="palmscan"
LABEL software.version="1.0"
LABEL description="This software provides palmscan for RdRp identification in sequences"
LABEL website="https://github.com/rcedgar/palmscan"
LABEL license="https://github.com/rcedgar/palmscan/blob/main/LICENSE"
LABEL maintainer="Joachim Johansen"
LABEL maintainer.email="joacjohansen@gmail.com"

ENV PATH=/miniconda/bin:${PATH} \
    LC_ALL=C

RUN apt-get update --fix-missing \
    && apt-get install -y wget gcc gzip unzip tar prodigal hmmer \
    && wget http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && bash Miniconda3-latest-Linux-x86_64.sh -p /miniconda -b \
    && rm Miniconda3-latest-Linux-x86_64.sh \
    && conda update -y conda \
    && conda install -c bioconda -c conda-forge pip git

RUN chmod u+x /palmscan/bin/palmscan
RUN git clone https://github.com/rcedgar/palmscan
ENV PATH="/palmscan/bin:${PATH}" 
