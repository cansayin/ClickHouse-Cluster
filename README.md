# ClickHouse-Cluster
Setup ClickHouse Cluster

1 cluster, with 3 shards
Each shard has 2 replica server

We have 6 clickhouse server container and one zookeeper container.

--Start servers

docker network create clickhouse-net

docker-compose up -d

--Connect To Servers
<pre id="example"><code class="language-lang"  style="color: #333; background: #f8f8f8;">docker run -it --rm --network="clickhouse-net" --link clickhouse1:clickhouse-server yandex/clickhouse-client --host clickhouse-server
</code></pre>
docker run -it --rm --network="clickhouse-net" --link clickhouse1:clickhouse-server yandex/clickhouse-client --host clickhouse-server
docker run -it --rm --network="clickhouse-net" --link clickhouse2:clickhouse-server yandex/clickhouse-client --host clickhouse-server
docker run -it --rm --network="clickhouse-net" --link clickhouse3:clickhouse-server yandex/clickhouse-client --host clickhouse-server
docker run -it --rm --network="clickhouse-net" --link clickhouse4:clickhouse-server yandex/clickhouse-client --host clickhouse-server
docker run -it --rm --network="clickhouse-net" --link clickhouse5:clickhouse-server yandex/clickhouse-client --host clickhouse-server
docker run -it --rm --network="clickhouse-net" --link clickhouse6:clickhouse-server yandex/clickhouse-client --host clickhouse-server
