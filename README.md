# kafka

## Kafka console producer example

```sh
kafka-console-producer --topic streams-file-input --broker-list 127.0.0.1:9092
```

## Kafka console consumer example

```sh
kafka-console-consumer --topic streams-file-input --bootstrap-server 127.0.0.1:9092 --from-beginning
```

## Kafka console consumer example with deserialization

```sh
kafka-console-consumer --topic streams-word-count-output --bootstrap-server 127.0.0.1:9092 --from-beginning --formatter kafka.tools.DefaultMessageFormatter --property print.key=true --property print.value=true --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer
```

## List topics in Kafka broker

```sh
kafka-topics --list --bootstrap-server  127.0.0.1:9092  --command-config ~/Documents/kafka-prod.config
```
## Consume messages from topic

```sh
kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --property schema.registry.url=https://schema-reg --topic example_topic --consumer.config ~/Documents/kafka.config --from-beginning --group test1029 --max-messages 10
```

## Get messages remaining in the topic after you create consume a message using consumer group

```sh
kafka-consumer-groups --describe --bootstrap-server 127.0.0.1:9092  --group test1029 --command-config ~/Documents/kafka.config

```

## Consume all messages

```sh
kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --property schema.registry.url=https://schema-reg --topic example_topic --consumer.config ~/Documents/kafka.config --from-beginning --group ESTest 

```

## Create a new topic

```sh
kafka-topics --bootstrap-server 127.0.0.1:9092 --command-config ~/Documents/kafka.config  --create --replication-factor 3 --partitions 1 --topic  example_topic config cleanup.policy=compact --config retention.ms=15552000000  --config max.message.bytes=20971520 

```

## Create a new topic with no compact

```sh
kafka-topics --bootstrap-server 127.0.0.1:9092 --command-config ~/Documents/kafka.config  --create --replication-factor 3 --partitions 5 --topic  example_topic --config  cleanup.policy=delete --config retention.ms=15552000000 —config max.message.bytes=40971520   

```

## Delete a new topic 

```sh
kafka-topics --bootstrap-server 127.0.0.1:9092 --command-config ~/Documents/kafka.config  --delete  --topic example_topic

```

## Count number of messages in topic

```sh
kafkacat -b 127.0.0.1:9092 -t espiq_piqreporting -X security.protocol=SSL -C -e -q | wc -l

```

## Reset offset for a topic and group (Dry run)

```sh
kafka-consumer-groups --group  recon-piq-avro-service-group --bootstrap-server 127.0.0.1:9092 --command-config ~/Documents/kafka.config --reset-offsets --topic example_topic --to-earliest --dry-run

```

## Reset offset for a topic and group (execute)

```sh
kafka-consumer-groups --group  recon-piq-avro-service-group --bootstrap-server 127.0.0.1:9092 --command-config ~/Documents/kafka.config --reset-offsets --topic example_topic --to-earliest --execute
```
