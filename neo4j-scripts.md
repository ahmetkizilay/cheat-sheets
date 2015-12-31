# Neo4j Scripts

#### Upgrading
Make sure to follow these steps:
* Disable auth
* Set storage upgrade
* Set database location

#### Enable http logging
In `conf/neo4j-server.properties` add
```
org.neo4j.server.http.log.enabled=true
org.neo4j.server.http.unsafe.content_log.enabled=true
```

#### Disable auth
In `conf/neo4j-server.properties` add
```
dbms.security.auth_enabled=false
```

#### Set database location
In `conf/neo4j-server.properties` add
```
org.neo4j.server.database.location=<new-path>
```

#### Disable usage data collection
In `conf/neo4j.properties`, add
```
neo4j.ext.udc.enabled = false
```

#### Set storage upgrade
In `conf/neo4j.properties`, add
```
allow_store_upgrade=true
```

#### Increase ulimit for user

In `/etc/security/limits.conf`, add the following for the user running neo4j to fix the `WARNING: Max 1024 open files allowed, minimum of 40 000 recommended.` warning.
```
<user>   soft    nofile  40000
<user>   hard    nofile  40000
```

#### Running with Docker
```
docker run \
    --detach \
    --publish=7474:7474 \
    --volume=$HOME/neo4j/data:/data \
    --ulimit=nofile=40000:40000 \
    --env=NEO4J_AUTH=none \
    neo4j/neo4j
```
Visit the [official repo](https://hub.docker.com/r/neo4j/neo4j/) for more options.
