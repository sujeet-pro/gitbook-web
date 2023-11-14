# Back of the envelope Calculations

| Servers     | RAM  | Processor | Storage |
| ----------- | ---- | --------- | ------- |
| Web         | Low  | High      | Low     |
| Application | High | Medium    | Medium  |
| Storage     | Low  | Medium    | High    |



Facebook open-sourced its data center design in 2011

Web Servers - 32GB RAM, 500GB Storage, For high end computations - Custom 16 core processors (partnered with Intel)

Application Servers - RAM up to 256GB, and Storage (Disk + Flash) - up to 6.5TB

Storage Servers, youtube example

* **Blob Storage** - for its encoded videos
* A **temporary processing queue storage** that can hold a few hundred hours of video content uploaded daily to YouTube for processing
* Specialized storage called **Bigtable** for storing a large number of thumbnails of videos.
* **RDBMS** - Relational database management system for users and videos metadata



#### Typical Server Specifications

No. of sockets - 2

Processors - Intel Xeon X2686

No. of cores - 36 cores (72 threads)

RAM - 256 GB

Cache L3 - 45 MB

Storage Capacity - 15TB

#### Important Latencies

| Component                                               | Time (nanoseconds)         |
| ------------------------------------------------------- | -------------------------- |
| L1 cache reference                                      | 0.9                        |
| L2 cache reference                                      | 2.8                        |
| L3 cache reference                                      | 12.9                       |
| Main memory reference                                   | 100                        |
| Compress 1KB with Snzip                                 | 3,000 (3 microseconds)     |
| Read 1MB sequentially from memory                       | 9,000 (9 microseconds)     |
| Read 1MB sequentially from SSD                          | 200,000 (200 microseconds) |
| Roundtrip within the same data center                   | 500,000 (500 microseconds) |
| Read 1MB sequentially from SSD with speed \~1DB/sec SSD | 1,000,000 (1ms)            |
| Disk seek                                               | 4ms                        |
| Read 1MB sequentially from disk                         | 2ms                        |
| Send packet SF->NYC                                     | 71ms                       |



### Important Rates / QPS

QPS = Queries per second

| QPS Handled by  | QPS          |
| --------------- | ------------ |
| MySQL           | 1,000        |
| Key-value store | 10,000       |
| Cache server    | 100,000 - 1M |



### Requests estimations

RPS = Requests per second

* CPU bound requests
* Memory bound requests

RPS\_CPU = NUM\_CPU / Task time

RPS Memory = RAM\_SIZE / (WORKER\_MEMORY X TASK\_TIME)

Eg. for RPS\_CPU, Assuming each tasks takes 200ms and the CPU has 72 threads

RPS\_CPU = 72 / 200ms = 360RPPS

Eg. for RPS Memory, Assuming Each worker needs 300MB, and takes 50ms for a request for a server with 240GB RAM,

240GB/(300MB \* 50MS) = 16000RPS

