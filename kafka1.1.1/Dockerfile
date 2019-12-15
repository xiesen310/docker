FROM registry.cn-hangzhou.aliyuncs.com/xiesen310/centos6.6-jdk:latest

RUN mkdir /opt/kafka

ENV KAFKA_VERSION "1.1.1"

COPY kafka_2.11-1.1.1.tgz /opt/kafka

RUN tar zxvf /opt/kafka/kafka*.tgz -C /opt/kafka &&\
	sed -i 's/num.partitions.*$/num.partitions=3/g' /opt/kafka/kafka_2.11-$KAFKA_VERSION/config/server.properties

RUN rm -rf /opt/kafka/kafka_2.11-1.1.1.tgz

RUN echo "source /root/.bash_profile" > /opt/kafka/start.sh &&\
	echo "cd /opt/kafka/kafka_2.11-"$KAFKA_VERSION >> /opt/kafka/start.sh &&\
	echo "sed -i 's%zookeeper.connect=.*$%zookeeper.connect=zookeeper:2181%g'  /opt/kafka/kafka_2.11-"$KAFKA_VERSION"/config/server.properties" >> /opt/kafka/start.sh &&\
	echo "bin/kafka-server-start.sh config/server.properties" >> /opt/kafka/start.sh &&\
	chmod a+x /opt/kafka/start.sh

EXPOSE 9092

ENTRYPOINT ["sh", "/opt/kafka/start.sh"]
