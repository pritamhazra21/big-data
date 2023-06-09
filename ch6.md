# Chapter 6

## Pig

Apache Pig is an open-source platform for analyzing large datasets in a distributed computing environment. It provides a high-level scripting language called Pig Latin, which allows users to express complex data transformations using a simple and concise syntax. Pig Latin scripts are then executed on Apache Hadoop, making it easy to process and analyze large volumes of data in parallel.

Here are some key features and concepts related to Apache Pig:

1. Data Flow Language: Pig Latin is a data flow language that focuses on the transformations and operations performed on the data. It abstracts the complexities of parallel processing and allows users to express their data transformations in a sequential and declarative manner.

2. Schema Discovery: Pig allows schema-on-read, meaning it infers the schema of the data at runtime. This flexibility allows you to work with data that may not have a fixed schema or changes frequently.

3. Data Processing Operations: Pig Latin provides a rich set of operators and functions to perform various data processing operations such as filtering, sorting, joining, grouping, aggregating, and more. These operations are designed to work on large-scale datasets efficiently.

4. User-Defined Functions (UDFs): Pig supports the creation of custom UDFs to extend its functionality. You can write UDFs in programming languages such as Java, Python, or JavaScript and use them within Pig Latin scripts to perform complex computations or apply custom logic.

5. Execution Modes: Pig supports different execution modes, such as local mode for testing and development on a single machine, and MapReduce mode for distributed processing on a Hadoop cluster. It can also leverage other execution engines like Apache Tez or Apache Spark for faster processing.

6. Integration with Ecosystem: Pig integrates well with the broader Apache Hadoop ecosystem. It can read and write data from various sources, including Hadoop Distributed File System (HDFS), Apache HBase, Apache Cassandra, and more. Pig can also interact with other Hadoop components like Hive and HCatalog.

Overall, Apache Pig simplifies the process of working with large-scale data by providing a higher-level language and abstracting away the complexities of distributed computing. It enables users to write expressive and reusable scripts for data processing and analysis, making it a valuable tool in big data analytics workflows.

## Grunt

In the context of Apache Pig, "Grunt" refers to the interactive shell or command-line interface provided by Pig. It allows users to interactively run Pig Latin statements and perform ad-hoc data operations.

When you launch Pig, you typically start in the Grunt shell, where you can enter Pig Latin statements, execute them, and see the results. The Grunt shell provides a prompt where you can enter commands and statements one at a time.

Here are some common tasks you can perform using the Grunt shell:

1. Loading Data: You can use commands like LOAD or REGISTER to load data from various sources, such as HDFS, local file systems, or databases, into Pig.

2. Data Transformations: Pig Latin statements for data transformations, such as filtering, sorting, joining, and aggregating, can be executed in the Grunt shell. These statements manipulate the loaded data to derive meaningful insights.

3. Storing Results: After processing the data, you can use commands like STORE or DUMP to save or display the results respectively. The results can be stored back to HDFS, local file systems, or other supported storage systems.

4. Diagnostic Commands: The Grunt shell provides additional commands for diagnostic purposes, such as DESCRIBE to display the schema of a relation, EXPLAIN to understand the execution plan of a Pig Latin statement, and ILLUSTRATE to visualize the data flow.

5. Macros and UDFs: Grunt also allows you to define macros (reusable code snippets) and register user-defined functions (UDFs) that can be used in Pig Latin statements to extend the functionality of Pig.

Overall, the Grunt shell provides an interactive environment for developing and testing Pig Latin scripts, allowing you to experiment with different data transformations and quickly iterate on your analysis. It provides immediate feedback and results, making it convenient for exploratory data analysis and ad-hoc queries.

## Pig data model

The data model in Apache Pig is based on a structured, schema-less, and self-describing format. Pig treats data as a collection of tuples, where each tuple is an ordered set of fields. The fields can be of any data type supported by Pig, such as integers, strings, floating-point numbers, or complex types like bags, maps, and tuples.

Here are the key components of the Pig data model:

1. Tuple: A tuple is an ordered set of fields enclosed in parentheses. It is analogous to a row in a table. Each field within a tuple is identified by its position or index, starting from 0.

Example:
```
(John, Doe, 25)
```

