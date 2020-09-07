# https://github.com/elastic/elasticsearch-docker
FROM docker.elastic.co/elasticsearch/elasticsearch:7.6.2

# Add your elasticsearch plugins setup here
# Waiting for release: https://github.com/allegro/elasticsearch-analysis-morfologik/issues/9
RUN elasticsearch-plugin install \
  pl.allegro.tech.elasticsearch.plugin:elasticsearch-analysis-morfologik:7.6.2
