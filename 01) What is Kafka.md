## What is Kafka

Kafka is public subscriber messagging system 
Kafka is a hub that all components of an application can plug into to handle many different types of messages.
How Kafka handles those message depends on the delivery semantics chosen. Also, in order to help simplify the format of data,
Kafka offers schemas to help keep it uniform over time.


### Message and schemas
Message delivery can take at least one of the following delivery methods

AT LEASET ONE - A produer can send the same message more than one,.If the message fails ot is not acknowledge the producer 
can send the message again. The consumer may have to eliminate duplicate messages

AT MOST ONE - The Producer send a message once and never retry.If the message fails or is not acknowledged the producer will 
never send the message again

EXCATLY ONE -  Even of a producer sends a message more than onece the consumer will only recieve the message once

Kafka able to sends millions of messges per second. Different consumers may access the same message. 
This allows you to move away from batch processing and scale infinetly. Another benefits is being able to 
utilize the data in real time versus keeeping stting on spanning disk


### Topics and Partisions

Messages in Kafka are called Topics. Topics are divided into partions with each message recieving an incremental ID called offsets


When the message is written
By default it is kept for one week

It cannot be altered or changed in anyway

The ID will increment indinetely (never start over at zero)

It is randomely assigned to a partions, unless a key is provided


## Producers and Consumers

### Producers

Producers are clients,that writes the data to the kafka cluster in order to eventually get consumed
eg : Activity Traking, Log Aggregation


### Consumers

consumer is the application that consumes or read the message. 
The consumer subscribe to one or more topics and read the messages in the order in which they were produced.

Acks : Producers can choose whether to recieve a confirmation of delivery by setting 'acks' (acknowledgements)

Key : Producers specify a key, indicating that a messages will go to the same partitions every time

Consumer Group : To consume multiple consumers aren't read the same message, consumer groups map reads to consumers 


