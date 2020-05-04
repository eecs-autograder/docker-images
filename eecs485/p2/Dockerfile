FROM jameslp/eecs485_base:1

USER autograder:autograder
COPY requirements-485-p2.txt .
RUN $PYTHON -m venv env-p2
RUN env-p2/bin/pip install -r requirements-485-p2.txt
USER root:root

RUN rm requirements-485-p2.txt
