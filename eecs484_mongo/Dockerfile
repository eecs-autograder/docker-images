FROM eecsautograder/ubuntu20:latest

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update --fix-missing
RUN apt-get install -y software-properties-common

RUN apt-get update

RUN apt-get install -y unzip wget

RUN add-apt-repository ppa:openjdk-r/ppa
RUN apt-get update
RUN apt-get install -y openjdk-11-jdk
ENV JAVA_HOME /usr/lib/jvm/java-11-openjdk-amd64

ENV MONGO_MAJOR 6.0
ENV MONGO_VERSION 6.0.0

RUN apt-get install -y ca-certificates apt-transport-https
RUN wget -qO - https://www.mongodb.org/static/pgp/server-${MONGO_MAJOR}.asc | apt-key add -
RUN echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/${MONGO_MAJOR} multiverse" | tee /etc/apt/sources.list.d/mongodb-org-${MONGO_MAJOR}.list
RUN apt-get update

RUN apt-get install -y mongodb-org

ENV DATA_DB_DIR /home/autograder/data/db
RUN mkdir -p $DATA_DB_DIR
RUN chown -R autograder:autograder $DATA_DB_DIR

COPY start_mongo.sh /usr/local/bin/start_mongo.sh
RUN chmod +x /usr/local/bin/start_mongo.sh

RUN apt-get install -y jq

RUN apt-get install -y python3-pip
RUN pip3 install deepdiff 
