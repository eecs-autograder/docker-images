FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update --fix-missing
RUN apt-get install -y software-properties-common

COPY jdk-8u211-linux-x64.tar.gz .
RUN mkdir -p /usr/lib/jvm && tar -xzvf jdk-8u211-linux-x64.tar.gz -C /usr/lib/jvm

ENV JAVA_HOME /usr/lib/jvm/jdk1.8.0_211
ENV JAVA_TOOL_OPTIONS -Xms512m -Xmx512m -XX:+UseSerialGC -XX:MaxMetaspaceSize=256m -XX:CompressedClassSpaceSize=128m
RUN update-alternatives --install /usr/bin/java java ${JAVA_HOME%*/}/bin/java 20000
RUN update-alternatives --install /usr/bin/javac javac ${JAVA_HOME%*/}/bin/javac 20000

RUN apt-get install -y unzip

COPY pmd-bin-6.0.1.zip .
RUN unzip pmd-bin-6.0.1.zip
RUN mv pmd-bin-6.0.1 /opt/pmd
RUN cp /opt/pmd/bin/run.sh /opt/pmd/bin/pmd.sh

COPY oclint-0.13-x86_64-linux-4.4.0-93-generic.tar.gz .
RUN tar -xzf oclint-0.13-x86_64-linux-4.4.0-93-generic.tar.gz
RUN mv oclint-0.13 /opt/oclint

COPY cppcheck-1.83.tar.gz .
RUN tar -xzf cppcheck-1.83.tar.gz
RUN mv cppcheck-1.83 /opt/cppcheck
RUN cd /opt/cppcheck && make CFGDIR=/opt/cppcheck/cfg CXXFLAGS="-O2 -DNDEBUG -Wall -Wno-sign-compare -Wno-unused-function"

ENV PATH /opt/oclint/bin:/opt/pmd/bin:/opt/cppcheck:$PATH

RUN rm pmd-bin-6.0.1.zip
RUN rm oclint-0.13-x86_64-linux-4.4.0-93-generic.tar.gz
RUN rm cppcheck-1.83.tar.gz

