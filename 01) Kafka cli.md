# Kafka CLI

## create topic kafka 
```
  kafka-topics.sh --zookeeper  127.0.0.1:2181 --topic trip_topic --create --partitions 3 --replication-factor 1
```

## list the topics
```
  kafka-topics.sh --zookeeper 127.0.0.1:2181 --list
```

## describe topics
```
  kafka-topics.sh --zookeeper 127.0.0.1:2181 --topic trip_topic --describe
  Topic:trip_topic        PartitionCount:3        ReplicationFactor:1     Configs:
          Topic: trip_topic       Partition: 0    Leader: 0       Replicas: 0     Isr: 0
          Topic: trip_topic       Partition: 1    Leader: 0       Replicas: 0     Isr: 0
          Topic: trip_topic       Partition: 2    Leader: 0       Replicas: 0     Isr: 0
```

## delete topic
```
 kafka-topics.sh --zookeeper 127.0.0.1:2181 --topic trip_topic2 --delete
 
 Topic trip_topic2 is marked for deletion.
 Note: This will have no impact if delete.topic.enable is not set to true.
```

```
kafka-console-producer.sh  --broker-list 127.0.0.1:9092 --topic trip_topic --producer-property acks=all
```

## send message 

open two terminal one is for producer and other one is for consumer

create a producer
```
  ./kafka-console-producer.sh  --broker-list 127.0.01:9092 --topic trip_topic
>
```
it will prompt console to help to type message and enter

create a consumer
```
  ./kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic trip_topic
```


## consumer groups
```
./kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic trip_topic --group first-application
./kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic trip_topic --group second-application
```

if we send a mesage to group it will appear in two groups 

## describe consumer groups 

```
  ./kafka-consumer-groups.sh --bootstrap-server 127.0.0.1:9092 --describe --group first-application

  TOPIC           PARTITION  CURRENT-OFFSET  LOG-END-OFFSET  LAG             CONSUMER-ID     HOST            CLIENT-ID
  trip_topic      1          12              12              0               -               -               -
  trip_topic      2          13              13              0               -               -               -
  trip_topic      0          12              12              0               -               -               -
```

```
  ./kafka-consumer-groups.sh --bootstrap-server 127.0.0.1:9092 --describe --group second-application

  TOPIC           PARTITION  CURRENT-OFFSET  LOG-END-OFFSET  LAG             CONSUMER-ID     HOST            CLIENT-ID
  trip_topic      1          12              12              0               -               -               -
  trip_topic      2          13              13              0               -               -               -
  trip_topic      0          12              12              0               -               -               -
```

## reset topic offset

```
  /kafka-consumer-groups.sh --bootstrap-server 127.0.0.1:9092  --group first-application  --reset-offsets --to-earliest --execute --topic trip_topic
  TOPIC                          PARTITION  NEW-OFFSET
  trip_topic                     0          0
  trip_topic                     2          0
  trip_topic                     1          0
```


