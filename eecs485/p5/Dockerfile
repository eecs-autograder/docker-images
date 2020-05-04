FROM jameslp/eecs485_base:1

RUN apt-get install -y unzip
USER autograder:autograder

COPY requirements-485-p5.txt .
RUN $PYTHON -m venv env-p5
RUN env-p5/bin/pip install -r requirements-485-p5.txt

COPY package.json .
COPY package-lock.json .
RUN env-p5/bin/pip install nodeenv
RUN env-p5/bin/nodeenv --python-virtualenv
RUN . env-p5/bin/activate && npm install .


RUN wget https://chromedriver.storage.googleapis.com/81.0.4044.69/chromedriver_linux64.zip
RUN unzip chromedriver_linux64.zip
RUN mv chromedriver env-p5/bin
RUN rm chromedriver_linux64.zip

USER root:root
RUN apt-get remove -y unzip


ADD https://dl-ssl.google.com/linux/linux_signing_key.pub .
RUN apt-key add linux_signing_key.pub
RUN sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
RUN apt-get update && apt-get install -y google-chrome-stable

RUN rm linux_signing_key.pub 
RUN rm requirements-485-p5.txt
