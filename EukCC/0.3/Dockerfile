# base image: Ubuntu
FROM ubuntu:xenial

# File Author / Maintainer
LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="EukCC"
LABEL software.version="0.3"
LABEL description="Eukaryotic MAG estimate"
LABEL website="https://github.com/Finn-Lab/EukCC"
LABEL license="https://github.com/Finn-Lab/EukCC/LICENSE.txt"
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
    && pip install EukRep \
    && conda install -c bioconda  -c conda-forge eukcc \
    && apt install -y cpanminus make gcc dialog \
    && cpanm inc::Module::Install::DSL Hash::Merge MCE::Mutex FindBin Test::Pod Logger::Simple Parallel::ForkManager.pm YAML

RUN wget http://topaz.gatech.edu/GeneMark/tmp/GMtool_jRNgT/gmes_linux_64.tar.gz
RUN wget http://topaz.gatech.edu/GeneMark/tmp/GMtool_jRNgT/gm_key_64.gz
RUN zcat gm_key_64.gz > ~/gm_key
RUN tar -xzvf gmes_linux_64.tar.gz
RUN cp gmes_linux_64/get_sequence_from_GTF.pl /usr/bin \
    && cp gmes_linux_64/gmes.cfg /usr/bin/ \
    && cp gmes_linux_64/gmes_petap.pl /usr/bin \
    && cp gmes_linux_64/gmhmme3 /usr/bin/