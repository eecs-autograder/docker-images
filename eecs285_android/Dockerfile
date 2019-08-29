FROM jameslp/eecs285:1

COPY p4-budget.zip .
RUN unzip p4-budget.zip
RUN wget https://dl.google.com/android/repository/sdk-tools-linux-4333796.zip
RUN unzip -d /opt/android_sdk sdk-tools-linux-4333796.zip
RUN cd p4-budget && yes | /opt/android_sdk/tools/bin/sdkmanager "platform-tools" "platforms;android-28" "build-tools;28.0.3"

ENV ANDROID_HOME /opt/android_sdk
ENV GRADLE_USER_HOME /home/autograder/working_dir/.gradle
RUN cd p4-budget && make test 

RUN rm -rf sdk-tools-linux-4333796.zip p4-budget.zip p4-budget

RUN chown -R autograder .

