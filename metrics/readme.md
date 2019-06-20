# Metrics: Grafana + Graphite (with Statsd)

Docker composition with metrics stack:
- [Grafana](https://grafana.com/docs/installation/docker/)
- [Graphite + Statsd](https://github.com/graphite-project/docker-graphite-statsd)

This composistion uses official Grafana and Graphite images.

## Grafana
Grafana comes with predefined datasource pointing to graphite fromt the composition.
Moreover it has some dashboards stored in `grafana/dashboards`.

## Sample usage
1. Start metrics with `docker-compose up`
2. Open http://localhost:3000 (default credentials: admin/admin)
3. Generate some random stats `while true; do echo -n "example:$((RANDOM % 100))|c" | nc -w 1 -u 127.0.0.1 8125; done`
4. Open "Test Dashboard" to see generated data