2. Field: A field is a single value within a tuple. It can be of any Pig data type, such as int, float, chararray (string), bytearray, bag, map, or tuple.

Example:
```
(John, Doe, 25)
   ^    ^    ^
   0    1    2
```

3. Bag: A bag is an unordered collection of tuples. It is analogous to a set or a bag in mathematics. A bag can contain tuples of different schemas, and it allows duplicate tuples.

Example:
```
{(John, Doe, 25), (Jane, Smith, 30)}
```

4. Map: A map is an associative array that stores key-value pairs. The keys are unique within a map, and each key is associated with a value. Both keys and values can be of any Pig data type.

Example:
```
['name'#'John', 'age'#25]
```

5. Nested Types: Pig supports nesting of complex types within tuples, bags, and maps. This means you can have fields that are bags, maps, or tuples themselves, allowing for hierarchical and structured data representation.

Example:
```
(John, {(English, 90), (Math, 80)})
```

The schema of the data is not explicitly defined in Pig. Instead, Pig follows a schema-on-read approach, where the structure of the data is determined at runtime when the data is loaded. This flexibility allows Pig to handle semi-structured or schema-less data sources effectively.

Pig's data model provides a flexible and dynamic way to handle different data structures and types, making it suitable for processing diverse datasets.

## Pig Latin

Pig Latin is a high-level scripting language specifically designed for data analysis and processing in Apache Pig. It provides a simplified and expressive syntax to perform complex transformations on large datasets. Pig Latin scripts are executed using Apache Pig, which translates the Pig Latin statements into a series of MapReduce or other execution engine tasks.

Here are some key features and concepts of Pig Latin:

1. Data Loading: Pig Latin allows you to load data from various sources such as HDFS, local file systems, or databases. You can use the `LOAD` statement to specify the data source, format, and location.

Example:
```
data = LOAD 'hdfs://data/input' USING PigStorage(',') AS (name: chararray, age: int);
```

2. Data Transformation: Pig Latin provides a rich set of operators to transform and manipulate data. You can use operators like `FILTER`, `GROUP`, `JOIN`, `FOREACH`, and many more to perform operations like filtering records, grouping data, joining datasets, and applying transformations to individual fields.

Example:
```
filtered_data = FILTER data BY age > 18;
```

3. Schema Projection: Pig Latin allows you to project only the required fields from the loaded data or intermediate results. This can help optimize performance and reduce the amount of data processed.

Example:
```
projected_data = FOREACH data GENERATE name, age;
```

4. User-Defined Functions (UDFs): Pig Latin supports the use of custom functions written in programming languages like Java, Python, or JavaScript. UDFs allow you to define and apply custom logic or computations on your data.

Example:
```
REGISTER 'myudfs.jar';
data = FOREACH data GENERATE myudfs.myFunction(name);
```

5. Storing Results: After processing the data, you can use the `STORE` statement to write the results to a specified location or storage system.

Example:
```
STORE filtered_data INTO 'hdfs://data/output';
```

6. Iterative Processing: Pig Latin also supports iterative processing using the `ITERATE` and `UNTIL` statements. This allows you to perform iterative computations on your data until a certain condition is met.

Example:
```
result = ITERATE input_data
         GENERATE Transform(input_data) AS transformed_data;
```

Pig Latin provides a concise and declarative syntax for expressing complex data transformations and analyses. It abstracts the complexities of distributed processing and allows users to focus on the data transformations rather than the underlying execution framework.
## Devoloping and testing

When developing and testing Pig Latin scripts, you can follow these steps to ensure smooth execution and accurate results:

1. Set up the Environment:

- Install Apache Pig on your system and set up the necessary configurations.
- Ensure that you have a compatible version of Apache Hadoop installed if you plan to run Pig in distributed mode.
2. Write Pig Latin Scripts:

- Create a new file with a ".pig" extension, e.g., "script.pig".
- Open the file in a text editor or an integrated development environment (IDE) with Pig Latin syntax highlighting support.
- Start writing your Pig Latin statements in the file, following the syntax and structure of Pig Latin.
3. Load Data:

- Use the LOAD statement to load your data into Pig from various sources such as HDFS, local file systems, or databases.
- Specify the data format, location, and any required schema or field mappings.
4. Perform Data Transformations:

