# ClickHouse-Cluster
Setup ClickHouse Cluster

1 cluster, with 3 shards
Each shard has 2 replica server

We have 6 clickhouse server container and one zookeeper container.

--Start servers
<pre id="example"><code class="language-lang"  style="color: #333; background: #f8f8f8;">docker network create clickhouse-net
</code></pre>

<pre id="example"><code class="language-lang"  style="color: #333; background: #f8f8f8;">docker-compose up -d
</code></pre>



--Connect To Servers
<pre id="example"><code class="language-lang"  style="color: #333; background: #f8f8f8;">docker run -it --rm --network="clickhouse-net" --link clickhouse1:clickhouse-server yandex/clickhouse-client --host clickhouse-server
</code></pre>
<pre id="example"><code class="language-lang"  style="color: #333; background: #f8f8f8;">docker run -it --rm --network="clickhouse-net" --link clickhouse2:clickhouse-server yandex/clickhouse-client --host clickhouse-server
</code></pre>
<pre id="example"><code class="language-lang"  style="color: #333; background: #f8f8f8;">docker run -it --rm --network="clickhouse-net" --link clickhouse3:clickhouse-server yandex/clickhouse-client --host clickhouse-server
</code></pre>
<pre id="example"><code class="language-lang"  style="color: #333; background: #f8f8f8;">docker run -it --rm --network="clickhouse-net" --link clickhouse4:clickhouse-server yandex/clickhouse-client --host clickhouse-server
</code></pre>
<pre id="example"><code class="language-lang"  style="color: #333; background: #f8f8f8;">docker run -it --rm --network="clickhouse-net" --link clickhouse5:clickhouse-server yandex/clickhouse-client --host clickhouse-server
</code></pre>
<pre id="example"><code class="language-lang"  style="color: #333; background: #f8f8f8;">docker run -it --rm --network="clickhouse-net" --link clickhouse6:clickhouse-server yandex/clickhouse-client --host clickhouse-server
</code></pre>

<pre id="example"><code class="language-lang"  style="color: #333; background: #f8f8f8;">SELECT *
FROM system.clusters

Query id: 5f75021c-bdc4-42cb-bb22-dc41437101d6

┌─cluster─────────────────────┬─shard_num─┬─shard_weight─┬─replica_num─┬─host_name──────────────────┬─host_address─┬─port─┬─is_local─┬─user────┬─default_database─┬─errors_count─┬─slowdowns_count─┬─estimated_recovery_time─┐
│ cluster_1                   │         1 │            1 │           1 │ clickhouse-shard1-replica1 │ 172.19.0.8   │ 9000 │        1 │ default │                  │            0 │               0 │                       0 │
│ cluster_1                   │         1 │            1 │           2 │ clickhouse-shard1-replica2 │ 172.19.0.6   │ 9000 │        0 │ default │                  │            0 │               0 │                       0 │
│ cluster_1                   │         2 │            1 │           1 │ clickhouse-shard2-replica1 │ 172.19.0.5   │ 9000 │        0 │ default │                  │            0 │               0 │                       0 │
│ cluster_1                   │         2 │            1 │           2 │ clickhouse-shard2-replica2 │ 172.19.0.4   │ 9000 │        0 │ default │                  │            0 │               0 │                       0 │
│ cluster_1                   │         3 │            1 │           1 │ clickhouse-shard3-replica1 │ 172.19.0.7   │ 9000 │        0 │ default │                  │            0 │               0 │                       0 │
│ cluster_1                   │         3 │            1 │           2 │ clickhouse-shard3-replica2 │ 172.19.0.3   │ 9000 │        0 │ default │                  │            0 │               0 │                       0 │
│ test_shard_localhost        │         1 │            1 │           1 │ localhost                  │ 127.0.0.1    │ 9000 │        1 │ default │                  │            0 │               0 │                       0 │
│ test_shard_localhost_secure │         1 │            1 │           1 │ localhost                  │ 127.0.0.1    │ 9440 │        0 │ default │                  │            0 │               0 │                       0 │
└─────────────────────────────┴───────────┴──────────────┴─────────────┴────────────────────────────┴──────────────┴──────┴──────────┴─────────┴──────────────────┴──────────────┴─────────────────┴─────────────────────────┘
8 rows in set. Elapsed: 0.025 sec. 
</code></pre>

