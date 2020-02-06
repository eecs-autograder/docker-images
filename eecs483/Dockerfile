FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update
RUN apt-get install -y software-properties-common python3-software-properties

RUN add-apt-repository ppa:ubuntu-toolchain-r/test
RUN apt-get update
RUN apt-get install -y g++-7 flex bison
RUN apt-get install -y spim

RUN update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-7 100


