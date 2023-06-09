# Chapter 4
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

## 5. test data and local tests

When it comes to testing MapReduce jobs using MRUnit, you have a couple of options for providing test data and running tests locally. Here's how you can handle test data and perform local tests:

1. Generating test data: You can generate test data programmatically within your test cases. For example, you can create a small dataset using hardcoded values or use libraries to generate synthetic data that represents the input your MapReduce job expects.

2. Sample input data: If you have sample input data that you want to use for testing, you can include it in your test resources. Create input files or directories containing the data you want to process. MRUnit allows you to specify the input paths for your MapReduce job, so you can point it to the sample data you've included in your test resources.

3. Local testing: MRUnit allows you to execute MapReduce jobs in a local test environment, simulating the MapReduce execution on a single machine. This is useful for running tests quickly and verifying the correctness of your MapReduce code without the need for a full Hadoop cluster. MRUnit provides utilities to set up the local testing environment and execute the MapReduce job using the local runner.

Here's a simple example demonstrating how to use MRUnit for local testing:
```

@RunWith(MockitoJUnitRunner.class)
public class MyMapReduceTest {

    @Test
    public void testMapReduceJob() throws Exception {
        // Set up the test input
        List<Pair<LongWritable, Text>> input = new ArrayList<>();
        input.add(new Pair<>(new LongWritable(1), new Text("input data")));

        // Set up the expected output
        List<Pair<Text, IntWritable>> expectedOutput = new ArrayList<>();
        expectedOutput.add(new Pair<>(new Text("input"), new IntWritable(1)));
        expectedOutput.add(new Pair<>(new Text("data"), new IntWritable(1)));

        // Create an instance of your MapReduce job
        MyMapReduceJob job = new MyMapReduceJob();

        // Configure the job and set the input path
        job.setMapperClass(MyMapper.class);
        job.setReducerClass(MyReducer.class);
        job.setInputPath(new Path("input"));

        // Create a test driver
        MapReduceDriver<LongWritable, Text, Text, IntWritable, Text, IntWritable> driver =
                MapReduceDriver.newMapReduceDriver(job);

        // Set the input and expected output
        driver.withAll(input);
        driver.withAllOutput(expectedOutput);

        // Run the test
        List<Pair<Text, IntWritable>> output = driver.run();

        // Perform assertions on the output
        Assert.assertEquals(expectedOutput, output);
    }
}

```

In the above example, MyMapReduceJob represents your actual MapReduce job class, MyMapper and MyReducer represent your mapper and reducer implementations, respectively. You can configure the job, set up the input data, and define the expected output. Then, you can run the test using MRUnit's MapReduceDriver and perform assertions on the output.

By providing test data and running tests locally with MRUnit, you can effectively validate the correctness of your MapReduce code in a controlled and isolated environment.


## 6. Anatomy of MapReduce job run

The anatomy of a MapReduce job run consists of several steps that take place from the submission of the job to the completion of its execution. Here's a high-level overview of the key stages involved:

1. Job submission: The MapReduce job is submitted to the cluster for execution. The job submission includes specifying the input and output paths, configuring job parameters, and providing the necessary code (mappers, reducers, etc.).

2. Job initialization: Once the job is submitted, the cluster's resource manager (e.g., YARN) initializes the necessary resources for the job, including allocating containers to run the mappers and reducers.

3. Map phase: The input data is divided into splits, and each split is assigned to a mapper. The mappers read their respective input splits, apply the map function to each input record, and generate intermediate key-value pairs.

4. Shuffle and sort: The intermediate key-value pairs produced by the mappers are partitioned, shuffled, and sorted based on their keys. This ensures that all values for a particular key are grouped together, facilitating the subsequent reduce phase.

5. Reduce phase: The sorted intermediate key-value pairs are input to the reducers. Each reducer processes a subset of the intermediate data, applies the reduce function to the values associated with each key, and generates the final output key-value pairs.

