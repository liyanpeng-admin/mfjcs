# MFJCS

## Starting and configuring Solr

$SOLR_HOME/bin/solr start -c -s solr/home
$SOLR_HOME/bin/solr zk -upconfig -d solr/conf/mfjcs-items -n mfjcs-items -z localhost:9983
$SOLR_HOME/bin/solr create -c mfjcs-items -n mfjcs-items

## Starting the REST API

1. `mvn clean install`
1. `java -jar target/mfjcs-rest-1.0-SNAPSHOT.jar server config.yml`
1. open `http://localhost:8080`

## Health Check

- open `http://localhost:8081/healthcheck`

## API Usage examples:

### Create an item

curl -XPOST -H'Content-Type: application/json' -H'Accept: application/json' -d '{ "fields": { "foo": "bar" } }' http://localhost:8080/items

### Retrieve it

curl http://localhost:8080/items/5F5fec25-76b5-49ae-a1bf-15692c86ef5d
