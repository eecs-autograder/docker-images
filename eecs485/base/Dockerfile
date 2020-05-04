FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update
RUN apt-get install -y software-properties-common python3-software-properties

RUN apt-get install -y libxml2-dev libxslt1-dev libz-dev wget

ENV PYTHON python3.8

RUN add-apt-repository ppa:deadsnakes/ppa && apt-get update
RUN apt-get install -y $PYTHON

RUN apt-get update --fix-missing && \
    apt-get install -y python3-wheel python3-setuptools $PYTHON-dev python3-pip $PYTHON-venv

RUN apt-get install -y sqlite3
RUN apt-get install -y netcat

RUN apt-get install -y openjdk-8-jdk
ENV JAVA_TOOL_OPTIONS -Xms512m -Xmx512m -XX:+UseSerialGC -XX:MaxMetaspaceSize=256m -XX:CompressedClassSpaceSize=128m
