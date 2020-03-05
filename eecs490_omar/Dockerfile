FROM jameslp/autograder-sandbox:3.1.2

RUN apt-get update
RUN apt-get install -y software-properties-common python3-software-properties
RUN apt-get install curl

RUN bash -c "curl https://sh.rustup.rs -sSf > rust.sh"
RUN sh rust.sh -y
RUN rm rust.sh
