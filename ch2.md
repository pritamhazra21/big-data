aggregate data models, aggregates, relationships, graph databases, schemaless
databases, materialized views, distribution models, sharding, master-slave
replication, peer-peer replication, sharding and replication, consistency,
relaxing consistency, version stamps, map-reduce, partitioning and combining,
composing map-reduce calculations. 

## What is NoSQL? types of NoSQL.

NoSQL is a type of database management system (DBMS) that is designed to handle and store large volumes of unstructured and semi-structured data. Unlike traditional relational databases that use tables with pre-defined schemas to store data, NoSQL databases use flexible data models that can adapt to changes in data structures and are capable of scaling horizontally to handle growing amounts of data.

The term NoSQL originally referred to “non-SQL” or “non-relational” databases, but the term has since evolved to mean “not only SQL,” as NoSQL databases have expanded to include a wide range of different database architectures and data models.

##### NoSQL databases are generally classified into four main categories:
+ Document databases: These databases store data as semi-structured documents, such as JSON or XML, and can be queried using document-oriented query languages. Examples – MongoDB, CouchDB, Cloudant
+ Key-value stores: These databases store data as key-value pairs, and are optimized for simple and fast read/write operations. Examples – Memcached, Redis, Coherence
+ Column-family stores: These databases store data as column families, which are sets of columns that are treated as a single entity. They are optimized for fast and efficient querying of large amounts of data. Examples – Hbase, Big Table, Accumulo
+ Graph databases: These databases store data as nodes and edges, and are designed to handle complex relationships between data. Examples – Amazon Neptune, Neo4j


## Key feature of NoSQL.

Key Features of NoSQL :

+ Dynamic schema: NoSQL databases do not have a fixed schema and can accommodate changing data structures without the need for migrations or schema alterations.
+ Horizontal scalability: NoSQL databases are designed to scale out by adding more nodes to a database cluster, making them well-suited for handling large amounts of data and high levels of traffic.
+ Document-based: Some NoSQL databases, such as MongoDB, use a document-based data model, where data is stored in semi-structured format, such as JSON or BSON.
+ Key-value-based: Other NoSQL databases, such as Redis, use a key-value data model, where data is stored as a collection of key-value pairs.
+ Column-based: Some NoSQL databases, such as Cassandra, use a column-based data model, where data is organized into columns instead of rows.
+ Distributed and high availability: NoSQL databases are often designed to be highly available and to automatically handle node failures and data replication across multiple nodes in a database cluster.
+ Flexibility: NoSQL databases allow developers to store and retrieve data in a flexible and dynamic manner, with support for multiple data types and changing data structures.
Performance: NoSQL databases are optimized for high performance and can handle a high volume of reads and writes, making them suitable for big data and real-time applications.

## Advantages of NoSQL: 

There are many advantages of working with NoSQL databases such as MongoDB and Cassandra. The main advantages are high scalability and high availability.

1. High scalability : NoSQL databases use sharding for horizontal scaling. Partitioning of data and placing it on multiple machines in such a way that the order of the data is preserved is sharding. Vertical scaling means adding more resources to the existing machine whereas horizontal scaling means adding more machines to handle the data. Vertical scaling is not that easy to implement but horizontal scaling is easy to implement. Examples of horizontal scaling databases are MongoDB, Cassandra, etc. NoSQL can handle a huge amount of data because of scalability, as the data grows NoSQL scale itself to handle that data in an efficient manner.
1. Flexibility: NoSQL databases are designed to handle unstructured or semi-structured data, which means that they can accommodate dynamic changes to the data model. This makes NoSQL databases a good fit for applications that need to handle changing data requirements.
1. High availability : Auto replication feature in NoSQL databases makes it highly available because in case of any failure data replicates itself to the previous consistent state.
1. Scalability: NoSQL databases are highly scalable, which means that they can handle large amounts of data and traffic with ease. This makes them a good fit for applications that need to handle large amounts of data or traffic
1. Performance: NoSQL databases are designed to handle large amounts of data and traffic, which means that they can offer improved performance compared to traditional relational databases.
1. Cost-effectiveness: NoSQL databases are often more cost-effective than traditional relational databases, as they are typically less complex and do not require expensive hardware or software.
1. Agility: Ideal for agile development.
## Disadvantages of NoSQL: 

NoSQL has the following disadvantages.

