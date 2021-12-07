## Run Zabbix in Docker

### Example

```console
docker-compose -f ./docker-compose_v3_ubuntu_timescaledb_2.5.1-pg13_latest.yaml up -d
docker exec -it 250-pg13_zabbix-server_1 bash
psql -h postgres-server -U zabbix zabbix < /usr/share/doc/zabbix-server-postgresql/timescaledb.sql
docker exec -it 250-pg13_postgres-server_1 psql -U zabbix zabbix -c "SELECT * FROM chunks_detailed_size('history')"
docker-compose -f ./docker-compose_v3_ubuntu_timescaledb_2.5.1-pg13_latest.yaml down
```
