FROM jameslp/eecs498_data_mining

RUN apt-get update && apt-get install -y ssh rsync
COPY hadoop_configs/* /opt/hadoop-2.7.6/etc/hadoop/ 
RUN ls -la /opt/hadoop-2.7.6/etc/hadoop && cat /opt/hadoop-2.7.6/etc/hadoop/core-site.xml

RUN ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa
RUN cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
RUN chmod 0600 ~/.ssh/authorized_keys

RUN hdfs namenode -format
COPY ssh_config /root/.ssh/config
RUN apt-get install -y vim
RUN apt-get install -y git sudo
RUN apt-get install -y p7zip-full p7zip-rar
RUN apt-get install -y net-tools
ENTRYPOINT echo "127.0.0.1	$(cat /etc/hostname)" >> /etc/hosts && cat /etc/hosts && service ssh start && /opt/hadoop-2.7.6/sbin/start-dfs.sh && hdfs dfs -mkdir /user && hdfs dfs -mkdir /user/root && hdfs dfs -mkdir /user/autograder && hdfs dfs -chown autograder /user/autograder && hdfs dfs -chmod 777 / && /opt/hadoop-2.7.6/sbin/start-yarn.sh && touch /startup-complete && echo "Startup complete!" && bash
