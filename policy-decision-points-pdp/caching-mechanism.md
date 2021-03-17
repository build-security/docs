# Caching Mechanism



There are multiple ways to get external data into the policy evaluation phase. These options are described in detail [here](https://www.openpolicyagent.org/docs/latest/external-data/).

build.security's approach is to leverage whatever there is in the request itself, and if there's a need for extra data to make a decision, an external call is made in realtime.

This approach is similar to how CPU cache is storing information for the CPU to use. It is assumed that most of the data shall not reside in the cache as it is not being used most of the time. Having said that, once data is fetched from the memory / external data source - it is assumed to be used many times in the near future.

The takeaway from this approach is that the responses from the external calls shall be cached for future subsequent requests.  
Our PDP's cache is a simple in-memory, FIFO cache, built on top of native Golang. It is enabled by default for each PDP and is not shared between multiple PDPs.

If there's a need to load information into the PDPs cache at startup, the [internal data source](https://docs.build.security/docs/creating-an-internal-data-source) mechanism could be useful as this data will be sent to the PDP at 1st communication.

**Eviction policy:**

* TTL: The default TTL is 60 seconds and can be changed on a per data source level.
* Memory: The cache will consume at most 50% of the available RAM to the PDP docker, with a minimum of 50MB.
* Amount of keys: The cache will maintain a maximum of 1M keys.

