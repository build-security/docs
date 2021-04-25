# Kafka Topic Authorization

### Introduction

Kafka streams can have many publishers and subscribers. OPA and build.security can be used to control **WHO** can read/write **WHAT** topic.

Let's dive right into it.

### 1. Get kafka

[Download](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.8.0/kafka_2.13-2.8.0.tgz) the latest Kafka version and extract it:

```bash
tar -xzf kafka_2.13-2.8.0.tgz
cd kafka_2.13-2.8.0
```

### 2. Start the kafka environment

{% hint style="info" %}
**NOTE**: Your local environment must have Java 8+ installed.
{% endhint %}

Run the following commands in order to start all services in the correct order:

```bash
# Start the ZooKeeper service
# Note: Soon, ZooKeeper will no longer be required by Apache Kafka.
bin/zookeeper-server-start.sh config/zookeeper.properties
```

### 3. Plug the external authorization plugin into Kafka

[download](https://github.com/Bisnode/opa-kafka-plugin/releases/download/v1.0.0/opa-authorizer-1.0.0-all.jar) the OPA authorizer and put it into the `libs` folder

edit `config/server.properties` and add the following lines:

```bash
authorizer.class.name=com.bisnode.kafka.authorization.OpaAuthorizer
opa.authorizer.url=http://localhost:8181/v1/data/kafka/authz/allow
opa.authorizer.cache.expire.after.seconds=1
```

### 4. Start the kafka server

Open another terminal session and run:

```bash
# Start the Kafka broker service
bin/kafka-server-start.sh config/server.properties
```

### 5. Create a topic

Run the following command to create a topic named `topic1`

```bash
bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092
```



