FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update
RUN apt-get install -y software-properties-common python3-software-properties

RUN add-apt-repository ppa:deadsnakes/ppa

RUN apt-get update

COPY jdk-8u211-linux-x64.tar.gz .
RUN tar -xf jdk-8u211-linux-x64.tar.gz
RUN mkdir -p /opt
RUN mv jdk1.8.0_211 /opt

ENV PATH /opt/jdk1.8.0_211/bin:$PATH

ENV JAVA_HOME /opt/jdk1.8.0_211
ENV JAVA_TOOL_OPTIONS -Xms512m -Xmx512m -XX:+UseSerialGC -XX:MaxMetaspaceSize=256m -XX:CompressedClassSpaceSize=128m

RUN rm jdk-8u211-linux-x64.tar.gz

ENV OPENBLAS_NUM_THREADS 1
ENV GOTO_NUM_THREADS 1
ENV OMP_NUM_THREADS 1

ENV hadoop_version 2.8.5
RUN apt-get install -y wget
RUN wget http://apache.osuosl.org/hadoop/common/hadoop-${hadoop_version}/hadoop-${hadoop_version}.tar.gz
RUN tar -xvz -C /opt -f hadoop-${hadoop_version}.tar.gz
ENV PATH="/opt/hadoop-${hadoop_version}/bin:${PATH}"
RUN rm hadoop-${hadoop_version}.tar.gz

RUN apt-get install -y python3.6 python3.6-dev
RUN wget https://bootstrap.pypa.io/get-pip.py -O /tmp/get-pip.py
RUN python3.6 /tmp/get-pip.py

RUN apt-get install -y python3.7 python3.7-dev
RUN wget https://bootstrap.pypa.io/get-pip.py -O /tmp/get-pip.py
RUN python3.7 /tmp/get-pip.py

RUN wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh -O /tmp/anaconda.sh
RUN bash /tmp/anaconda.sh -b -p /opt/anaconda3

ENV PATH /opt/anaconda3/bin:$PATH
