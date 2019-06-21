# Metrics: Grafana + Graphite (with Statsd)

Docker composition with metrics stack:
- [Grafana](https://grafana.com/docs/installation/docker/)
- [Graphite + Statsd](https://github.com/graphite-project/docker-graphite-statsd)

This composistion uses official Grafana and Graphite images.

## Grafana
Grafana comes with predefined graphite datasource and some dashboards stored in `grafana/dashboards`.

## Exposed ports
- [3000](http://localhost:3000) - grafana
- 8880 - nginx
- 2003 - carbon receiver - plaintext
- 2004 - carbon receiver - pickle
- 2023 - carbon aggregator - plaintext
- 2024 - carbon aggregator - pickle
- [8080](http://localhost:8080) - Graphite internal gunicorn port (without Nginx proxying).
- 8125 - statsd (udp)
- 8126 - statsd admin

## Sample usage
1. Start metrics with `docker-compose up`
2. Open http://localhost:3000 (default credentials: admin/admin)
3. Generate some random stats `while true; do echo -n "example:$((RANDOM % 100))|c" | nc -w 1 -u 127.0.0.1 8125; done`
4. Open "Test Dashboard" to see generated data
