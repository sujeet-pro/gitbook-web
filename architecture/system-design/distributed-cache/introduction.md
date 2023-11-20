# Introduction

### Writing Policies

#### Write-through Cache

Write on both storages (cache and DB), which can happen concurrently or one after the other.

Increases the write latency but ensures strong consistency between the DB and the cache.

#### Write Back Cache

Write first to the cache and asynchronously write to the DB.

Low latency, but inconsistent data when reading from db.

#### Write-Around Cache

Write only to the DB.

The cache is updated after the next cache miss.

It is not favorable for reading recently updated data.

### Eviction Policies

* Least recently used (LRU)
* Most recently used (MRU)
* Least frequently used (LFU)
* Most frequently used (MFU)

#### Data Temperature

* Hot: highly accessed data
* Warm: This is less frequently accessed data
* Cold: Rarely accessed data

The idea is to evict the cold data.

### Cache invalidation

Invalid/stale data must be marked for deletion

#### TTL: Time to Live

Add static metadata to each cache entry. And upon expiry, delete those.

* Active Expiration: Actively checks the TTL of cache entries through a daemon process
* Passive expiration: checks the TTL of entry at the time of access.

### Storage Mechanism

#### Which Cache Server

Use a Hash function. Consistent hashing is preferred for distributed systems to handle scaling or crashes.

#### Locate Cache

Use a hashing function to locate a cache entry to read/write inside a cache server.

* Use Bloom filters to check if the cache doesn't exist.
  * Gives Probabilistic output: Probably Yes | Firm No.
  * If yes, use other mechanisms to check if it exists.
* Use Doubly linked list to store the data
  * Adding/removing data is a constant time operation
    * Evict from tail
    * Relocate an entry to head (Order based on access - LRU)

### Sharding in cache clusters

Sharding involves splitting up cache data among multiple cache servers.

* Dedicated cache servers
  * Flexibility for scale and infra needs.
  * Allows for cache as a service.
* Co-locate cache
  * Generally used for reduction in CAPEX (Capital Expenditures) and OPEX (Operational Expenditures)
  * Good for read-only. Issues with updates. If one server updates some data, it will update its cache, but what about others?

### Cache Clients

* Does the hashing and has information about all the nodes and connects with them.
