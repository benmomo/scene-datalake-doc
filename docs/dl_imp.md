# Data Lake Available implementations

## Open-source approaches

<div align="justify">
For open-source approaches, the low-level layer of <strong>data lakes</strong> was typically implemented via Hadoop Distributed File System (<strong>HDFS</strong>) for the early data lakes; modern ones use <strong>Spark</strong> for distributed computing, which is faster than (Hadoop) MapReduce with the in-memory processing. For a cloud-based approach, private implementations of data lakes are used (see next section). On top of the local approaches, and in some cases also supporting the cloud-based solutions, there are some additional (open) layers and/or projects, summarized in the Table below.
</div>
<br/>

|Solution|Description|
|---|---|
|**Apache Hadoop**|Apache Hadoop is an open-source framework for distributed storage and processing of large sets of data using a cluster of commodity hardware. It includes HDFS <br/> https://hadoop.apache.org/  
.|
|**Apache Spark**|Apache Spark is a newer open-source framework than Hadoop used for managing and processing large volumes of data for analytics. It uses in-memory caching and optimized query execution for fast analytic queries against data of any size.<br/> https://spark.apache.org/ .|
|**Apache Hive**|Apache Hive is a data warehouse infrastructure built on top of Hadoop. It provides a high-level language (HiveQL) for querying and managing large datasets stored in Hadoop files. <br/> https://hive.apache.org/  <br/> *Note: technically speaking, Apache Hive is a data warehouse, but it is common its appearance with data lakes and data lakehouses. As we are not focusing on data warehouses, we think it is worth while listing it here*|
|**Apache Hudi**|Apache Hudi (Hadoop Upserts Deletes and Incrementals) is a data lake management framework for stream processing on top of Apache Hadoop compatible storage systems, and also cloud-based approaches. It supports record-level insert, update, and delete <br/> https://hudi.apache.org/ |
|**Apache ORC (Optimized Row Columnar)** |BORC is a self-describing type-aware columnar file format designed for Hadoop workload (commonly used in Hive). RC is significantly faster than RC File or Parquet, and is being used by Facebook and Yahoo. <br/> https://orc.apache.org/ |
|**Readable file format**|If possible, it is highly recommended to use open-source formats, rather than proprietary, such as Apache Parquet or ORC (commonly used in Hadoop ecosystems). Parquet is typically better for analytical workloads and large and complex data structures. ORC is intended for write-intensive tasks and data modifications.<br/> Additionally, columnar storage makes data typically easier to read (for analytics applications). Apache Parquet and ORC are column-based standards, whereas Apache Avro is file-based (more suitable for non-regular queries and ETL pipelines) <br/>For compression mechanisms applied to data for cost reasons, it is typically better to use a ‘weak’ compression standard in order to speed up the decompression and use compute power in the real analytics. For example, Parquet supports the following compression methods: uncompressed, fast, gzip, lzo, brotli,lz4,zstd.|
|**Presto/Trino**|Presto was created at Facebook as a project and was later divided into PrestoDB and PrestoSQL. The latter one was rebranded as Trino in 2021. 
Presto (PrestSQL) is a distributed SQL query engine optimized for ad-hoc analysis. It can query data from various data sources, including Hadoop, making it a good choice for querying data in a data lake. <br/> https://prestodb.io/ <br/> https://trino.io/ |
|**Apache Iceberg**|Apache Iceberg is a table format for large, slow-moving tabular data that aims for best practices in systems like Spark, Trino, Flink, Presto, Hive and Impala <br/> https://iceberg.apache.org/ .|
|**Alluxio (Community)**|Alluxio, formerly known as Tachyon, is an open-source data orchestration layer that sits between storage systems and computational frameworks to manage data efficiently.|
|**Delta Lake**|Delta Lake is an open-source storage layer that brings ACID transactions to Apache Spark and big data workloads <br/> https://delta.io/ .|



