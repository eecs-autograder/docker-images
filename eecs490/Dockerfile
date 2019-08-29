FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update
RUN apt-get install -y software-properties-common python3-software-properties

RUN add-apt-repository ppa:plt/racket
RUN add-apt-repository ppa:swi-prolog/stable
RUN add-apt-repository ppa:deadsnakes/ppa
RUN add-apt-repository ppa:ubuntu-toolchain-r/test

RUN apt-get update

RUN apt-get install -y racket swi-prolog python3.7

COPY jdk-8u211-linux-x64.tar.gz .
RUN tar -xf jdk-8u211-linux-x64.tar.gz
RUN mkdir -p /opt
RUN mv jdk1.8.0_211 /opt

ENV PATH /opt/jdk1.8.0_211/bin:$PATH

ENV JAVA_HOME /opt/jdk1.8.0_211

RUN apt-get install -y python3.7-dev
RUN apt-get install wget
RUN wget https://bootstrap.pypa.io/get-pip.py -O /tmp/get-pip.py
RUN python3.7 /tmp/get-pip.py
RUN python3.7 -m pip install numpy

ENV OPENBLAS_NUM_THREADS 1
ENV GOTO_NUM_THREADS 1
ENV OMP_NUM_THREADS 1

ENV JAVA_TOOL_OPTIONS -Xms512m -Xmx512m -XX:+UseSerialGC -XX:MaxMetaspaceSize=256m -XX:CompressedClassSpaceSize=128m

RUN apt-get install -y g++-7

COPY requirements.txt .
RUN python3.7 -m pip install -r requirements.txt
RUN rm requirements.txt

RUN rm jdk-8u211-linux-x64.tar.gz