1. Lack of standardization :  There are many different types of NoSQL databases, each with its own unique strengths and weaknesses. This lack of standardization can make it difficult to choose the right database for a specific application
1. Lack of ACID compliance : NoSQL databases are not fully ACID-compliant, which means that they do not guarantee the consistency, integrity, and durability of data. This can be a drawback for applications that require strong data consistency guarantees.
1. Narrow focus : NoSQL databases have a very narrow focus as it is mainly designed for storage but it provides very little functionality. Relational databases are a better choice in the field of Transaction Management than NoSQL.
1. Open-source : NoSQL is open-source database. There is no reliable standard for NoSQL yet. In other words, two database systems are likely to be unequal.
1. Lack of support for complex queries : NoSQL databases are not designed to handle complex queries, which means that they are not a good fit for applications that require complex data analysis or reporting.
1. Lack of maturity : NoSQL databases are relatively new and lack the maturity of traditional relational databases. This can make them less reliable and less secure than traditional databases.
1. Management challenge : The purpose of big data tools is to make the management of a large amount of data as simple as possible. But it is not so easy. Data management in NoSQL is much more complex than in a relational database. NoSQL, in particular, has a reputation for being challenging to install and even more hectic to manage on a daily basis.
1. GUI is not available : GUI mode tools to access the database are not flexibly available in the market.
1. Backup : Backup is a great weak point for some NoSQL databases like MongoDB. MongoDB has no approach for the backup of data in a consistent manner.
1. Large document size : Some database systems like MongoDB and CouchDB store data in JSON format. This means that documents are quite large (BigData, network bandwidth, speed), and having descriptive key names actually hurts since they increase the document size.

