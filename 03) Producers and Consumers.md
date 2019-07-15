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