6. Output generation: The output key-value pairs from the reducers are collected and written to the specified output location, typically a distributed file system like HDFS. The output can be in various formats, such as text files, sequence files, or other custom formats.

7. Job completion: Once the output is generated, the MapReduce job is considered complete. The job status is updated, and any final cleanup tasks may be performed.

Throughout the process, the cluster's resource manager monitors the progress of the job, manages task scheduling and allocation, and handles failures by rescheduling or restarting failed tasks.

It's important to note that the actual execution and internal mechanisms may vary depending on the specific MapReduce framework being used, such as Apache Hadoop MapReduce or Apache Spark. Additionally, advanced optimizations and features, like speculative execution or combiners, may be employed to improve performance and fault tolerance in the MapReduce job execution.

## 7. YARN

YARN (Yet Another Resource Negotiator) is a key component of the Apache Hadoop ecosystem that serves as a resource management and job scheduling framework. It provides a flexible and scalable architecture for managing resources and running distributed applications in a Hadoop cluster.

Here are the main features and components of YARN:

1. Resource Manager (RM): The Resource Manager is the central component of YARN and serves as the master of the cluster. It is responsible for resource allocation, monitoring, and scheduling of applications. The RM manages the allocation of cluster resources to different applications and tracks their status.

2. Node Manager (NM): Each node in the Hadoop cluster runs a Node Manager, which is responsible for managing resources on that node. The Node Manager communicates with the Resource Manager to request and release resources, monitor container health, and report node status.

3. Application Master (AM): Each application running on YARN has an Application Master that manages its execution. The Application Master negotiates resources with the Resource Manager, tracks task progress, and coordinates the execution of tasks on the cluster. The AM is specific to the application framework being used (e.g., MapReduce, Spark), and multiple AMs can run concurrently on the cluster.

4. Containers: YARN uses containers as the basic unit of resource allocation. A container represents a specific amount of resources (CPU, memory) on a node and is assigned to execute a specific task or process. Containers are managed by the Node Manager and are allocated by the Resource Manager based on the resource requirements specified by the Application Master.

5. Application Lifecycle: YARN supports the execution of various distributed applications, such as MapReduce, Spark, Hive, and others. It provides a unified framework for running and managing these applications, enabling them to coexist and share cluster resources efficiently. YARN handles the lifecycle of applications, including their submission, resource negotiation, execution, and termination.

6. Scheduling: YARN supports pluggable scheduling policies and allows administrators to choose different scheduling algorithms, such as Capacity Scheduler or Fair Scheduler, based on their specific requirements. These schedulers determine how resources are allocated to different applications and help ensure fair and efficient utilization of the cluster.

YARN decouples resource management from application execution, providing a flexible and scalable platform for running diverse workloads on a Hadoop cluster. It enables efficient utilization of cluster resources, improves multi-tenancy support, and supports a wide range of data processing frameworks and applications in the Hadoop ecosystem.

## YARN architecture

YARN (Yet Another Resource Manager) takes programming to the next level beyond Java , and makes it interactive to let another application Hbase, Spark etc. to work on it.Different Yarn applications can co-exist on the same cluster so MapReduce, Hbase, Spark all can run at the same time bringing great benefits for manageability and cluster utilization.

###### Components of YARN

+ Client: It submits map-reduce jobs.
+ Resource Manager: It is the master daemon of YARN and is responsible for resource assignment and management among all the applications. Whenever it receives a processing request, it forwards it to the corresponding node manager and allocates resources for the completion of the request accordingly. It has two major components: 
    - Scheduler: It performs scheduling based on the allocated application and available resources. It is a pure scheduler, means it does not perform other tasks such as monitoring or tracking and does not guarantee a restart if a task fails. The YARN scheduler supports plugins such as Capacity Scheduler and Fair Scheduler to partition the cluster resources.
    - Application manager: It is responsible for accepting the application and negotiating the first container from the resource manager. It also restarts the Application Master container if a task fails.
