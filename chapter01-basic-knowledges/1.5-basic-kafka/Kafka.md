# Producer

The one who produce the event

When producer produce message 

- With no message id, Randomly assign to a partition
- With message id, same id always go to same partition

### Broker

Server instance that running Kafka

### Topic

A topic that producer produce to and consumer subscribe to

### Partition

A partition of the topic 

Number of partition limit the number of consumer on that topic

2 Partitions -> No more than 2 consumer

# Comsumer

## Consumer Group:

- A group of consumer that subscribe to the same topic but difference partition
- Typically each consumer in consumer group will be only subscribe to 1 partition
- If number of consumer in group < number of partition, one or more consumer will consume more than 1 partition

- Every partition must be consume by at least one consumer

- Rebalance process will occure when number of consumer in consumer group change to ensure  partition consumption

