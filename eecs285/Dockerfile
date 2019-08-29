FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update --fix-missing
RUN apt-get install -y software-properties-common

RUN apt-get update

COPY jdk-8u211-linux-x64.tar.gz .
RUN tar -xf jdk-8u211-linux-x64.tar.gz
RUN mkdir -p /opt
RUN mv jdk1.8.0_211 /opt

ENV PATH /opt/jdk1.8.0_211/bin:$PATH

ENV JAVA_HOME /opt/jdk1.8.0_211
ENV JAVA_TOOL_OPTIONS -Xms512m -Xmx512m -XX:+UseSerialGC -XX:MaxMetaspaceSize=256m -XX:CompressedClassSpaceSize=128m

RUN apt-get install -y unzip wget

RUN wget https://github.com/pmd/pmd/releases/download/pmd_releases%2F6.8.0/pmd-bin-6.8.0.zip
RUN unzip pmd-bin-6.8.0.zip
RUN rm pmd-bin-6.8.0.zip
RUN mv pmd-bin-6.8.0 /opt/pmd
RUN cp /opt/pmd/bin/run.sh /opt/pmd/bin/pmd.sh

RUN wget https://github.com/checkstyle/checkstyle/releases/download/checkstyle-8.13/checkstyle-8.13-all.jar
RUN mkdir -p /opt/checkstyle
RUN mv checkstyle-8.13-all.jar /opt/checkstyle
COPY checkstyle /opt/checkstyle/
RUN chmod a+x /opt/checkstyle/checkstyle

ENV PATH /opt/checkstyle:/opt/pmd/bin:$PATH

RUN apt-get install -y junit4
ENV CLASSPATH $CLASSPATH:/usr/share/java/junit4.jar

RUN rm jdk-8u211-linux-x64.tar.gz
