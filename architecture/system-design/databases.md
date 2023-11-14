# Databases

### RDBMS

#### ACID

* **Atomicity:** A transaction is considered an atomic unit. Therefore, either all the statements within a transaction will successfully execute, or none of them will execute. If a statement fails within a transaction, it should be aborted and rolled back.
* **Consistency:** At any given time, the database should be in a consistent state, and it should remain in a consistent state after every transaction. For example, if multiple users want to view a record from the database, it should return a similar result each time.
* **Isolation:** In the case of multiple transactions running concurrently, they shouldn’t be affected by each other. The final state of the database should be the same as the transactions were executed sequentially.
* **Durability:** The system should guarantee that completed transactions will survive permanently in the database even in system failure events.

#### Benifits&#x20;

* Flexibility
* Reduced Redundancy (Via Normalizations)
* Concurrency
* Integration

#### Drawbacks

* **Impedance mismatch** is the difference between the relational model and the in-memory data structures.

### No-SQL

#### Types

* Key-Value Store. - Dynamodb
* Document - Mongodb
* Column Oriented / Columner - Cassandra
* Graph - Neo DB
