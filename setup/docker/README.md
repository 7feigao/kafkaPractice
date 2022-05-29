1. refer to page: #https://developer.confluent.io/quickstart/kafka-docker/
2. to handle error like `TimeoutException: Timeout expired while fetching topic metadata Kafka`, you can refer to https://www.confluent.io/blog/kafka-client-cannot-connect-to-broker-on-aws-on-docker-etc/#scenario-4, after done to setup and restart kafka broker, you can access kafka services from local through `localhost:19092`.
### Create a topic
   Kafka stores messages in topics. It’s good practice to explicitly create them before using them, even if Kafka is configured to automagically create them when referenced.
Run this command to create a new topic into which we’ll write and read some test messages.
```shell
# create a topic named quickstart with 3 partition
docker exec broker kafka-topics --bootstrap-server broker:9092 --create --topic partition3 --partitions 3
```
