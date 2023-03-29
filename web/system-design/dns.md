---
description: Domain Name System
---

# DNS

DNS is a hierarchical and distributed naming system that converts a domain name to an IP Address.



### DNS Hierarchy

#### DNS Resolver

Resolvers initiate the querying sequence and forward requests to other DNS name servers.

#### Root level Name Servers

Root name servers maintain name servers based on the top-level domain names, such as `.com, .edu,.us` and so on.&#x20;

There are 13 logical root name servers with many instances spread throughout the globe and are managed by 12 diffferent organizations.

`[a-m].root-servers.net`

[https://www.iana.org/domains/root/servers](https://www.iana.org/domains/root/servers)

#### Top-level domain (TLD) Name servers

These servers hold the IP addresses of authoritative name servers. The querying party will get a list of IP addresses that belong to the authoritative servers of the organizations.

#### Authoritative Name servers

These are organization's DNS name servers that provide the IP address of the web or applications servers. These maintain all the resource records that you configure eg. A, CNAME, MX, etc.



### Iterative Vs Recursive Query Resolution

**Iterative**: The local server requests the root, TLD, and the authoritative servers for the IP address.&#x20;

**Recursive**: The end user requests the local server. The local server further requests the root DNS name servers. The root name servers forward the requests to other name servers.

> **Note:** Typically, an iterative query is preferred to reduce query load on DNS infrastructure.

### Caching

Caching refers to temporary storage of frequently requested resource records.



### Resource Records

#### CNAME

#### A Records

#### MX Records

### DNS as a distributed system

#### Highly scalable

Due to its hierarchical nature, DNS is a highly scalable system. Roughly 1,000 replicated instances of 13 root-level servers are spread throughout the world strategically to handle user queries. The working labor is divided among TLD and root servers to handle a query and, finally, the authoritative servers that are managed by the organizations themselves to make the entire system work.

#### Reliable

* **Caching**: The caching is done in the browser, OS, local name server, ISP DNS. Caching can results in showing outdated information and to mitigate this issue, each cached record comes with an expiration time called time-to-live (TTL).
* **Server Replication**: DNS has replicated copies of each logical server spread systematically across the globe to entertain user requests at low latency.
* **Protocol:** UDP (User Datagram Protocol). A DNS resolver can resend the UDP request if it didn't get a reply to a previous one. This just need 1 round trip instead of 3-way handshake before data exchange in case of TCP.&#x20;
  * DNS can use TCP when its message size exceeds the original packet size of 512 Bytes.
  * DNS always use **TCP for zone transfers.**

#### **Consistent**

DNS compromises on strong consistency to achieve high performance because data is read frequently from DNS databases as compared to writing. However, DNS provides eventual consistency and updates records on replicated servers lazily.
