# cache

### Functions Description

There are 3 cache related functions to be used as part of policy evaluation. These function can be used to store and fetch data from an in-memory FIFO cache within the PDP. Commonly used to minimize external calls to data sources.

### Functions format

* `cache.insert(key, value, ttl)`
* `cache.get(key)`
* `cache.delete(key)`

**Parameters:**

* `key` - a string representing the key for the cache entry. Inserting multiple cache entries with the same `key` will result in overriding previous inserts.
* `value` - JSON object to be stored in cache
* `ttl` - Time To Live represented as seconds.

### Function Usage Example

```scala
cache.insert("key", "value", 60)

# After 30 seconds
cache.get("key") # will return "value"

# After 61 seconds
cache.get("key") # will return false
```

