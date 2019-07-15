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



