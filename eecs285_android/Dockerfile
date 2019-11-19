FROM jameslp/eecs285:1

ENV ANDROID_HOME /home/autograder/working_dir/android_sdk
ENV GRADLE_USER_HOME /home/autograder/working_dir/.gradle

COPY android-docker-setup.zip .
RUN unzip android-docker-setup.zip

RUN cd android-docker-setup && make setup compile 

RUN rm -rf android-docker-setup android-docker-setup.zip
RUN chown -R autograder:autograder .

