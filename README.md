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


How do we know that topic has been created?
```
kafka-topics --zookeeper 127.0.0.1:2181 --list
```

Information about the topic created:
```
kafka-topics --zookeeper 127.0.0.1:2181 --topic <topicname> describe
```

```
C:\kafka_2.12-2.5.0>kafka-topics --zookeeper 127.0.0.1:2181 --topic first_topic
--describe
Topic: first_topic      PartitionCount: 3       ReplicationFactor: 1    Configs:

        Topic: first_topic      Partition: 0    Leader: 0       Replicas: 0
Isr: 0
        Topic: first_topic      Partition: 1    Leader: 0       Replicas: 0
Isr: 0
        Topic: first_topic      Partition: 2    Leader: 0       Replicas: 0
Isr: 0
```


```
Create 2nd topic

kafka-topics.bat --zookeeper 127.0.0.1:2181 --topic seccond_topic --create --partitions 3 --replication-factor 1


```


```
Delete topic

kafka-topics --zookeeper 127.0.0.1:2181 --topic first_topic --delete

NOTE:

In windows there is a bug if you delete topic , the kafka crashes , so dont delete
Bug:1194

```


```
produce messsages

kafka-console-producer.bat --broker-list 127.0.0.1:9092 --topic first_topic

```


```
C:\kafka_2.12-2.5.0>kafka-console-producer.bat --broker-list 127.0.0.1:9092 --to
pic first_topic
>hello dhana
>learning kafka
>another messsage
>:-)
>Terminate batch job (Y/N)? y

C:\kafka_2.12-2.5.0>

```

