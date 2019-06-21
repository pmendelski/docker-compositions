# Kafka + Zookeeper

A [Docker](docker) composition with:
- [Kafka](kafka)
- [Zookeeper](zookeeper)

Most configuration was copied from [simplesteph/kafka-stack-docker-compose](https://github.com/simplesteph/kafka-stack-docker-compose).

## Configurations

- [kafka-single-zk-single](./kafka-single-zk-single) - Single kafka server and single zookeeper server
- [kafka-multi-zk-single](./kafka-multi-zk-single) - Multiple kafka servers and single zookeeper server
- [kafka-single-zk-multi](./kafka-single-zk-multi) - Single kafka server and multiple zookeeper servers
- [kafka-multi-zk-multi](./kafka-multi-zk-multi) - Multiple kafka servers and multiple zookeeper servers

## Exposed ports

- Zookeeper ports starts from: 2181
- Kafka ports starts from: 9092

## Sample usage

```sh
cd kafka-single-zk-single
docker-compose up
# Create topic
kafka-topics.sh --create --topic test --replication-factor 1 --partitions 12 --zookeeper $DOCKER_HOST_IP:2181
# Produce 100 events
for x in {1..100}; do echo $x; done | kafka-console-producer.sh --broker-list $DOCKER_HOST_IP:9092 --topic test
# Consume events
kafka-console-consumer.sh --bootstrap-server $DOCKER_HOST_IP:9092 --topic test --from-beginning --timeout-ms 20000
```

You can also do it in two separate terminals.
One for producer:
```sh
kafka-console-producer.sh --broker-list $DOCKER_HOST_IP:9092 --topic test
```

Secons one for consumer:
```sh
kafka-console-consumer.sh --bootstrap-server $DOCKER_HOST_IP:9092 --topic test
```