- Use Pig Latin operators and functions to perform the desired data transformations, such as filtering, grouping, joining, and aggregating.
- Chain multiple operators together to create complex data pipelines.
5. Store or Display Results:

- Use the STORE statement to write the transformed data to an output location or storage system.
- Alternatively, use the DUMP statement to display the results on the console for testing and debugging purposes.
6. Debugging and Iterative Development:

- Use the DESCRIBE statement to check the schema of relations at different stages in your script.
- Use the EXPLAIN statement to understand the execution plan of your Pig Latin script.
- Leverage the ILLUSTRATE statement to visualize the data flow and intermediate results.
7. Test and Validate:

- Run your Pig Latin script using the Pig command-line interface or by submitting it to a Pig cluster.
- Monitor the execution progress and check for any error messages or warnings.
- Inspect the output data or results to ensure they match your expectations.
- Iterate and modify your script as needed based on the results and feedback.
8. Use Parameterization:

- Parameterize your Pig Latin script to make it more flexible and reusable.
- Define parameters at the beginning of your script and refer to them throughout the script.
- This allows you to easily change input sources, output locations, or other settings without modifying the script itself.
9. Use Sample or Subset Data:

- During development and testing, it can be beneficial to work with a smaller sample or subset of your data to speed up execution and quickly validate results.
- Use the LIMIT or SAMPLE operators to limit the number of records or randomly sample a subset of your data.
10. Handle Errors and Exceptions:

- Ensure that your script includes error handling mechanisms for scenarios like missing data, incorrect data types, or unexpected conditions.
- Use the FILTER operator to remove invalid or erroneous data from your dataset.
- Leverage the power of Pig's error handling and exception mechanisms to gracefully handle issues and failures.

By following these steps, you can develop and test your Pig Latin scripts effectively, iterate on your data transformations, and ensure the accuracy and efficiency of your data processing pipelines.

## Pig architecture

The language used to analyze data in Hadoop using Pig is known as Pig Latin. It is a highlevel data processing language which provides a rich set of data types and operators to perform various operations on the data.

To perform a particular task Programmers using Pig, programmers need to write a Pig script using the Pig Latin language, and execute them using any of the execution mechanisms (Grunt Shell, UDFs, Embedded). After execution, these scripts will go through a series of transformations applied by the Pig Framework, to produce the desired output.

Internally, Apache Pig converts these scripts into a series of MapReduce jobs, and thus, it makes the programmer’s job easy. The architecture of Apache Pig is shown below.

