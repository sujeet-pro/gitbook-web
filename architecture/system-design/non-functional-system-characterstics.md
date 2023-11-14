# Non Functional System Characterstics

### Availability

Availability is the percentage of time that some service or infrastructure is accessible to clients and is operated upon under normal conditions

| Availability        | Downtime per year | Downtime per month | Downtime per week |
| ------------------- | ----------------- | ------------------ | ----------------- |
| 90% (1 nine)        | 36.5 days         | 72 hours           | 16.8 hours        |
| 99% (2 nines)       | 3.65 days         | 7.20 hours         | 1.68 hours        |
| 99.5% (2 nines)     | 1.83 days         | 3.60 hours         | 50.4 minutes      |
| 99.9% (3 nines)     | 8.76 hours        | 43.8 minutes       | 10.1 minutes      |
| 99.99% (4 nines)    | 52.56 minutes     | 4.32 minutes       | 1.01 minutes      |
| 99.999% (5 nines)   | 5.26 minutes      | 25.9 seconds       | 6.05 seconds      |
| 99.9999% (6 nines)  | 31.5 seconds      | 2.59 seconds       | 0.605 seconds     |
| 99.99999% (7 nines) | 3.15 seconds      | 0.259 seconds      | 0.0605 seconds    |

### Reliability

Reliability, R, is the probability that the service will perform its functions for a specified time. R measures how the service performs under varying operating conditions.

We often use **mean time between failures (MTBF)** and **mean time to repair (MTTR)** as metrics to measure `R`.



MTBF = (Total Elapsed Time - Sum of Downtime) / Total Numbers of Failures

MTTR = Total Maintenance Time / Total Number of Repairs

We stribe for higher MTBF and lower MTTR.



Reliability and availability are two important metrics to measure compliance of service to agreed-upon **service level objectives (SLO)**.

### Scalability

&#x20;Scalability is the ability of a system to handle an increasing amount of workload without compromising performance.

Kind of workload:

* **Request workload:** This is the numner of requests served by the system.
* **Data/Storage Workload**: This is the amount of data stored by the system.

#### Dimensions of scalability

* Size scalability: If we can add additional users and resources to it.
* Administrative scalability: Capacity for a growing number of organizations o rusers to share a single distributed system with ease.
* Geographical scalability: How easily the program can cater to other regions while maintaining acceptable performance constraints.

### Maintainability

**Operability:** This is the ease with which we can ensure the system’s smooth operational running under normal circumstances and achieve normal conditions under a fault.

**Lucidity:** This refers to the simplicity of the code. The simpler the code base, the easier it is to understand and maintain it, and vice versa.

**Modifiability:** This is the capability of the system to integrate modified, new, and unforeseen features without any hassle.

MTTR= Total Number of Repairs / Total Maintenance Time ​

#### Maintainability and reliability

Maintainability can be defined more clearly in close relation to reliability. The only difference between them is the variable of interest. Maintainability refers to `time-to-repair`, whereas reliability refers to both `time-to-repair` and the `time-to-failure`. Combining maintainability and reliability analysis can help us achieve availability, downtime, and uptime insights.

### **Fault Tolerance**

**Fault tolerance** refers to a system’s ability to execute persistently even if one or more of its components fail. Here, components can be software or hardware

#### Replication

We can replicate both the services and data. We can swap out failed nodes with healthy ones and a failed data store with its replica.

#### Checkpointing

Checkpointing is a technique that saves the system’s state in stable storage when the system state is consistent. Checkpointing is performed in many stages at different time intervals. The primary purpose is to save the computational state at a given point. When a failure occurs in the system, we can get the last computed data from the previous checkpoint and start working from there.
