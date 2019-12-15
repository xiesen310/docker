## commad
 docker run -itd --name kafka -h kafka -p9092:9092 --link zookeeper  kakfa:1.1.1 bash
 docker build -t kakfa:1.1.1 .
 docker stop kafka 
