FROM jameslp/eecs285:3

ENV ANDROID_HOME /home/autograder/working_dir/android_sdk
ENV GRADLE_USER_HOME /home/autograder/working_dir/.gradle

USER autograder

COPY android-docker-setup.zip .
RUN unzip android-docker-setup.zip

RUN cd android-docker-setup && make setup compile 

RUN rm -rf android-docker-setup android-docker-setup.zip
USER root

