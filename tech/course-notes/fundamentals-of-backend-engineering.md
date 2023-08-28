# Fundamentals of Backend Engineering

### Request Response Model

* Web, HTTP, DNS, SSH
* RPC (Remote procedure call)
* SQL & Database Protocols
* APIs (REST/SOAP/GraphQL

#### Doesn't work&#x20;

* Notification service
* Chatting application
* Very long running requests
* What if client disconnects
* What about alternatives.

#### Anatomy of Request / Response

```
METHOD PATH HTTP_VERSION
HEADERS
<CRLF>
BODY

Eg.
GET / HTTP/1.1
Headers
```



Eg: Building an upload image service with request / response

* Send large request with the image (simple)
* Chunk image and send a request per chunk (resumable)

#### Asynchronous I/O

* Caller sends a request
* Caller can work until it gets a response
* Caller either
  * Checks if the response is ready (epoll)
  * Receiver calls back when it's done (io\_uring)
  * Spins up a new thread that blocks.

Example of an OS asynchronous call (NodeJS)

* Program spins up a secondary thread
* Secondary thread reads from disk, OS blocks it
* Main program still running and executing code
* Thread finish reading and calls back main thread.

#### Asynchronous workloads

* Ashynchronous programming (promises/futures)
* Asynchronous backend processing
  * Reply immediately with a job Id, and request can go to a queue.
* Asynchronous commits in postgres
* Asynchronous IO in linux (epoll, io\_uring)
* Asynchronous replication
* Asynchronous OS fsync (fs cache)

### Push

* Pros
  * Real time
* Cons
  * Clients must be online
  * Clients might not be able to handle&#x20;
  * Requires a bidirectional protocol
  * Polling is preferred for light clients
  *

### Polling

#### Short Polling

* &#x20;Client sends a request
* Server responds immediately with a handle
* Server continues to process the request
* Client uses that handle to check for status
* Multiple "short" request response as polls

Pros

* Simple
* Good for long running requests
* Client can disconnect

Cons

* Too chatty
* Network bandwidth
* Wasted Backend resources

#### Long Polling

Request is taking long, I'll check with you later. But talk to me only when it's ready.



### Server Sent Events

* Vanilla request/response isn't ideal for notification backend
* Client wants real time notification from backend
  * A user just logged in
  * A message is just received
* Push works but restrictive
* Server sent events work with request/response

What is it

* It is a reqeust but an unending response

Pros

* Real time
* Compatibility with Request/response

Cons

* Clients must be online
* Clients might not be able to handle
* Polling is preferred for light clients
* HTTP/1.1 problem (up to 6 connections in browsers)

Notes:

Client Side uses `EventSource` to read messages.\
Server side sends an content type header as `text/event-stream`

### Publisher Subscriber

One publisher, many reader

Where regular sequential api breaks

* Youtube example - Upload service, compress service, format service, Notification service, copyright service
* Pros
  * Elegant and simple
  * Scalable
* Cons
  * Bad for multiple receivers
  * Hight coupling
  * Client/server have to be running
  * Chaining

Pub Sub

* Pros
  * Scales w/ multiple receivers
  * Great for microservices
  * Loose coupling
  * Works while clients not running
* Cons
  * Message delivery issues&#x20;
    * At least once delivery
  * Complexity
  * Network saturation

### Multiplexing vs Demultiplexing&#x20;

(h2 proxying vs connection pooling)

### Stateful vs Stateless

### Sidecar pattern

ALPN - TSL Extenstion - Application Layer Protocal Negotiation

Eg: Linkerd



### Protocols

#### Protocol properties

* Data Format
  * Text Based (plain text, json, xml)
  * Binary (protobuf, RESP, h2, h3)
* Transfer mode
  * Message based (UDP, HTTP)
  * Stream (TCP, WebRTC)
* Addressing System
  * DNS name, IP, MAC
* Directionality
  * Bidirectional (TCP)
  * Unidirectional (HTTP)
  * Full/Half duplex



