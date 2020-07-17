# kafka
kafka


Setup Java

create folders

C:/kafka_2.12-2.5.0/data/zookeeper
C:/kafka_2.12-2.5.0/data/kafka

Edit below in zookeeper.properties
dataDir=C:/kafka_2.12-2.5.0/data/zookeeper

Edit below in server.propeerties
log.dirs=C:/kafka_2.12-2.5.0/data/kafka

Set Path variable for kafka 
  C:/kafka_2.12-2.5.0/bin/windows
  
Start zookeeper
```
  zookeeper-server-start.bat config\zookeeper.propeerties
 ```
Start kafka
  ```
    kafka-server-start.bat config/server.properties
  ```
  NOTE:
  Donot delete any topics , other wise your kafka will crash , There is a bug when you delete the topics.
  
  
#Start with kafka topics
```
Below  has some errors , missing required arguments for partitions
kafka-topics.bat --zookeeper 127.0.0.1:2181 --topic first_topic --create 

Below  has some errors , missing required arguments for replication-factor
kafka-topics.bat --zookeeper 127.0.0.1:2181 --topic first_topic --create --partitions 3

replication factor larger than available broker we have only 1 broker
kafka-topics.bat --zookeeper 127.0.0.1:2181 --topic first_topic --create --partitions 3 --replication-factor 2


kafka-topics.bat --zookeeper 127.0.0.1:2181 --topic first_topic --create --partitions 3 --replication-factor 1

```





