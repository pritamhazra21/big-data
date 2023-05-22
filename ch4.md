 unit tests with MRUnit, test data and local tests,
anatomy of MapReduce job run, classic Map-reduce, YARN, failures in classic
Map-reduce and YARN, job scheduling, shuffle and sort, task execution,
MapReduce types, input formats, output formats

## 1. MapReduce workflow

MapReduce is a programming model and software framework used for processing and analyzing large data sets in a distributed computing environment. It was popularized by Google and has become widely adopted in the field of big data analytics. The MapReduce framework breaks down a data processing task into two main phases: the map phase and the reduce phase.

Here's a high-level overview of how MapReduce works:

1. Input data splitting: The input data is divided into smaller chunks or blocks that can be processed independently. Each block is assigned to a processing node in a distributed cluster.

2. Map phase: The map phase involves processing the input data in parallel. Each processing node receives a subset of the input data and applies a map function to it. The map function takes this input, performs some specific operation, and emits intermediate key-value pairs.

3. Shuffle and sort: The intermediate key-value pairs produced by the map phase are sorted and grouped based on their keys. This step is necessary to ensure that all intermediate values associated with the same key are brought together.

4. Reduce phase: In this phase, each processing node receives a subset of the sorted intermediate key-value pairs. A reduce function is applied to these key-value pairs, where the reduce function takes a key and the corresponding list of values and performs some aggregation or summarization operation. The reduce function emits the final output key-value pairs.

5. Final output: The output key-value pairs produced by the reduce phase are collected and combined to generate the final result of the MapReduce job.

The key idea behind MapReduce is its ability to parallelize and distribute the processing of large datasets across a cluster of machines. By breaking down the data into smaller subsets and performing parallel operations on each subset, MapReduce allows for efficient processing and analysis of big data.

The MapReduce framework provides fault tolerance by automatically handling failures of individual nodes. If a node fails during the computation, the framework redistributes the failed node's work to other available nodes in the cluster.

It's worth noting that while MapReduce is a powerful and widely used framework, there have been advancements in distributed computing frameworks and technologies since its introduction. Alternatives such as Apache Spark, which provides more flexibility and improved performance, are now commonly used for big data processing.

![image](https://github.com/pritamhazra21/big-data/assets/75198912/49304c2c-0dbc-4d5d-a35e-c968eb6231db)

## 2. What are the failures of classic mapreduce.

In classic MapReduce, there are a few potential points of failure that can occur during the data processing job:

1. Node failure: If one or more nodes in the cluster fail during the execution of the MapReduce job, it can lead to data loss or interruptions in the processing. Classic MapReduce frameworks typically handle node failures by redistributing the failed node's work to other available nodes in the cluster.

2. Network failure: Network failures can disrupt communication between nodes in the cluster, affecting the overall performance and completion of the MapReduce job. The framework may have mechanisms to handle network failures and retry failed communications.

3. Task failure: Each map or reduce task in the MapReduce job can fail due to errors or exceptions in the code or data. The framework usually detects task failures and retries the failed tasks on different nodes to ensure completion.

4. Resource limitations: If the available resources, such as memory or disk space, become insufficient during the MapReduce job, it can cause failures or slow down the processing. Monitoring and managing resources effectively are essential to prevent such failures.

Classic MapReduce frameworks, like Apache Hadoop MapReduce, provide fault tolerance mechanisms to handle these failures. They typically have features like speculative execution, where redundant tasks are executed on different nodes to compensate for slow-running tasks or failed nodes. Additionally, checkpointing and data replication strategies are employed to ensure data durability and availability in case of failures.

It's important to note that more recent big data processing frameworks, like Apache Spark, have introduced improvements and advancements over the classic MapReduce model, addressing some of the limitations and failure scenarios.

## 3. What are the types of mapreduce ?

In the context of big data processing, there are different types or variations of the MapReduce model. Some of the notable types of MapReduce include:

1. Classic MapReduce: This refers to the original MapReduce model introduced by Google. It consists of a map phase where data is processed in parallel, a shuffle and sort phase to group and sort the intermediate key-value pairs, and a reduce phase for final aggregation. Classic MapReduce is implemented in frameworks like Apache Hadoop MapReduce.

2. Iterative MapReduce: This type of MapReduce is designed for iterative algorithms, where the same computation is repeated multiple times with different inputs. It reduces the overhead of reading and writing data from storage in each iteration by keeping intermediate results in memory or on disk. This helps to improve performance for iterative tasks.

3. Streaming MapReduce: Streaming MapReduce allows for continuous processing of data streams rather than batch processing. It enables the processing of data as it arrives in a continuous and incremental manner. Streaming MapReduce frameworks, such as Apache Storm or Apache Flink, provide mechanisms to handle data streams and perform computations in real-time.

4. Distributed MapReduce: Distributed MapReduce extends the basic MapReduce model to work with distributed file systems and across multiple nodes in a cluster. It enables the parallel processing and distributed storage of large-scale data sets, providing scalability and fault tolerance. Distributed MapReduce frameworks, like Apache Hadoop MapReduce, allow for processing data stored in distributed file systems like HDFS (Hadoop Distributed File System).

5. In-Memory MapReduce: In-Memory MapReduce frameworks, such as Apache Spark, leverage the power of distributed memory to store and process intermediate data in memory rather than writing it to disk. This can significantly improve the performance of MapReduce jobs by reducing disk I/O overhead.

These variations of the MapReduce model cater to different requirements and use cases in big data processing, providing flexibility and efficiency based on the specific data processing needs.

## 4. unit tests with MRUnit

MRUnit is a testing framework specifically designed for unit testing MapReduce jobs. It provides utilities and APIs to write unit tests for MapReduce code, enabling developers to validate the correctness of their MapReduce logic in isolation. Here's an overview of how you can use MRUnit for unit testing MapReduce jobs:

1. Setup: Start by including the MRUnit library in your project's dependencies. MRUnit is available for Java, and you can typically include it using a build automation tool like Maven or Gradle.

2. Write test cases: Create test classes and methods to define your unit tests. Each test method should focus on a specific aspect or functionality of your MapReduce job. You'll typically write multiple test methods to cover different scenarios and use cases.

3. Set up input data: Define the input data that your MapReduce job will process. This can be sample input files or mock data. You may need to set up the input data in a way that represents the input format and structure expected by your MapReduce code.

4. Configure the job: Configure the MapReduce job to be tested, including setting up the input and output paths, specifying mapper and reducer classes, and configuring any other necessary job parameters.

5. Write assertions: Define the expected output data or results that your MapReduce job should produce. This can include key-value pairs, counters, or any other output generated by your MapReduce logic. Write assertions in your test methods to validate that the actual output matches the expected output.

6. Run the test: Use the MRUnit APIs to run the MapReduce job in the test environment. Provide the input data and verify the output using the assertions you defined. MRUnit provides methods to simulate the execution of MapReduce phases, allowing you to test your mappers and reducers independently.

7. Verify the results: After running the test, check if the actual output matches the expected output defined in your assertions. MRUnit provides assertion methods to compare the output produced by the MapReduce job with the expected values.

By following these steps, you can use MRUnit to write unit tests for your MapReduce code, ensuring that your MapReduce logic functions correctly and handles different input scenarios as expected.
