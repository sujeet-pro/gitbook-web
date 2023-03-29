# Consistency

Different meanings of consistency

* Each replica node has the same view of data at a given point in time.
* Each read request gets the value of the recent write.



### Spectrum of Consistency Models

* Strict consistency / linearizability
* Sequencial consistency
* Causal consistency
* Eventual consistency



### Eventual Consistency

Eventual consistency ensures that all the replicas will eventually return the same value to the read request, but the returned value isn’t meant to be the latest value. However, the value will finally reach its latest state.

> Note: Cassandra is a highly available NoSQL database that provides eventual consistency.

Usecase example:

The **domain name system** is a highly available system that enables name lookups to a hundred million devices across the Internet. It uses an eventual consistency model and doesn’t necessarily reflect the latest values.



### Causal Consistency

Causal consistency works by categorizing operations into dependent and independent operations. **Dependent operations** are also called causally-related operations. Causal consistency preserves the order of the causally-related operations.

Causal consistency is weaker overall, but stronger than the eventual consistency model. It’s used to prevent non-intuitive behaviors.

#### Example

The causal consistency model is used in a commenting system. For example, for the replies to a comment on a Facebook post, we want to display comments after the comment it replies to. This is because there is a cause-and-effect relationship between a comment and its replies.



### Sequential Consistency

Sequential consistency is stronger than the causal consistency model. It preserves the ordering specified by each client’s program. However, sequential consistency doesn’t ensure that the writes are visible instantaneously or in the same order as they occurred according to some global clock.

#### Example

In social networking applications, we usually don’t care about the order in which some of our friends’ posts appear. However, we still anticipate a single friend’s posts to appear in the correct order in which they were created). Similarly, we expect our friends’ comments in a post to display in the order that they were submitted. The sequential consistency model captures all of these qualities.



### Strict Consistency aka Linearizability

Linearizable services appear to carry out transactions/operations in sequential, real-time order.

Synchronous replication ensures linearizability, in which an acknowledgment is not sent to the client until the new value is written to all replicas.

\
Linearizability affects the system’s availability, which is why it’s not always used. Applications with strong consistency requirements use techniques like **quorum-based replication** to increase the system’s availability.

> Note: **Amazon Aurora** provides strong consistency.

#### Example

Updating an account’s password requires strict consistency. For example, if we suspect suspicious activity on our bank account, we immediately change our password so that no unauthorized users can access our account. If it were possible to access our account using an old password due to a lack of strict consistency, then changing passwords would be a useless security strategy.
