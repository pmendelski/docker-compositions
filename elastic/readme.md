# Elasticsearch + Kibana

A [Docker](docker) composition with:
- [Kibana](kibana)
- [Elasticsearch](elasticsearch)
- [Morfologik Polish Lemmatizer](morfologik)

## Configurations
- [elastic-kibana-5](./elastic-kibana-5) - Elastic v5 and Kibana
- [elastic-kibana-6](./elastic-kibana-6) - Elastic v6 and Kibana

## Sample usage

```
docker-compose up
```

When containers start:
- http://localhost:5601 - Kibana
- http://localhost:9200 - Elasticsearch

[elasticsearch]: https://www.elastic.co/products/elasticsearch
[kibana]: https://www.elastic.co/products/kibana
[morfologik]: https://github.com/allegro/elasticsearch-analysis-morfologik
[docker]: https://www.docker.com/
