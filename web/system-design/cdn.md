# CDN

A CDN is a group of geographically distributed proxy servers. A proxy server is an intermediate server between a client and the origin server.

### Requirements

#### Functional

* Retrieve
* Request
* Deliver
* Search
* Update
* Delete

#### Non-Functional

* Performance
* Availablity
* Scalability
* Reliability & security

### Design CDN

#### CDN Components

* Clients
* Routing system
* Scrubber servers - separates the good traffic from malicious traffic and protect against well known attacks like DDoS.
* Proxy Servers (or Edge proxy servers) - Servers content to the users. Stores hot data in RAM and cold in SSDs.
* Distributed System - distributing content to all the edge proxy servers. Uses broadcast-like approache.
* Origin Server
* Managment System

### Content Caching Strategy

#### Push CDN

* Origin server sends the contents to the CDN Proxy server
* Good for static content
* Maintains more replicas and improves availability

#### Pull CDN

* CDN Proxy server retrieves the content from the Origin server, when a resource is requested and is not already cached.
* Good for dynamic content.

#### Dynamic content caching optimization

* Execution of scripts at the proxy server instead of the origin server (Edge computing)
* Edge Side Includes (ESI)&#x20;
  * Solves the problem of fetching entire page, when only a small portion of the page changes. Eg. User's name in account area on a news site.

For Videos, **Dynamic Adaptive Streaming one HTTP (DASH)** uses manifest file with URIs of the video with different resolutions so that the client can fetch whatever is appropriate as per prevailing network and end node conditions. Netflix uses a proprietarty DASH version with a Byte-range in teh URL for further content reqeust and delivery optimizations.

### Problems that CDN Tackles

* High latency:&#x20;
  * Transmission delays (function of available bandwidth)
  * Propagation delay (function of distance)
  * Queuing delay (function of network congestion)
  * Nodal processing delays
* Data-intensive applications
  * small Path Message Transmission Units (MTU) links can reduce the throughput of applications.
  * Different portions of network will have different congestion characteristics.
* Scarcity of data center resources.
  * computational capacity and bandwidth become a limitaiton with increase in users.
