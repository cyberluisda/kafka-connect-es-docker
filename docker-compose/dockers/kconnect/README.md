# EMP Assets Kafka Connect

This project contains configuration to run with kafka connect server or in a
kafka connect standalone docker in order to save data from topic `assets_json` to `assets` ElasticSearch index.

Values expected in topic are elastic search document (json), this implies that value type on topic must be a string.

Keys in topic must be the doc id used to save in ES in order to make save process
idempotent.

# Default configuration.

Elastic search entry point configured by default is `http://elastic-search:9200`

Kafka bootstrap servers configured by default is `kafka:9092`

Mapping used for this index is `asset`. See
[Elasti Search Schemas](../../../schemas/elasticsearch) For more information.

For change configuration see files on [config path](files/config)

# Build and run with docker

To build and run in standalone mode over docker you can run next commands:

```
docker build --tag emp_assets_kconnect .
docker run -d emp_assets_kconnect
```

Or you can look-up and follow `docker-compose` as reference on [Integration tests path](../../../integration-tests)
