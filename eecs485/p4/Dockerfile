FROM jameslp/eecs485_base:1

USER autograder:autograder
COPY requirements-485-p4.txt .
RUN $PYTHON -m venv env-p4
RUN env-p4/bin/pip install -r requirements-485-p4.txt
USER root:root

RUN rm requirements-485-p4.txt
