# Kafka

## Producer

The one who produce the event

When producer produce message 

- With no message id, Randomly assign to a partition
- With message id, same id go to same partition

## Broker

Server instance that running Kafka

## Topic

A topic that producer produce to and consumer subscribe to

## Partition

A part of the topic 

Number of partition limit the number of consumer on that topic

2 Partition -> No more than 2 consumer

## Comsumer

## Consumer Group: 

> A group of consumer that subscribe to the same topic but difference partition
>
> If consumer < number of partition -> One or more consumer will consume more than 1 partition

