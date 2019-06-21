# Mongo Replica Set

A [Docker](docker) composition with [MongoDB](mongo) containing Replica Set of 3 nodes.

## Ports
- 27017 - first mongo node mongo0
- 27018 - second mongo node mongo1
- 27019 - third mongo node mongo2

## Configure Replica set
1. Start docker compose `docker-compose up`
2. Execute script containing replica set configuration on any node `mongo < replicaset-init.js`. This step must be executed only once after first start.

[mongo]: https://www.mongodb.com/download-center/community
[docker]: https://www.docker.com/
