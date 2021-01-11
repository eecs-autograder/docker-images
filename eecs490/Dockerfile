FROM eecsautograder/ubuntu18:latest 

RUN apt-get update
RUN apt-get install -y software-properties-common 

RUN add-apt-repository ppa:plt/racket
RUN add-apt-repository ppa:swi-prolog/stable
RUN add-apt-repository ppa:deadsnakes/ppa
RUN add-apt-repository ppa:ubuntu-toolchain-r/test

RUN apt-get update

RUN apt-get install -y racket swi-prolog

ENV PYTHON=python3.9

# Don't prompt for timezone when installing tzdata as dependency
RUN DEBIAN_FRONTEND="noninteractive" apt-get install -y $PYTHON-distutils $PYTHON-dev $PYTHON

RUN $PYTHON -m pip install --upgrade pip
RUN $PYTHON -m pip install --upgrade setuptools
RUN $PYTHON -m pip install numpy

RUN apt-get install -y g++-7

COPY requirements.txt .
RUN $PYTHON -m pip install --no-cache-dir -r requirements.txt
RUN rm requirements.txt

