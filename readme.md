# Docker Compositions

Docker compositions for local development:

- [MongoDB](./mongo)
  - [mongo-single](./mongo/mongo-single) - Single mongo node. Best option for local development.
  - [mongo-cluster](./mongo/mongo-cluster) - Mongo cluster of 3 nodes. Best option for development involving cluster issues.
- [Elasticsearch](./elastic) - Elasticseach with Kibana in multiple versions
  - [elastic-kibana-5](./elastic/elastic-kibana-5) - Elastic v5 and Kibana
  - [elastic-kibana-6](./elastic/elastic-kibana-6) - Elastic v6 and Kibana
  - [elastic-kibana-7](./elastic/elastic-kibana-7) - Elastic v7 and Kibana
- [Kafka](./kafka) - Multiple setups of kafka
  - [kafka-single-zk-single](./kafka/kafka-single-zk-single) - Single kafka server and single zookeeper server
  - [kafka-multi-zk-single](./kafka/kafka-multi-zk-single) - Multiple kafka servers and single zookeeper server
  - [kafka-single-zk-multi](./kafka/kafka-single-zk-multi) - Single kafka server and multiple zookeeper servers
  - [kafka-multi-zk-multi](./kafka/kafka-multi-zk-multi) - Multiple kafka servers and multiple zookeeper servers
- [Metrics](./metrics) - Basic metric stack consisting of: StatsD + Graphite + Grafana
- [ELK](./elk) - Basic ELK stack consisting of: Elasticsearch + Logstash + Kibana
- [Nginx](./nginx) - Sample nginx compositions
  - [nginx-forward-cache](./nginx/nginx-forward-cache) - Nginx proxy caching http resources
  - [nginx-static](./nginx/nginx-static) - Nginx configured to serve static content

## Sample usage

Add `bin` folder to `PATH` with `PATH="$PATH:$PWD/bin"`:

```sh
# List available docker compositions
dcomps list
# Start a docker composition
dcomps start mongo
```
