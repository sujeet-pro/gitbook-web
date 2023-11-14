# Load Balancers

A load balancer is a reverse proxy server that distributes network or application traffic across a number of servers (aka server farm or server pool).

* **Scalability**: Distributes client requests or network load efficiently across multiple servers
* **Availability**: Ensures high availability and reliability by sending requests only to servers that are online
* **Elasticity & Performance**: Provides the flexibility to add or subtract servers as demand dictates

### Load Balancing Algorithms

* **Round Robin** – Requests are distributed across the group of servers sequentially.
  * **Weighted Round Robin**, when the servers have varing capabilities.
* **Least Connections** – A new request is sent to the server with the fewest current connections to clients. The relative computing capacity of each server is factored into determining which one has the least connections.
* **Least Time** – Sends requests to the server selected by a formula that combines the fastest response time and fewest active connections. Exclusive to NGINX Plus.
* **Hash** – Distributes requests based on a key you define, such as the client IP address or the request URL. NGINX Plus can optionally apply a **consistent hash** to minimize redistribution of loads if the set of upstream servers changes.
  * Hashing Session Key with consistent hashing is optimal for cases when you want the same server to handle concurrent requests.
* **IP Hash** – The IP address of the client is used to determine which server receives the request.
* **Random with Two Choices** – Picks two servers at random and sends the request to the one that is selected by then applying the Least Connections algorithm (or for NGINX Plus the Least Time algorithm, if so configured).\


### Services Offered by load balancers

* **Health checking**: LBs use the heartbeat protocol to monitor the health and therefore, reliability of end-servers.
* **TLS terminations**: LBs reduce the burden on end-servers by handling TLS termination with the client. (aka SSL Termination proxy, SSL offloading)
* Predictive analytics: LBs can predict traffic patterns through analytics performed over traffic passing through them.
* Service Discovery: Client's requests are forwarded to appropriate hosting servers by inquiring about the service registry.
* Security: LBs may also improve security by mitigating attacks like denial-of-service at different layers of the OSI model (layer 3, 4 and 7)

### Types of Load Balancer

#### Based on the OSI Layer:

* Layer 4: Operates at TCP/UDP Layer. (Network Load Balancer)
* Layer 7: Operates at application Layer/ Much smarter but slower compared to Layer 4. (Application Load Balancer)

#### Based on the Use case

* GTM - Global Server Load Balancer
  * Using DNS
  * Using ADC
* Local Load Balancer

#### Based on Implementation

* Hardware (Generally operates at Layer 4)
* Software (Generally operates at Layer 7)
* Cloud Based (Load Balancer as a service)

### Global Traffic Management (GTM)

### Global Server Load Balancing

GSLB involves the distribution of traffic load across multiple geographical regions.



#### GSLB using DNS Resolution

DNS lookup can respond with re-ordered IP address list (using round-robin) and using a short TTL can help to distribute the load better.&#x20;

The small size of DNS packet 512Bytes is not enough to include all possible IP addresses. (At max 8)

GTM using DNS generally doesn't have access to the end-user's IP address and resolves based on the nameserver that they are using (generally ISPs) and hence can distribute load un-evenly.

For Akamai, it has access to User's IP Address if; EDNS0 End-User Client Subnet (ECS) is enabled for the domain and the end user is using a resolver with which ​Akamai​ has an ECS agreement, for example Google Public DNS or OpenDNS



Network Traffic -> GSLB -> Local LB -> Server.

#### GTM through ADCs:



### Glossary:

* ADCs - Application Delivery Controllers
  * Security
  * Acceleration
  * Authentication

### References

* [https://www.nginx.com/resources/glossary/load-balancing/](https://www.nginx.com/resources/glossary/load-balancing/)
* [https://techdocs.akamai.com/gtm/docs/gtm-concepts](https://techdocs.akamai.com/gtm/docs/gtm-concepts)
