1. Start containers
```
docker-compose up
```
2. Start debezium
```
for name in cassandra-seed cassandra1 cassandra2; do docker-compose exec -d $name sh start-debezium.sh; done
```
This can take some time as cassandra takes some time to start. 

3. Make changes
```
cqlsh localhost 9042
```

4. Verify events on debezium logs
```
for name in cassandra-seed cassandra1 cassandra2; do docker-compose exec $name cat debezium.stdout.log | grep -i "Received event"; done
```