![image](https://github.com/pritamhazra21/big-data/assets/75198912/efa03f14-6ad4-47ad-a6ce-668b4b7c2555)

Apache Pig Components

As shown in the figure, there are various components in the Apache Pig framework. Let us take a look at the major components.

**Parser**

Initially the Pig Scripts are handled by the Parser. It checks the syntax of the script, does type checking, and other miscellaneous checks. The output of the parser will be a DAG (directed acyclic graph), which represents the Pig Latin statements and logical operators.

In the DAG, the logical operators of the script are represented as the nodes and the data flows are represented as edges.

**Optimizer**

The logical plan (DAG) is passed to the logical optimizer, which carries out the logical optimizations such as projection and pushdown.

**Compiler**

The compiler compiles the optimized logical plan into a series of MapReduce jobs.

**Execution engine**

Finally the MapReduce jobs are submitted to Hadoop in a sorted order. Finally, these MapReduce jobs are executed on Hadoop producing the desired results.

## Hive

Hive is an open-source data warehouse infrastructure built on top of Apache Hadoop. It provides a high-level SQL-like language called HiveQL (Hive Query Language) that allows users to query and analyze large datasets stored in Hadoop Distributed File System (HDFS) or other compatible storage systems.

Here are some key features and concepts related to Hive:

1. Schema-on-Read: Hive follows a schema-on-read approach, which means that the structure and schema of the data are determined at the time of reading the data rather than when it is stored. This flexibility allows Hive to work with diverse and evolving data sources.

2. Metastore: Hive uses a metastore to store metadata about the tables, partitions, columns, and other information related to the data stored in Hive. The metastore can be backed by various databases like MySQL, PostgreSQL, or Derby.

3. HiveQL: HiveQL is a SQL-like query language that provides a familiar syntax for data querying and analysis. It supports a wide range of SQL operations like SELECT, JOIN, GROUP BY, ORDER BY, and functions to perform aggregations, transformations, and filtering on the data.

4. Tables and Partitions: Hive organizes data into tables, which are similar to database tables. Tables can be partitioned based on one or more columns, allowing for efficient querying and data organization. Partitioning enables faster data retrieval by pruning unnecessary partitions during query execution.

5. Storage Formats: Hive supports various storage formats, including plain text, CSV, Avro, Parquet, ORC (Optimized Row Columnar), and more. Different storage formats offer different trade-offs between storage efficiency, query performance, and compatibility with other tools in the Hadoop ecosystem.

6. User-Defined Functions (UDFs): Hive allows users to define and use custom User-Defined Functions (UDFs) in different programming languages like Java, Python, or Scala. UDFs extend the functionality of Hive by allowing users to perform custom computations or apply complex logic during data processing.

7. Data Integration: Hive integrates well with other components in the Hadoop ecosystem. It can seamlessly interact with HDFS, Apache HBase, Apache Kafka, and other data sources. Hive also provides integration with Apache Spark, enabling the use of Spark as an execution engine for Hive queries.

8. Hive Server: Hive provides a Hive Server that enables clients to submit Hive queries remotely. It supports various client interfaces like JDBC, ODBC, and a command-line interface (CLI) for interacting with Hive and executing queries.

Hive provides a SQL-like interface and an SQL-like language to query and analyze large datasets stored in Hadoop. It abstracts the complexities of distributed computing and allows users to leverage their SQL skills to perform data analysis on big data platforms.

## Hive data type and file formats

Hive supports a variety of data types and file formats for storing and processing data. Here are the commonly used data types and file formats in Hive:

**Data Types:**

1. Primitive Data Types:

- BOOLEAN: Represents a boolean value (true or false).
- TINYINT: 1-byte signed integer.
- SMALLINT: 2-byte signed integer.
- INT: 4-byte signed integer.
- BIGINT: 8-byte signed integer.
- FLOAT: Single-precision floating-point number.
- DOUBLE: Double-precision floating-point number.
- STRING: Variable-length character string.
- CHAR: Fixed-length character string.
- VARCHAR: Variable-length character string with a maximum length.
- TIMESTAMP: Represents a particular point in time.
- DATE: Represents a date (year, month, day).
- BINARY: Arbitrary-length binary data.
- DECIMAL: Fixed-point decimal number.
2. Complex Data Types:

- ARRAY: Ordered collection of elements of the same type.
- MAP: Collection of key-value pairs, where keys and values can have different data types.
- STRUCT: Collection of named fields, each with its own data type.
- UNION: A special type that can hold values of different data types.

**File Formats:**

1. Text File Format:

- Delimited Text: Plain text files with fields separated by a specified delimiter, such as commas (CSV), tabs (TSV), or custom delimiters.
- Regex Text: Text files with fields parsed using regular expressions to extract structured data.
2. SequenceFile: A binary file format that allows efficient serialization and storage of key-value pairs. It is a common format for intermediate data in Hadoop.

3. Avro: A row-based data serialization system that provides rich data structures, dynamic typing, and schema evolution. Avro files are self-describing and support efficient data compression.

4. Parquet: A columnar storage file format optimized for query performance and compression. It provides efficient columnar encoding, predicate pushdown, and support for nested data structures.

5. ORC (Optimized Row Columnar): A columnar file format designed for high-performance analytics workloads. It offers advanced compression techniques, predicate pushdown, and support for ACID transactions.

6. RCFile (Record Columnar File): A columnar storage format that combines the benefits of both row-based and columnar storage. It provides efficient compression and supports predicate pushdown.

7. JSON: A lightweight data interchange format that represents data in a human-readable text format.

8. XML: XML files that store data in a hierarchical structure using tags and elements.

9. Apache HBase: Hive can also interact with Apache HBase, a NoSQL database built on top of Hadoop, using HBase storage handlers.

Hive supports additional file formats and can also work with custom file formats by defining custom input/output formats and SerDe (Serializer/Deserializer) libraries.

The choice of data types and file formats in Hive depends on factors such as the nature of the data, query patterns, performance requirements, and integration with other tools and systems in the Hadoop ecosystem.

## Hive data defination

In HiveQL (Hive Query Language), you can define and manipulate data structures using Data Definition Language (DDL) statements. HiveQL provides several DDL statements to create, alter, and drop tables, databases, and partitions. Here are the commonly used DDL statements in HiveQL for data definition:

1. Create Database:
   - The `CREATE DATABASE` statement is used to create a new database in Hive.

   Syntax:
   ```sql
   CREATE DATABASE [IF NOT EXISTS] database_name
   [COMMENT 'database_comment']
   [LOCATION 'hdfs_directory']
   [WITH DBPROPERTIES (property_name=property_value, ...)];
   ```

2. Create Table:
   - The `CREATE TABLE` statement is used to create a new table in Hive.

   Syntax:
   ```sql
   CREATE [EXTERNAL] TABLE [IF NOT EXISTS] [database_name.]table_name
   [(col_name data_type [COMMENT col_comment], ...)]
   [COMMENT 'table_comment']
   [PARTITIONED BY (col_name data_type [COMMENT col_comment], ...)]
   [CLUSTERED BY (col_name, col_name, ...) [SORTED BY (col_name [ASC|DESC], ...)] INTO num_buckets BUCKETS]
   [ROW FORMAT row_format]
   [STORED AS file_format]
   [LOCATION 'hdfs_directory']
   [TBLPROPERTIES (property_name=property_value, ...)];
   ```

3. Alter Table:
   - The `ALTER TABLE` statement is used to modify the structure or properties of an existing table.

   Syntax:
   ```sql
   ALTER TABLE [database_name.]table_name
   ADD COLUMNS (col_name data_type [COMMENT col_comment], ...);
   ALTER TABLE [database_name.]table_name
   RENAME TO new_table_name;
   ALTER TABLE [database_name.]table_name
   SET TBLPROPERTIES (property_name=property_value, ...);
   ```

4. Drop Table:
   - The `DROP TABLE` statement is used to remove an existing table from Hive.

   Syntax:
   ```sql
   DROP TABLE [IF EXISTS] [database_name.]table_name;
   ```

5. Create Partition:
   - The `ALTER TABLE ... ADD PARTITION` statement is used to add a new partition to a partitioned table.

   Syntax:
   ```sql
   ALTER TABLE [database_name.]table_name
   ADD PARTITION (partition_spec)
   [LOCATION 'hdfs_directory'];
   ```

6. Drop Partition:
   - The `ALTER TABLE ... DROP PARTITION` statement is used to remove a partition from a partitioned table.

   Syntax:
   ```sql
   ALTER TABLE [database_name.]table_name
   DROP PARTITION (partition_spec);
   ```

7. Truncate Table:
   - The `TRUNCATE TABLE` statement is used to remove all data from an existing table, while keeping the table structure intact.

   Syntax:
   ```sql
   TRUNCATE TABLE [database_name.]table_name;
   ```

These DDL statements provide the necessary tools to define and manipulate tables, databases, partitions, and their properties in Hive. They allow you to create and manage the data structures needed for data storage and querying in Hive.
## HiveQL data manipulation

In HiveQL (Hive Query Language), you can manipulate data using Data Manipulation Language (DML) statements. HiveQL provides several DML statements to insert, update, delete, and query data in Hive tables. Here are the commonly used DML statements in HiveQL for data manipulation:

1. Insert into Table:
   - The `INSERT INTO` statement is used to insert data into a table.

   Syntax:
   ```sql
   INSERT INTO [TABLE] [database_name.]table_name [PARTITION (partition_spec)]
   [VALUES (value_expr, ...), ...]
   [SELECT ...]
   ```

2. Update Table:
   - Hive does not support direct updates to existing records. Instead, you can use the `INSERT INTO ... SELECT` statement with appropriate logic to create a new table with updated data.

   Syntax:
   ```sql
   INSERT INTO [TABLE] [database_name.]new_table_name [PARTITION (partition_spec)]
   SELECT ...
   ```

3. Delete from Table:
   - Hive does not support direct deletion of individual records. Instead, you can use the `INSERT INTO ... SELECT` statement with appropriate logic to create a new table excluding the records you want to delete.

   Syntax:
   ```sql
   INSERT INTO [TABLE] [database_name.]new_table_name [PARTITION (partition_spec)]
   SELECT ...
   ```

4. Select from Table:
   - The `SELECT` statement is used to query data from one or more tables.

   Syntax:
   ```sql
   SELECT [ALL | DISTINCT] select_expr [, select_expr, ...]
   FROM [database_name.]table_name
   [WHERE condition]
   [GROUP BY col_name [, col_name, ...]]
   [HAVING condition]
   [ORDER BY col_name [ASC | DESC] [, col_name [ASC | DESC], ...]]
   [LIMIT n]
   ```

5. Join Tables:
   - Hive supports different types of joins such as INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN, etc., to combine data from multiple tables.

   Syntax:
   ```sql
   SELECT ...
   FROM table_name1
   [INNER | LEFT | RIGHT [OUTER] | FULL [OUTER]] JOIN table_name2
   ON table_name1.col_name = table_name2.col_name
   ```

6. Union Tables:
   - The `UNION` statement is used to combine the result sets of multiple SELECT statements into a single result set.

   Syntax:
   ```sql
   SELECT ...
   FROM table_name1
   UNION [ALL]
   SELECT ...
   FROM table_name2
   ```

7. Aggregation Functions:
   - Hive provides various built-in aggregation functions such as SUM, AVG, MIN, MAX, COUNT, etc., to perform calculations on groups of data.

   Syntax:
   ```sql
   SELECT aggregation_function(column_name)
   FROM table_name
   [GROUP BY column_name]
   ```

8. Subqueries:
   - Hive supports subqueries, allowing you to use the result of one query as input for another query.

   Syntax:
   ```sql
   SELECT ...
   FROM table_name
   WHERE column_name IN (SELECT column_name FROM another_table)
   ```

These DML statements provide the necessary tools to manipulate and query data in Hive tables. They allow you to insert, update, delete, and retrieve data from tables using various filtering, aggregation, and joining techniques.
## HiveQL queries

HiveQL (Hive Query Language) is a SQL-like language that allows you to query and analyze data stored in Hive tables. HiveQL supports a wide range of SQL operations and provides additional features specific to the Hadoop ecosystem. Here are some examples of common HiveQL queries:

1. Select All Columns from a Table:
   ```sql
   SELECT * FROM table_name;
   ```

2. Select Specific Columns from a Table:
   ```sql
   SELECT column1, column2, ... FROM table_name;
   ```

3. Filter Rows with WHERE Clause:
   ```sql
   SELECT * FROM table_name WHERE condition;
   ```

4. Aggregation Queries:
   - Sum of a Column:
     ```sql
     SELECT SUM(column_name) FROM table_name;
     ```

   - Average of a Column:
     ```sql
     SELECT AVG(column_name) FROM table_name;
     ```

   - Count of Rows:
     ```sql
     SELECT COUNT(*) FROM table_name;
     ```

5. Grouping and Aggregation:
   ```sql
   SELECT column1, COUNT(column2) FROM table_name GROUP BY column1;
   ```

6. Sorting Rows:
   ```sql
   SELECT * FROM table_name ORDER BY column_name [ASC|DESC];
   ```

7. Joining Tables:
   ```sql
   SELECT * FROM table1 JOIN table2 ON table1.column_name = table2.column_name;
   ```

8. Subqueries:
   ```sql
   SELECT * FROM table1 WHERE column_name IN (SELECT column_name FROM table2 WHERE condition);
   ```

9. Using Built-in Functions:
   ```sql
   SELECT column1, FUNCTION(column2) FROM table_name;
   ```

10. Conditional Statements with CASE:
    ```sql
    SELECT column1, CASE WHEN condition THEN value1 ELSE value2 END FROM table_name;
    ```

11. Limiting Results:
    ```sql
    SELECT * FROM table_name LIMIT n;
    ```

12. Create a New Table from Query Results:
    ```sql
    CREATE TABLE new_table_name AS SELECT * FROM table_name;
    ```

These are just a few examples of HiveQL queries. HiveQL provides a rich set of SQL-like operations and functions to manipulate and analyze data in Hive tables. The queries can be customized and combined to suit specific data analysis and reporting requirements.
