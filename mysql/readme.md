# PostgreSQL

A [Docker](docker) composition with [MySQL](mysql).

## Sample usage

```
docker-compose up
```

Important values:
- database: test
- username: mysql
- password: mysql
- Jdbc connection: `jdbc:mysql://localhost:3306/test`
- Adminer http://localhost:8836/?server=db&username=mysql&db=test ([mysql-workbench](https://dev.mysql.com/downloads/workbench/) or [squirrelsql](http://squirrel-sql.sourceforge.net/) are much better)

[mysql]: https://hub.docker.com/_/mysql
[docker]: https://www.docker.com/
