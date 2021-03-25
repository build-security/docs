# build.rate\_limit



### Function Description

`build.rate_limit` returns `false` for a predefined `RATE_LIMITER_DURATION` for the first `limit` times it is called within `duration`. Returns `true` if it has been called more than `limit` times within a given `duration`.

This builtin provides a flexible way to implement rate-limiting on any operation. It needs to be connected to a [Redis](https://redis.io/) server: you can set it up yourself, or use solutions like [AWS ElastiCache](https://aws.amazon.com/elasticache/) \(managed Redis\).

Because it uses shared memory, this function is safe for use across multiple PDPs. If they are connected to the same Redis server, we can expect the results to be consistent for the given `key` and `limit` across all PDPs.

In the [example](https://github.com/build-security/aws-api-gateway-authz/blob/main/policy), we use it to rate-limit requests made to our AWS API Gateway endpoint.

### Function format

`build.rate_limit(key, limit)`

**Parameters:**

* `key` - string to be used as key to distinguish between multiple rate limiters
* `limit` - a number representing the upper `limit` of calls for given `key`

### Function Usage Example

```scala
buiild.rate_limit("user", 5)
```

### PDP configuration

After [setting up Redis](https://redis.io/topics/quickstart), you can use our here's an example of extra env. variables to be added to the PDP:

Note the extra variables:

* RATE\_LIMITER_\__REDIS\_ENDPOINT
* RATE\_LIMITER_\__REDIS\_PASSWORD
* RATE\_LIMITER_\_DURATION_

```bash
docker pull buildsecurity/api-gw-pdp
docker run \
    -e RATE_LIMITER_REDIS_ENDPOINT=<your Redis endpoint> \
    -e RATE_LIMITER_REDIS_PASSWORD=<your Redis password, if you've set one> \
    -e RATE_LIMITER_DURATION=<the duration basis for rate-limiting> \
    -p 8181:8181 \
    --name pdp \
    buildsecurity/api-gw-pdp
```

{% hint style="info" %}


**Supported PDP version** 

This built-in function supported from version V0.2.0 and above.
{% endhint %}



