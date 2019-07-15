### Topics and Partisions

Messages in Kafka are called Topics. Topics are divided into partions with each message recieving an incremental ID called offsets


When the message is written
By default it is kep for one week

It cannot be altered or changed in anyway

The ID will increment indinetely (never start over at zero)

It is randomely assigned to a partions, unless a key is provided
