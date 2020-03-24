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

RUN apt-get install -y ca-certificates apt-transport-https
RUN wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | apt-key add -
RUN echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.2 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.2.list
RUN apt-get update
RUN apt-get install -y mongodb-org-shell mongodb-org-tools

COPY ojdbc-full.tar.gz .
RUN tar -xf ojdbc-full.tar.gz
RUN mv OJDBC-Full /opt

RUN apt-get install -y junit4
ENV CLASSPATH $CLASSPATH:/usr/share/java/junit4.jar:/opt/OJDBC-Full/ojdbc6.jar

# https://www.oracle.com/database/technologies/instant-client/linux-x86-64-downloads.html#ic_x64_inst
RUN mkdir -p /opt/oracle
COPY instantclient-basiclite-linux.x64-19.3.0.0.0dbru.zip \
     instantclient-sqlplus-linux.x64-19.3.0.0.0dbru.zip \
     instantclient-jdbc-linux.x64-19.3.0.0.0dbru.zip \
     ./
RUN unzip instantclient-basiclite-linux.x64-19.3.0.0.0dbru.zip
RUN unzip instantclient-sqlplus-linux.x64-19.3.0.0.0dbru.zip
RUN unzip instantclient-jdbc-linux.x64-19.3.0.0.0dbru.zip

RUN mv instantclient_19_3 /opt/oracle
RUN apt-get install -y libaio1
ENV LD_LIBRARY_PATH=/opt/oracle/instantclient_19_3:$LD_LIBRARY_PATH
ENV PATH=/opt/oracle/instantclient_19_3:$PATH

RUN rm jdk-8u211-linux-x64.tar.gz \
       ojdbc-full.tar.gz \
       instantclient-basiclite-linux.x64-19.3.0.0.0dbru.zip \
       instantclient-sqlplus-linux.x64-19.3.0.0.0dbru.zip \
       instantclient-jdbc-linux.x64-19.3.0.0.0dbru.zip

RUN apt-get install -y jq

RUN apt-get install -y python3-pip
RUN pip3 install deepdiff 

