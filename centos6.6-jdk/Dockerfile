FROM registry.cn-hangzhou.aliyuncs.com/xiesen310/centos:6.6
RUN mkdir /opt/java

COPY jdk-8u161-linux-x64.tar.gz /opt/java

RUN tar zxvf /opt/java/jdk-8u161-linux-x64.tar.gz -C /opt/java &&\
	JAVA_HOME=/opt/java/jdk1.8.0_161 &&\
	sed -i "/^PATH/i export JAVA_HOME=$JAVA_HOME" /root/.bash_profile &&\
	sed -i "s%^PATH.*$%&:$JAVA_HOME/bin%g" /root/.bash_profile &&\
	source /root/.bash_profile

