## Run Zabbix 6.0 LTS in Docker

### Example

```console
docker-compose -f ./docker-compose_v3_ubuntu_timescaledb_2.7.2-pg14_latest.yaml up -d

# import zabbix timescaledb
docker exec -it 272-pg14_zabbix-server_1 bash
psql -h postgres-server -U zabbix zabbix < /usr/share/doc/zabbix-server-postgresql/timescaledb.sql
exit

# check timescaledb chunks
docker exec -it 272-pg14_postgres-server_1 psql -U zabbix zabbix -c "SELECT * FROM chunks_detailed_size('history')"

firefox http://192.168.42.13
Admin/zabbix

# stop & delete container
docker-compose -f ./docker-compose_v3_ubuntu_timescaledb_2.7.2-pg14_latest.yaml down
```
