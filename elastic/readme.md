# Elasticsearch + Kibana

A [Docker](docker) composition with:
- [Kibana](kibana)
- [Elasticsearch](elasticsearch)
- [Morfologik Polish Lemmatizer](morfologik)

There are separate folders for each version because of Elasticsearch drastic api changes between versions.
Most often I need access to multiple versions.

## Configurations
- [elastic-kibana-5](./elastic-kibana-5) - Elastic v5 and Kibana
- [elastic-kibana-6](./elastic-kibana-6) - Elastic v6 and Kibana
- [elastic-kibana-7](./elastic-kibana-7) - Elastic v7 and Kibana

## Exposed ports
- [5601](http://localhost:5601) - Kibana
- [9200](http://localhost:9200) - Elasticsearch HTTP
- [9300](http://localhost:9300) - Elasticsearch TCP transport

## Sample queries

Go to [Kibana](http://localhost:5601) then select DevTools

```
# Sample index
# DELETE my_index # delete if already created
PUT my_index
{
  "settings": {
    "analysis": {
      "filter": {
        "unique_stem": {
          "type": "unique",
          "only_on_same_position": true
        }
      },
      "analyzer": {
        "polish": {
          "_comment": "Definition of a standard polish analyzer",
          "tokenizer": "standard",
          "filter": [
            "lowercase",
            "keyword_repeat",
            "morfologik_stem",
            "unique_stem"
          ]
        },
        "path_analyzer": {
          "_comment": "Definition of a standard hierarchical path analyzer",
          "tokenizer": "path_tokenizer"
        }
      },
      "tokenizer": {
        "path_tokenizer": {
          "type": "path_hierarchy"
        }
      }
    }
  },
  "mappings": {
    "item": {
      "properties": {
        "title": {
          "type": "text",
          "analyzer": "polish"
        },
        "categories": {
          "type": "keyword",
          "analyzer": "path_analyzer"
        }
      }
    }
  }
}

# Sample documents

PUT /my_index/item/1
{
  "title": "Super rowery",
  "categories": ["a/b/c","a/e/f"]
}
PUT /my_index/item/2
{
  "title": "Blueberry dla yuppie",
  "categories": ["a/e"]
}
PUT /my_index/item/3
{
  "title": "Dzikie węże",
  "categories": ["a/b"]
}
PUT /my_index/item/4
{
  "title": "Jabłko zamiast della",
  "categories": ["a/b/d"]
}

# Sample queries
GET /my_index/item/_search
GET /my_index/item/_search
{
  "query" : {
    "match": {
      "title": "jabłka"
    }
  }
}
GET /my_index/item/_search
{
  "query" : {
    "match": {
      "categories": "a/b"
    }
  }
}
GET /my_index/item/_search
{
  "query" : {
    "bool": {
      "should": [
        { "match": { "title": "jabłka" } },
        { "match": { "categories": "a/b" } }
      ]
    }
  }
}
```

[elasticsearch]: https://www.elastic.co/products/elasticsearch
[kibana]: https://www.elastic.co/products/kibana
[morfologik]: https://github.com/allegro/elasticsearch-analysis-morfologik
[docker]: https://www.docker.com/
