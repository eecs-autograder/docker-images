FROM jameslp/autograder-sandbox:3.1.0

RUN apt-get update
RUN apt-get install -y software-properties-common python3-software-properties

RUN add-apt-repository ppa:deadsnakes/ppa
RUN add-apt-repository ppa:webupd8team/java && apt-get update

RUN apt-get update

RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
    apt-get install -y oracle-java8-installer
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

ENV OPENBLAS_NUM_THREADS 1
ENV GOTO_NUM_THREADS 1
ENV OMP_NUM_THREADS 1

ENV JAVA_TOOL_OPTIONS -Xms512m -Xmx512m -XX:+UseSerialGC -XX:MaxMetaspaceSize=256m -XX:CompressedClassSpaceSize=128m

ENV hadoop_version 2.7.6
RUN wget http://apache.osuosl.org/hadoop/common/hadoop-${hadoop_version}/hadoop-${hadoop_version}.tar.gz
RUN tar -xvz -C /opt -f hadoop-${hadoop_version}.tar.gz
ENV PATH="/opt/hadoop-${hadoop_version}/bin:${PATH}"
RUN rm hadoop-${hadoop_version}.tar.gz

RUN apt-get install -y python3.6 python3.6-dev
RUN wget https://bootstrap.pypa.io/get-pip.py -O /tmp/get-pip.py
RUN python3.6 /tmp/get-pip.py

RUN wget https://repo.anaconda.com/archive/Anaconda3-5.2.0-Linux-x86_64.sh -O /tmp/anaconda.sh
RUN bash /tmp/anaconda.sh -b -p /opt/anaconda3

ENV PATH /opt/anaconda3/bin:$PATH
