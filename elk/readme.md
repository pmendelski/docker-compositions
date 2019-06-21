# Elasticsearch + Logstash + Kibana

A [Docker](docker) composition with:
- [Kibana](kibana)
- [Elasticsearch](elasticsearch)
- [Logstash](logstash)

Used for tracking application logs.
Most configuration was copied from [deviantony/docker-elk](https://github.com/deviantony/docker-elk).

## Exposed ports

- [5601](http://localhost:5601) - Kibana
- [9200](http://localhost:9200) - Elasticsearch HTTP
- [9300](http://localhost:9300) - Elasticsearch TCP transport
- [5000](http://localhost:5000) - Logstash TCP input

## Usage

1. Start the stack `docker-compose up`
2. Upload some logs `nc localhost 5000 < /path/to/logfile.log`
3. Open [Kibana](http://localhost:5601)

[elasticsearch]: https://www.elastic.co/products/elasticsearch
[kibana]: https://www.elastic.co/products/kibana
[logstash]: https://www.elastic.co/products/logstash
[docker]: https://www.docker.com/