+ Node Manager: It take care of individual node on Hadoop cluster and manages application and workflow and that particular node. Its primary job is to keep-up with the Resource Manager. It registers with the Resource Manager and sends heartbeats with the health status of the node. It monitors resource usage, performs log management and also kills a container based on directions from the resource manager. It is also responsible for creating the container process and start it on the request of Application master.
+ Application Master: An application is a single job submitted to a framework. The application master is responsible for negotiating resources with the resource manager, tracking the status and monitoring progress of a single application. The application master requests the container from the node manager by sending a Container Launch Context(CLC) which includes everything an application needs to run. Once the application is started, it sends the health report to the resource manager from time-to-time.
+ Container: It is a collection of physical resources such as RAM, CPU cores and disk on a single node. The containers are invoked by Container Launch Context(CLC) which is a record that contains information such as environment variables, security tokens, dependencies etc.

![image](https://github.com/pritamhazra21/big-data/assets/75198912/32089ef6-50a7-4d52-9cc7-8addac4241d4)

## 8. MapReduce and YARN

MapReduce and YARN are two closely related components in the Apache Hadoop ecosystem, but they serve distinct purposes and work together to enable distributed data processing in a Hadoop cluster.

1. MapReduce: MapReduce is a programming model and framework for processing and analyzing large-scale data sets in a distributed computing environment. It provides a high-level abstraction for developers to write parallelizable code that can be executed on a cluster of machines. MapReduce breaks down the processing task into two main phases: the map phase and the reduce phase. It handles task scheduling, fault tolerance, and data distribution across the cluster. MapReduce was originally introduced by Google and is implemented in Apache Hadoop as Hadoop MapReduce.

2. YARN (Yet Another Resource Negotiator): YARN is the resource management and job scheduling framework in the Apache Hadoop ecosystem. It serves as the cluster operating system and provides a flexible and scalable platform for running various distributed applications, including MapReduce. YARN decouples the resource management functionality from the application-specific logic, allowing different application frameworks to coexist and share cluster resources efficiently. YARN consists of a Resource Manager (RM), which manages the overall resource allocation and scheduling, and Node Managers (NMs), which run on each node in the cluster and manage resources on that node. YARN allows multiple applications to run simultaneously, dynamically allocating resources based on demand.

How MapReduce and YARN work together:

When a MapReduce job is submitted to the cluster, the Resource Manager (RM) in YARN receives the job request.
- The RM negotiates resources with the job's Application Master (AM), which is responsible for managing the execution of the MapReduce job.
- The RM allocates containers (resource units) to the AM for running the mappers and reducers of the MapReduce job.
- The AM, in coordination with the RM, launches the map tasks and reduce tasks on the allocated containers.
- The map tasks and reduce tasks communicate with the Node Managers (NMs) to manage resources and report progress.
- The MapReduce job's map tasks process input data in parallel, generating intermediate key-value pairs.
- The intermediate key-value pairs are shuffled, sorted, and passed to the reduce tasks.
- The reduce tasks process the shuffled data, aggregating it and producing the final output.
- Throughout the process, YARN's Resource Manager monitors the overall progress, manages resource allocation, handles failures, and ensures efficient utilization of cluster resources.

In summary, YARN provides the resource management and scheduling capabilities necessary for running MapReduce jobs efficiently in a Hadoop cluster, while MapReduce provides the programming model and framework for processing data in parallel using the map and reduce phases.

## 9. Classic MapReduce

Classic MapReduce refers to the original implementation of the MapReduce programming model and framework, initially introduced by Google. It provided a scalable and efficient approach to process and analyze large-scale data sets in a distributed computing environment.

The key characteristics of classic MapReduce include:

1. Map and Reduce Phases: The MapReduce model divides the data processing task into two primary phases: the map phase and the reduce phase. In the map phase, input data is divided into smaller chunks, and a map function is applied to each chunk independently, generating intermediate key-value pairs. In the reduce phase, the intermediate key-value pairs are grouped, sorted, and processed to produce the final output.

2. Scalability and Fault Tolerance: Classic MapReduce is designed to handle large-scale data processing by leveraging the parallel processing capabilities of a cluster of machines. It provides scalability by distributing the data and computation across multiple nodes, allowing for efficient utilization of resources. It also offers fault tolerance by automatically handling failures and rerunning failed tasks on different nodes.

3. Data Locality: Classic MapReduce optimizes data processing by prioritizing data locality. It tries to execute map tasks on the nodes where the input data resides. This minimizes network overhead by avoiding unnecessary data transfers between nodes.

4. Shuffle and Sort: The intermediate key-value pairs generated by the map tasks are shuffled and sorted based on their keys before being passed to the reduce tasks. This ensures that all values associated with the same key are brought together, facilitating the aggregation and processing in the reduce phase.

5. Task Granularity: Classic MapReduce operates on a task-level granularity. Each map task processes a subset of the input data independently, and each reduce task handles a subset of the intermediate data associated with specific keys. This allows for efficient parallelism and load balancing.

Classic MapReduce served as the foundation for various implementations and frameworks, most notably Apache Hadoop MapReduce. While classic MapReduce has its advantages, newer frameworks like Apache Spark have introduced enhancements and optimizations to address certain limitations and provide more advanced features for big data processing.

## 10. Job scheduler

Job scheduling plays a crucial role in managing the execution of tasks and resources in a distributed computing environment. In the context of Hadoop and YARN, job scheduling refers to the process of allocating resources and determining the execution order of jobs and tasks within a cluster. Here are some key aspects of job scheduling in Hadoop:

1. Scheduling Policies: Hadoop provides pluggable scheduling policies that determine how resources are allocated among different jobs or applications. Two commonly used scheduling policies in Hadoop are:

- Capacity Scheduler: The Capacity Scheduler allows the cluster resources to be divided into multiple queues, with each queue having a defined capacity. The resources are allocated to the queues based on their configured capacities, and each queue can have its scheduling policy, such as fair sharing or FIFO.

- Fair Scheduler: The Fair Scheduler aims to provide fair sharing of resources among different applications. It allocates resources based on the demands and needs of each application, ensuring that no application is starved of resources for an extended period.

2. Resource Allocation: The scheduler determines how cluster resources, such as CPU, memory, and disk, are allocated to different tasks and applications. It takes into account factors like the resource requirements of tasks, the priority of jobs, and the availability of resources in the cluster. The scheduler aims to maximize resource utilization and minimize job completion times.

3. Task Scheduling: Within a job, the scheduler determines the order and allocation of tasks, such as map tasks and reduce tasks. It considers factors like data locality (running tasks on nodes where data resides), load balancing, and task dependencies. The scheduler strives to optimize the execution of tasks and minimize the time taken to complete a job.

4. Task Preemption: In resource-constrained scenarios, where there is competition for resources, the scheduler may employ task preemption. Preemption involves reclaiming resources from running tasks and allocating them to higher-priority tasks or jobs. This ensures that critical jobs or tasks get the necessary resources to complete in a timely manner.

5. Monitoring and Adjustment: The scheduler continuously monitors the cluster's resource usage and job progress. It adjusts resource allocations based on real-time information and workload changes to adapt to dynamic resource availability and job requirements. This helps optimize resource utilization and job performance.

Efficient job scheduling is crucial for achieving high throughput, minimizing job latencies, and ensuring fair resource sharing in a Hadoop cluster. It plays a vital role in achieving optimal performance and resource utilization across multiple concurrent jobs and tasks.

## 11. suffle and sort

Shuffle and sort are crucial steps in the MapReduce framework that facilitate data aggregation and preparation for the reduce phase. These steps involve the reorganization and grouping of intermediate key-value pairs produced by the map tasks before they are processed by the reduce tasks. Here's an explanation of shuffle and sort in MapReduce:

1. Intermediate Key-Value Pairs:
During the map phase of a MapReduce job, each map task processes a portion of the input data and generates intermediate key-value pairs. The key represents a unique identifier or category, and the value contains the associated data or information.

2. Partitioning:
The intermediate key-value pairs are partitioned based on the keys. Each key-value pair is assigned to a specific reduce task based on a partitioning function. The partitioning function ensures that key-value pairs with the same key are sent to the same reduce task, enabling the grouping of related data.

3. Shuffling:
In the shuffling phase, the map outputs from all the map tasks are transferred to the appropriate reduce tasks. This involves the movement of data over the network, as the intermediate key-value pairs need to be sent from the map tasks' locations to the respective reduce tasks. This transfer of data is a critical part of the shuffle process.

4. Sorting:
Once the intermediate key-value pairs reach the reduce tasks, they undergo a sorting process based on the keys. Sorting ensures that the key-value pairs with the same key are arranged in a specific order, such as ascending or descending. Sorting facilitates efficient grouping and processing of related data in the reduce phase.

5. Grouping:
After sorting, the sorted intermediate key-value pairs are grouped together based on the keys. All key-value pairs with the same key are brought together, forming an iterable collection that serves as the input for the reduce function. Grouping allows the reduce tasks to process all the values associated with a particular key in a single iteration.

The shuffle and sort steps are essential in the MapReduce framework as they enable the distribution, sorting, and grouping of intermediate data before it is processed by the reduce tasks. These steps optimize data aggregation and provide a consolidated view of the relevant data for each reduce task, allowing for efficient processing and aggregation of results.

## 12. task execusion

Task execution in the context of MapReduce refers to the process of executing individual tasks within a MapReduce job. MapReduce divides the processing of data into map tasks and reduce tasks, which are executed in parallel across a distributed computing environment. Here's an overview of the task execution process:

1. Map Task Execution:

- Input data splitting: The input data is divided into smaller splits, and each split is assigned to a map task. The number of map tasks is determined by the cluster configuration or user-defined settings.
- Task assignment: The Resource Manager (YARN) assigns available containers to run the map tasks. Each container represents a node in the cluster with allocated resources (CPU, memory).
- Task initialization: The assigned map tasks are launched in the allocated containers. Each map task initializes its execution environment, including loading necessary libraries and configurations.
- Map function execution: The map task applies the user-defined map function to its assigned input split. The map function processes the input records and generates intermediate key-value pairs.
- Intermediate data storage: The map task writes the generated intermediate key-value pairs to local disk or memory, usually in a sorted order based on the keys.

2. Shuffle and Sort:

- Shuffle and sort occur between the map and reduce phases and involve the movement and sorting of intermediate data across the cluster. The shuffled data is partitioned, transferred, and sorted based on the keys to ensure that all values with the same key are grouped together. This phase prepares the data for efficient processing by the reduce tasks.

3. Reduce Task Execution:

- Task assignment: After the shuffle and sort phase, reduce tasks are assigned to containers based on available resources.
Task initialization: The assigned reduce tasks are launched, initializing their execution environment.
- Reduce function execution: Each reduce task retrieves the shuffled and sorted intermediate data associated with its assigned keys. The reduce function processes the values associated with each key and produces the final output key-value pairs.
- Output storage: The output key-value pairs generated by the reduce tasks are typically written to a distributed file system, such as HDFS, in the specified output directory.

Throughout the task execution process, the cluster's resource manager (YARN) monitors task progress, manages task scheduling and resource allocation, and handles failures by rescheduling or restarting failed tasks.

Task execution in MapReduce leverages the parallel processing capabilities of a distributed computing environment, allowing for efficient processing of large-scale data sets. The parallel execution of map and reduce tasks across multiple nodes in the cluster enables the scalability and performance benefits of MapReduce.

## 13. input format output format

In the context of MapReduce, input formats and output formats define the structure and organization of data during the input and output stages of a MapReduce job. They specify how the data is read from an input source (such as files or databases) and how the results are written to an output destination. Here's an explanation of input formats and output formats in MapReduce:

Input Formats:

An input format describes the way input data is read and presented to the map tasks in a MapReduce job. It defines how the input data is divided into input splits, which are processed by individual map tasks. Some commonly used input formats include:

1. TextInputFormat: This is the default input format in MapReduce. It treats each line of input as a separate record and provides the key-value pairs where the key is the byte offset of the line and the value is the line itself.

2. KeyValueInputFormat: This input format allows for custom key-value pairs to be read from the input data. It enables flexibility in the format of input data.

3. SequenceFileInputFormat: This input format is used when the input data is in the form of a SequenceFile, which is a binary file format in Hadoop that stores key-value pairs.

Output Formats:

An output format specifies how the results of the MapReduce job are written or stored after the reduce tasks have processed the intermediate data. It defines the format in which the output data is presented or the destination to which it is written. Some commonly used output formats include:

1. TextOutputFormat: This is the default output format in MapReduce. It writes the final output of the reduce tasks as plain text, where each line represents a key-value pair.

2. KeyValueOutputFormat: This output format allows for custom key-value pairs to be written to the output data. It provides flexibility in formatting the output data.

3. SequenceFileOutputFormat: This output format is used when the output data needs to be stored in a SequenceFile format.

4. MultipleOutputs: This feature allows writing output to different files or directories based on specific criteria. It enables multiple output formats to be used within a single MapReduce job.

By specifying appropriate input and output formats, MapReduce jobs can efficiently process data in various formats and interact with different storage systems. These formats provide flexibility and customization options for handling different types of input and output data in a MapReduce workflow.

## DIfferent types of failure

In Hadoop and YARN, various types of failures can occur due to hardware issues, software errors, network problems, or other unexpected events. These failures can impact the availability, reliability, and performance of the cluster. Here are some common types of failures that can occur in Hadoop and YARN:

1. Node Failure:

- Node failures refer to the failure of individual machines (nodes) in the cluster due to hardware faults, power outages, or operating system crashes.
- When a node fails, the tasks running on that node are interrupted and need to be rescheduled on other available nodes.
- The Resource Manager (YARN) detects node failures through periodic heartbeat messages from Node Managers and takes necessary actions to recover or redistribute resources.
2. Task Failure:

- Task failures occur when individual tasks fail to complete successfully due to errors in processing, software bugs, or data corruption.
- Task failures can be caused by application-specific issues, such as programming errors or incompatible data formats.
- When a task fails, the Application Master (YARN) can retry the failed task on the same or different node, depending on the configured retry policies.
3. Application Master Failure:

- The Application Master (AM) manages the execution of a specific application or job in YARN.
- If the Application Master fails due to software errors, resource exhaustion, or other reasons, the job progress is affected.
- YARN provides mechanisms to detect AM failures and restart the AM on a different node to resume the execution of the application.
4. Resource Manager Failure:

- The Resource Manager (RM) is the central component of YARN responsible for resource allocation and job scheduling.
- If the RM fails, the cluster's resource allocation and job management capabilities are affected.
- To ensure fault tolerance, YARN supports High Availability (HA) mode where multiple RMs are configured in an active-standby setup. If the active RM fails, the standby RM takes over seamlessly to continue cluster operations.
5. Network Failure:

- Network failures can disrupt communication between components in the cluster, affecting the coordination and data transfer between nodes.
- Network failures can lead to delays, timeouts, or loss of connectivity, impacting the overall performance and reliability of the cluster.
- YARN and Hadoop have mechanisms to handle network failures, including retrying failed communications, detecting and handling timeouts, and ensuring data integrity during transmission.
6. Data Corruption:

- Data corruption can occur due to hardware faults, software bugs, or issues during data storage or transfer.
- Data corruption can lead to incorrect computation results, data loss, or job failures.
- Hadoop and YARN employ mechanisms like data replication, checksums, and fault tolerance techniques (such as HDFS block replication) to detect and recover from data corruption.

To mitigate the impact of failures, Hadoop and YARN employ fault tolerance mechanisms, such as automatic recovery, task re-execution, redundancy, and resource management strategies. These mechanisms help ensure the reliable and continuous operation of the cluster, even in the presence of failures.
