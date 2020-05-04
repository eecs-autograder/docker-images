FROM jameslp/eecs485_base:1

USER autograder:autograder
COPY requirements-485-p1.txt .
RUN $PYTHON -m venv env-p1
RUN env-p1/bin/pip install -r requirements-485-p1.txt
USER root:root

RUN rm requirements-485-p1.txt
