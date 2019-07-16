# PostgreSQL

A [Docker](docker) composition with [PostgreSQL](postgres).

## Sample usage

```
docker-compose up
```

Important values:
- database: test
- username: postgres
- password: postgres
- Jdbc connection: `jdbc:postgresql://localhost:5432/test`

PgAdmin4
- Address: http://localhost:8832
- Email: pgadmin4@pgadmin.org
- Password: postgres
- Host: postgres:5432

[postgres]: https://hub.docker.com/_/postgres
[docker]: https://www.docker.com/
