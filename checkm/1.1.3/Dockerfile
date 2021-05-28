
# base image: Ubuntu
FROM ubuntu:xenial

# File Author / Maintainer
LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="checkM"
LABEL software.version="1.1.3"
LABEL description="This software provides checkM for calculating MAG completeness and quality estimates"
LABEL website="https://github.com/Ecogenomics/CheckM"
LABEL license="https://github.com/Ecogenomics/CheckM/LICENSE.txt"
LABEL maintainer="Joachim Johansen"
LABEL maintainer.email="joacjohansen@gmail.com"

ENV PATH=/miniconda/bin:${PATH} \
    LC_ALL=C

# Install VAMB
RUN apt-get update --fix-missing \
    && apt-get install -y wget gcc pigz tar \
    && wget http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && bash Miniconda3-latest-Linux-x86_64.sh -p /miniconda -b \
    && rm Miniconda3-latest-Linux-x86_64.sh \
    && conda update -y conda \ 
    && conda install pip \
    && conda install -c bioconda hmmer prodigal pplacer \
    && pip3 install numpy matplotlib pysam checkm-genome \
    && conda install -c conda-forge -c bioconda seqtk