# Metrics: Grafana + Prometheus

Docker composition with metrics stack:
- [Grafana](https://grafana.com/docs/installation/docker/)
- [Prometheus](https://prometheus.io/)

This composistion uses official Grafana and Prometheus images.

## Grafana
Grafana comes with predefined datasource and some dashboards stored in `grafana/dashboards`.

## Exposed ports
- [3000](http://localhost:3000) - grafana
- [8880](http://localhost:8880) - nginx
- 2003 - carbon receiver - plaintext
- 2004 - carbon receiver - pickle - send metrics here
- 2023 - carbon aggregator - plaintext
- 2024 - carbon aggregator - pickle
- 8080 - Graphite internal gunicorn port (without Nginx proxying).
- 8125 - statsd (udp)
- 8126 - statsd admin
