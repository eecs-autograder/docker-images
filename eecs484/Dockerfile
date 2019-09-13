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

RUN rm jdk-8u211-linux-x64.tar.gz
