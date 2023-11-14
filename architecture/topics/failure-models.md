# Failure Models

List of failure models in order of increasing difficulty to deal with it.

* Fail-stop
* Crash
* Omission
* Temporal
* Byzantine

### Fail-stop

A node in the distributed systems halts permanently. However, the other nodes can still detect that node by communicating with it.



### Crash

In this type of failure, a node in the distributed system halts silently, and the other nodes can't detect that the node has stopped working.



### Omission Failures

In omission failures, the node fails to send or receive messages.&#x20;

* **Send Omission Failures**: The node fails to respond to the incoming request.
* **Receive Omission Failure**: The nod fails to receive the request and thus can't acknowledge it.



### Temporal Failures

The node generates correct results, but is too late to be useful. The failure could be due to bad algorithms, a bad design strategy or a loss of synchronization between the processor clocks.



### Byzantine Failures

The node exhibits random behaviour like transmitting arbitrary messages at arbitrary times, producing wrong results, or stopping midway. This mostly happens due to an attack by a malicious entity or a software bug.

