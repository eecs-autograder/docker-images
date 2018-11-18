FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update --fix-missing
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:octave/stable
RUN apt-get update
RUN apt-get install -y octave

ENV OPENBLAS_NUM_THREADS 1
ENV GOTO_NUM_THREADS 1
ENV OMP_NUM_THREADS 1

RUN apt-get install -y liboctave-dev
RUN octave --eval "pkg install -forge image"
