# kafka-connect-docker-es #

Docker image with software to run kafka connects based on cyberlusda/kafka-connect
and with Elastic Search connector by confluent.
For more informatiom see
[Github confluentinc/kafka-connect-elasticsearch](https://github.com/confluentinc/kafka-connect-elasticsearch)

# Using with docker-compose #

There is an docker-compose example on `docker-compose/` path.

Because there is internal references to dcocker base images. You must build
docker-compose images at first step:

```command
cd docker-compose
docker-compose build
```

## Ingest data on Elastic Search example ##

After build process (previously described ) you can run and test how data is
saved to Elastic Search

Launch example produce service

```command
docker-compose up -d produce-tests
```

After a few minutes you can see data persisted on Elastic Search:

```command
docker-compose run --rm curl "elastic-search:9200/tests/test/1?pretty=true"
```

```json
{
  "_index" : "tests",
  "_type" : "test",
  "_id" : "1",
  "_version" : 0,
  "found" : true,
  "_source" : {
    "test_id" : "TEST"
  }
}
```

## Cleaning procedure ##

* After data was saved on ES, you can delete all services with:

  ```
  docker-compose down
  ```

* Clean building local images.

  ```
  docker images  | awk '$1~/dockercompose/{print $3}' | xargs docker rmi -f
  ```

  Please, have in mind, that last command delete all local docker images which
  name contains `dockercompose`. This is default project name set by docker-compose
  (it is extracted from `docker-compose` path where example is saved).

* Clean local docker volumes.

  ```
  docker volume prune -f
  ```