## Difference between SQL and NoSQL
![image](https://github.com/pritamhazra21/big-data/assets/75198912/7c9614cc-3d15-4adb-8e56-f1074b29c19f)

## Key Value data model

A key-value data model or database is also referred to as a key-value store. It is a non-relational type of database. In this, an associative array is used as a basic database in which an individual key is linked with just one value in a collection. For the values, keys are special identifiers. Any kind of entity can be valued. The collection of key-value pairs stored on separate records is called key-value databases and they do not have an already defined structure.

![image](https://github.com/pritamhazra21/big-data/assets/75198912/84239e88-30b1-4508-a18b-3edc54c65dcb) 

#### How do key-value databases work?
A number of easy strings or even a complicated entity are referred to as a value that is associated with a key by a key-value database, which is utilized to monitor the entity. Like in many programming paradigms, a key-value database resembles a map object or array, or dictionary, however, which is put away in a tenacious manner and controlled by a DBMS.

An efficient and compact structure of the index is used by the key-value store to have the option to rapidly and dependably find value using its key. For example, Redis is a key-value store used to tracklists, maps, heaps, and primitive types (which are simple data structures) in a constant database. Redis can uncover a very basic point of interaction to query and manipulate value types, just by supporting a predetermined number of value types,  and when arranged, is prepared to do high throughput.

#### When to use a key-value database:
Here are a few situations in which you can use a key-value database:-

+ User session attributes in an online app like finance or gaming, which is referred to as real-time random data access.
+ Caching mechanism for repeatedly accessing data or key-based design.
+ The application is developed on queries that are based on keys.
#### Features:
+ One of the most un-complex kinds of NoSQL data models.
+ For storing, getting, and removing data, key-value databases utilize simple functions.
+ Querying language is not present in key-value databases.
+ Built-in redundancy makes this database more reliable.
#### Advantages:
+ It is very easy to use. Due to the simplicity of the database, data can accept any kind, or even different kinds when required.
+ Its response time is fast due to its simplicity, given that the remaining environment near it is very much constructed and improved.
+ Key-value store databases are scalable vertically as well as horizontally.
+ Built-in redundancy makes this database more reliable.
#### Disadvantages:
+ As querying language is not present in key-value databases, transportation of queries from one database to a different database cannot be done.
+ The key-value store database is not refined. You cannot query the database without a key.
#### Some examples of key-value databases:
Here are some popular key-value databases which are widely used:

+ Couchbase: It permits SQL-style querying and searching for text.
+ Amazon DynamoDB: The key-value database which is mostly used is Amazon DynamoDB as it is a trusted database used by a large number of users. It can easily handle a large number of requests every day and it also provides various security options.
+ Riak: It is the database used to develop applications.
+ Aerospike: It is an open-source and real-time database working with billions of exchanges.
+ Berkeley DB: It is a high-performance and open-source database providing scalability.


## Document data model
A Document Data Model is a lot different than other data models because it stores data in JSON, BSON, or XML documents. in this data model, we can move documents under one document and apart from this, any particular elements can be indexed to run queries faster. Often documents are stored and retrieved in such a way that it becomes close to the data objects which are used in many applications which means very less translations are required to use data in applications. JSON is a native language that is often used to store and query data too. 

So in the document data model, each document has a key-value pair below is an example for the same.
```
{
"Name" : "Yashodhra",
"Address" : "Near Patel Nagar",
"Email" : "yahoo123@yahoo.com",
"Contact" : "12345"
}
```
##### Working of Document Data Model: 
This is a data model which works as a semi-structured data model in which the records and data associated with them are stored in a single document which means this data model is not completely unstructured. The main thing is that data here is stored in a document.

##### Features:
+ Document Type Model: As we all know data is stored in documents rather than tables or graphs, so it becomes easy to map things in many programming languages.
+ Flexible Schema: Overall schema is very much flexible to support this statement one must know that not all documents in a collection need to have the same fields.
+ Distributed and Resilient: Document data models are very much dispersed which is the reason behind horizontal scaling and distribution of data.
+ Manageable Query Language: These data models are the ones in which query language allows the developers to perform CRUD (Create Read Update Destroy) operations on the data model. 
##### Examples of Document Data Models :

+ Amazon DocumentDB
+ MongoDB
+ Cosmos DB
+ ArangoDB
+ Couchbase Server
+ CouchDB
##### Advantages:
+ Schema-less: These are very good in retaining existing data at massive volumes because there are absolutely no restrictions in the format and the structure of data storage. 
+ Faster creation of document and maintenance: It is very simple to create a document and apart from this maintenance requires is almost nothing.
+ Open formats: It has a very simple build process that uses XML, JSON, and its other forms.
+ Built-in versioning: It has built-in versioning which means as the documents grow in size there might be a chance they can grow in complexity. Versioning decreases conflicts.
##### Disadvantages:
+ Weak Atomicity: It lacks in supporting multi-document ACID transactions. A change in the document data model involving two collections will require us to run two separate queries i.e. one for each collection. This is where it breaks atomicity requirements.
+ Consistency Check Limitations: One can search the collections and documents that are not connected to an author collection but doing this might create a problem in the performance of database performance.
+ Security: Nowadays many web applications lack security which in turn results in the leakage of sensitive data. So it becomes a point of concern, one must pay attention to web app vulnerabilities.
##### Applications of Document Data Model :
+ Content Management: These data models are very much used in creating various video streaming platforms, blogs, and similar services Because each is stored as a single document and the database here is much easier to maintain as the service evolves over time.
+ Book Database: These are very much useful in making book databases because as we know this data model lets us nest.
+ Catalog: When it comes to storing and reading catalog files these data models are very much used because it has a fast reading ability if incase Catalogs have thousands of attributes stored.
+ Analytics Platform: These data models are very much used in the Analytics Platform.
## CAP theorem

The CAP theorem, also known as Brewer's theorem, is a fundamental principle in distributed systems and database design, including NoSQL databases. It states that in a distributed system, it is impossible to simultaneously guarantee all three of the following properties:

1. Consistency (C): Every read operation will return the most recent write or an error. In other words, all nodes in the system will have the same view of data at any given time.

2. Availability (A): Every request receives a response, regardless of the success or failure of individual nodes. The system remains operational even if some nodes fail.

3. Partition tolerance (P): The system continues to operate despite the presence of network partitions, i.e., the system can be divided into separate groups of nodes that cannot communicate with each other.

According to the CAP theorem, when a network partition occurs (P), a distributed system must choose between either consistency (C) or availability (A). In other words, it must decide whether to continue providing responses, possibly returning stale or conflicting data (available but not consistent), or to stop responding until consistency can be guaranteed.

NoSQL databases, which are designed to scale horizontally and handle large volumes of data, often prioritize availability and partition tolerance over strong consistency. This means that in the event of a network partition, NoSQL databases may choose to provide availability by allowing different nodes to diverge and return potentially inconsistent data. This trade-off allows the system to remain operational and handle high loads even in the face of failures or network partitions.

It's important to note that the CAP theorem does not imply that a system can only have two out of the three properties. Instead, it states that during a network partition, a system must make a trade-off between consistency and availability. Different NoSQL databases make different choices depending on their specific design goals and requirements, resulting in various consistency models such as eventual consistency, strong eventual consistency, or causal consistency.
