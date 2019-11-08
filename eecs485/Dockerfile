FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update
RUN apt-get install -y software-properties-common python3-software-properties

RUN apt-get install -y libxml2-dev libxslt1-dev libz-dev wget

RUN add-apt-repository ppa:deadsnakes/ppa && apt-get update
RUN apt-get install -y python3.7

COPY jdk-8u211-linux-x64.tar.gz .
RUN tar -xf jdk-8u211-linux-x64.tar.gz
RUN mkdir -p /opt
RUN mv jdk1.8.0_211 /opt
RUN rm jdk-8u211-linux-x64.tar.gz

ENV PATH /opt/jdk1.8.0_211/bin:$PATH

ENV JAVA_HOME /opt/jdk1.8.0_211
ENV JAVA_TOOL_OPTIONS -Xms512m -Xmx512m -XX:+UseSerialGC -XX:MaxMetaspaceSize=256m -XX:CompressedClassSpaceSize=128m

RUN apt-get update --fix-missing && \
    apt-get install -y python3-wheel python3-setuptools python3.7-dev python3-pip python3.7-venv

RUN apt-get install -y sqlite3

USER autograder:autograder
COPY requirements-485-p1.txt .
RUN python3.7 -m venv env-p1
RUN env-p1/bin/pip install -r requirements-485-p1.txt

COPY requirements-485-p2.txt .
RUN python3.7 -m venv env-p2
RUN env-p2/bin/pip install -r requirements-485-p2.txt

COPY requirements-485-p3.txt .
RUN python3.7 -m venv env-p3
RUN env-p3/bin/pip install -r requirements-485-p3.txt

USER root:root
RUN apt-get install -y unzip

ADD https://dl-ssl.google.com/linux/linux_signing_key.pub .
RUN apt-key add linux_signing_key.pub
RUN sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
RUN apt-get update && apt-get install -y google-chrome-stable

RUN rm linux_signing_key.pub 

USER autograder:autograder
COPY package.json .
COPY package-lock.json .

RUN env-p3/bin/pip install nodeenv
RUN env-p3/bin/nodeenv --python-virtualenv
RUN . env-p3/bin/activate && npm install .

COPY requirements-485-p4.txt .
RUN python3.7 -m venv env-p4
RUN env-p4/bin/pip install -r requirements-485-p4.txt

COPY requirements-485-p5.txt .
RUN python3.7 -m venv env-p5
RUN env-p5/bin/pip install -r requirements-485-p5.txt

RUN env-p5/bin/pip install nodeenv
RUN env-p5/bin/nodeenv --python-virtualenv
RUN . env-p5/bin/activate && npm install .

RUN wget https://chromedriver.storage.googleapis.com/77.0.3865.40/chromedriver_linux64.zip
RUN unzip chromedriver_linux64.zip
RUN cp chromedriver env-p3/bin
RUN mv chromedriver env-p5/bin
RUN rm chromedriver_linux64.zip
USER root:root

ENV hadoop_version 2.8.5
RUN wget http://apache.osuosl.org/hadoop/common/hadoop-${hadoop_version}/hadoop-${hadoop_version}.tar.gz
RUN tar -xvz -C /opt -f hadoop-${hadoop_version}.tar.gz
ENV PATH="/opt/hadoop-${hadoop_version}/bin:${PATH}"
RUN rm hadoop-${hadoop_version}.tar.gz

#RUN chown -R autograder:autograder .
RUN rm requirements-485-p1.txt requirements-485-p2.txt requirements-485-p3.txt requirements-485-p4.txt requirements-485-p5.txt

RUN apt-get install -y libgconf-2-4
RUN chown autograder:autograder package.json package-lock.json
