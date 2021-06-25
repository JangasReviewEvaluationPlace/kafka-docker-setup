# About

This is a kafka docker setup including
- zookeeper
- kafka (Wurstmeister)
- ksql
- schema-registry
- connect


## Connect

Installed Connectors:
- JDBC (Postgres)
- Elasticsearch
- SFTP
- Twitter


## Kafka Cheat-Sheet

1. List all topics of a specific broker
```
opt/kafka/bin/kafka-topics.sh \
  --list \
  --bootstrap-server `broker-list.sh`
```

2. Create Topic
```
opt/kafka/bin/kafka-topics.sh \
	--create \
	--topic <topic_name> \
	[--partitions <partitioncount / default: 1>] \
	[--replication-factor <replicationcount / default: 1>] \
	--bootstrap-server `broker-list.sh`
```
This example won't work with more than 1 partition and 1 replication.
Please do not use this flags for following the example.

3. Delete Topic
```
opt/kafka/bin/kafka-topics.sh \
  --delete \
  --topic <topic_name> \
  --bootstrap-server `broker-list.sh`
```

4. Produce Messages into a topic
```
opt/kafka/bin/kafka-console-producer.sh \
  --topic <topic_name> \
  --broker-list=`broker-list.sh`
```
And now have fun with producing some messages!

5. Consume a topic
```
opt/kafka/bin/kafka-console-consumer.sh --topic <topic_name> \
    [--from-beginning] \
    --bootstrap-server `broker-list.sh`
```
If you've used step 4 before and have produced some messages, you
should receive your messages now. But anyways, just for fun: Keep
your consumer open and open a new terminal where you produce new
messages for your already consumed topic.
