
# base image: Ubuntu
FROM ubuntu:xenial

# File Author / Maintainer
LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="vamb"
LABEL software.version="3.0.2"
LABEL description="This software provides VAMB for metagenomic contig binning"
LABEL website="https://github.com/RasmussenLab/vamb"
LABEL license="https://github.com/RasmussenLab/vamb/blob/master/LICENSE"
LABEL maintainer="Joachim Johansen"
LABEL maintainer.email="joacjohansen@gmail.com"

ENV PATH=/miniconda/bin:${PATH} \
    LC_ALL=C

# Prepare directory structure
RUN mkdir /app && mkdir /appdownload

# Install VAMB
RUN apt-get update --fix-missing \
    && apt-get install -y wget gcc \
    && wget http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && bash Miniconda3-latest-Linux-x86_64.sh -p /miniconda -b \
    && rm Miniconda3-latest-Linux-x86_64.sh \
    && conda update -y conda \
    && conda install -c anaconda -y python=3.8.2 \
    && conda install -c bioconda metabat2 samtools \
    && conda install pip \
    && conda install -c pytorch pytorch torchvision cudatoolkit=10.2 \
    && pip install numpy==1.19.5 torch==1.7.1 pysam==0.16.0.1 \
    	 torchvision==0.8.2 typing_extensions==3.7.4.3 Pillow==8.1.0 \
	 https://github.com/RasmussenLab/vamb/archive/3.0.2.zip

COPY write_concat_bins.py /app

