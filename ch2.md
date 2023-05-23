## CAP theorem

The CAP theorem, also known as Brewer's theorem, is a fundamental principle in distributed systems and database design, including NoSQL databases. It states that in a distributed system, it is impossible to simultaneously guarantee all three of the following properties:

1. Consistency (C): Every read operation will return the most recent write or an error. In other words, all nodes in the system will have the same view of data at any given time.

2. Availability (A): Every request receives a response, regardless of the success or failure of individual nodes. The system remains operational even if some nodes fail.

3. Partition tolerance (P): The system continues to operate despite the presence of network partitions, i.e., the system can be divided into separate groups of nodes that cannot communicate with each other.

According to the CAP theorem, when a network partition occurs (P), a distributed system must choose between either consistency (C) or availability (A). In other words, it must decide whether to continue providing responses, possibly returning stale or conflicting data (available but not consistent), or to stop responding until consistency can be guaranteed.

NoSQL databases, which are designed to scale horizontally and handle large volumes of data, often prioritize availability and partition tolerance over strong consistency. This means that in the event of a network partition, NoSQL databases may choose to provide availability by allowing different nodes to diverge and return potentially inconsistent data. This trade-off allows the system to remain operational and handle high loads even in the face of failures or network partitions.

It's important to note that the CAP theorem does not imply that a system can only have two out of the three properties. Instead, it states that during a network partition, a system must make a trade-off between consistency and availability. Different NoSQL databases make different choices depending on their specific design goals and requirements, resulting in various consistency models such as eventual consistency, strong eventual consistency, or causal consistency.
