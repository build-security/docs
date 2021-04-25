# Kafka Topic Authorization

### Introduction

Kafka streams can have many publishers and subscribers. OPA and build.security can be used to control **WHO** can read/write **WHAT** topic.

Let's dive right into it.

### Prerequisites

{% hint style="info" %}
**NOTE**: Your local environment must have Java 8+ installed.
{% endhint %}

### 1. Get kafka

[Download](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.8.0/kafka_2.13-2.8.0.tgz) the latest Kafka version and extract it:

```bash
tar -xzf kafka_2.13-2.8.0.tgz
cd kafka_2.13-2.8.0
```

### 2. Start the kafka environment

Run the following commands in order to start all services in the correct order:

```bash
# Start the ZooKeeper service
# Note: Soon, ZooKeeper will no longer be required by Apache Kafka.
bin/zookeeper-server-start.sh config/zookeeper.properties
```

### 3. Plug the external authorization plugin into Kafka

[Download](https://github.com/Bisnode/opa-kafka-plugin/releases/download/v1.0.0/opa-authorizer-1.0.0-all.jar) the OPA authorizer and put it into the `libs` folder

edit `config/server.properties` and add the following lines:

```bash
authorizer.class.name=com.bisnode.kafka.authorization.OpaAuthorizer
opa.authorizer.url=http://localhost:8181/v1/data/kafka/authz/allow
opa.authorizer.cache.expire.after.seconds=1
```

This configuration will :

* instruct the kafka server to use OPA as an external authorization service for all operations.
* Provide the external authorization service endpoint address
* Instruct the authorization plugin to cache the results for 1 second \(in production we shall increase this to a larger value\)

### 4. Run PDP with kafka policy enforced

Follow the pdp deployment [instructions](../policy-decision-points-pdp/pdp-deployments/) and publish a simple kafka policy.

{% hint style="info" %}
Make sure the policy package name is `kafka.authz`
{% endhint %}

### 5. Start the kafka server

Open another terminal session and run:

```bash
# Start the Kafka broker service
bin/kafka-server-start.sh config/server.properties
```

### 6. Create a topic

Run the following command to create a topic named `topic1`

```bash
bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092
```

### 7. Watch decision logs

Already you should be seeing decision logs in the project as the topic creation operation got authorized.

### 8. Create a kafka producer and consumer

Play with the policy by adding kafka producer and consumer, watch decision logs and add more rules to the policy.

On another terminal screen, start a kafka producer:

```bash
bin/kafka-console-producer.sh --topic topic1 --bootstrap-server localhost:9092
```

On another terminal screen, start a kafka consumer:

```bash
bin/kafka-console-consumer.sh --topic topic1 --bootstrap-server localhost:9092
```

### Usage

Example structure of input data provided from opa-kafka-plugin to Open Policy Agent.

```javascript
{
    "action": {
        "logIfAllowed": true,
        "logIfDenied": true,
        "operation": "DESCRIBE",
        "resourcePattern": {
            "name": "alice-topic",
            "patternType": "LITERAL",
            "resourceType": "TOPIC",
            "unknown": false
        },
        "resourceReferenceCount": 1
    },
    "requestContext": {
        "clientAddress": "192.168.64.1",
        "clientInformation": {
            "softwareName": "unknown",
            "softwareVersion": "unknown"
        },
        "connectionId": "192.168.64.4:9092-192.168.64.1:58864-0",
        "header": {
            "data": {
                "clientId": "rdkafka",
                "correlationId": 5,
                "requestApiKey": 3,
                "requestApiVersion": 2
            },
            "headerVersion": 1
        },
        "listenerName": "SASL_PLAINTEXT",
        "principal": {
            "name": "alice-consumer",
            "principalType": "User"
        },
        "securityProtocol": "SASL_PLAINTEXT"
    }
}
```

### More information

The following table summarizes the supported resource types and operation names.

| `input.action.resourcePattern.resourceType` | `input.action.operation` |
| :--- | :--- |
| `CLUSTER` | `CLUSTER_ACTION` |
| `CLUSTER` | `CREATE` |
| `CLUSTER` | `DESCRIBE` |
| `GROUP` | `READ` |
| `GROUP` | `DESCRIPTION` |
| `TOPIC` | `ALTER` |
| `TOPIC` | `DELETE` |
| `TOPIC` | `DESCRIBE` |
| `TOPIC` | `READ` |
| `TOPIC` | `WRITE` |

