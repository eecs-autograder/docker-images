FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update
RUN apt-get install -y software-properties-common python3-software-properties

COPY jdk-8u211-linux-x64.tar.gz .
RUN tar -xf jdk-8u211-linux-x64.tar.gz
RUN mkdir -p /opt
RUN mv jdk1.8.0_211 /opt

ENV PATH /opt/jdk1.8.0_211/bin:$PATH
ENV JAVA_HOME /opt/jdk1.8.0_211
ENV JAVA_TOOL_OPTIONS -Xms512m -Xmx512m -XX:+UseSerialGC -XX:MaxMetaspaceSize=256m -XX:CompressedClassSpaceSize=128m
RUN rm jdk-8u211-linux-x64.tar.gz
