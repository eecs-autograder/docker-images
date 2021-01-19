FROM eecsautograder/ubuntu18:latest

RUN apt-get update --fix-missing && \
    apt-get install -y software-properties-common python3-software-properties \
                       python3-dev python3-pip python3-venv

RUN apt-get install -y libz-dev 
RUN apt-get install -y unzip

# From https://ocaml.org/docs/install.html, Jan 2021
RUN apt-get install -y ocaml-nox
