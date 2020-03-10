FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update --fix-missing
RUN apt-get install -y software-properties-common

RUN apt-get update

RUN apt-get install -y unzip wget

ENV MONGO_MAJOR 3.6
ENV MONGO_VERSION 3.6.8

RUN apt-get install -y ca-certificates apt-transport-https
RUN wget -qO - https://www.mongodb.org/static/pgp/server-${MONGO_MAJOR}.asc | apt-key add -
RUN echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/${MONGO_MAJOR} multiverse" | tee /etc/apt/sources.list.d/mongodb-org-${MONGO_MAJOR}.list
RUN apt-get update
#RUN apt-get install -y mongodb-org

RUN apt-get install -y \
        mongodb-org=${MONGO_VERSION} \
        mongodb-org-server=${MONGO_VERSION} \
        mongodb-org-shell=${MONGO_VERSION} \
        mongodb-org-mongos=${MONGO_VERSION} \
        mongodb-org-tools=${MONGO_VERSION}

ENV DATA_DB_DIR /home/autograder/data/db
RUN mkdir -p $DATA_DB_DIR
RUN chown -R autograder:autograder $DATA_DB_DIR

COPY start_mongo.sh /usr/local/bin/start_mongo.sh
RUN chmod +x /usr/local/bin/start_mongo.sh

RUN apt-get install -y jq
