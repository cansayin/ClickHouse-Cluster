# ClickHouse-Cluster
Setup ClickHouse Cluster

1 cluster, with 3 shards
Each shard has 2 replica server

We have 6 clickhouse server container and one zookeeper container.

Start servers

docker network create clickhouse-net

docker-compose up -d
