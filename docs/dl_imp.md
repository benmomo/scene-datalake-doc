# Data Lake Available implementations

## Open-source approaches

<div align="justify">
For open-source approaches, the low-level layer of <strong>data lakes</strong> was typically implemented via Hadoop Distributed File System (<strong>HDFS</strong>) for the early data lakes; modern ones use <strong>Spark</strong> for distributed computing, which is faster than (Hadoop) MapReduce with the in-memory processing. For a cloud-based approach, private implementations of data lakes are used (see next section). On top of the local approaches, and in some cases also supporting the cloud-based solutions, there are some additional (open) layers and/or projects, summarized in the Table below.
</div>
<br/>

|Solution|Description|
|---|---|
|**Apache Hadoop**|Apache Hadoop is an open-source framework for distributed storage and processing of large sets of data using a cluster of commodity hardware. It includes HDFS <br/> [https://hadoop.apache.org/](https://hadoop.apache.org/) .|
|**Apache Spark**|Apache Spark is a newer open-source framework than Hadoop used for managing and processing large volumes of data for analytics. It uses in-memory caching and optimized query execution for fast analytic queries against data of any size.<br/>[https://spark.apache.org/](https://spark.apache.org/) .|
|**Apache Hive**|Apache Hive is a data warehouse infrastructure built on top of Hadoop. It provides a high-level language (HiveQL) for querying and managing large datasets stored in Hadoop files. <br/>[https://hive.apache.org/](https://hive.apache.org/)  <br/> *Note: technically speaking, Apache Hive is a data warehouse, but it is common its appearance with data lakes and data lakehouses. As we are not focusing on data warehouses, we think it is worth while listing it here*|
|**Apache Hudi**|Apache Hudi (Hadoop Upserts Deletes and Incrementals) is a data lake management framework for stream processing on top of Apache Hadoop compatible storage systems, and also cloud-based approaches. It supports record-level insert, update, and delete <br/>[https://hudi.apache.org/](https://hudi.apache.org/) |
|**Apache ORC (Optimized Row Columnar)** |ORC is a self-describing type-aware columnar file format designed for Hadoop workload (commonly used in Hive). RC is significantly faster than RC File or Parquet, and is being used by Facebook and Yahoo. <br/>[https://orc.apache.org/](https://orc.apache.org/) |
|**Presto/Trino**|Presto was created at Facebook as a project and was later divided into PrestoDB and PrestoSQL. The latter one was rebranded as Trino in 2021. Presto (PrestSQL) is a distributed SQL query engine optimized for ad-hoc analysis. It can query data from various data sources, including Hadoop, making it a good choice for querying data in a data lake. <br/>[https://prestodb.io/](https://prestodb.io/) <br/>[https://trino.io/](https://trino.io/) |
|**Apache Iceberg**|Apache Iceberg is a table format for large, slow-moving tabular data that aims for best practices in systems like Spark, Trino, Flink, Presto, Hive and Impala <br/>[https://iceberg.apache.org/](https://iceberg.apache.org/) .|
|**Alluxio (Community)**|Alluxio, formerly known as Tachyon, is an open-source data orchestration layer that sits between storage systems and computational frameworks to manage data efficiently.|
|**Delta Lake**|Delta Lake is an open-source storage layer that brings ACID transactions to Apache Spark and big data workloads <br/>[https://delta.io/](https://delta.io/) .|


<div align="justify">
As for the data governance layer in data lakes, it is probably one of the most challenging aspects in terms of available open-source implementations. Though there are open-source <strong>data catalogs</strong> for an effective data management, they are not natively integrated in any of the data lakes and are offered as independent modules. We were able to find only one data governance module specifically developed for a data lake called <a href="https://cdn.hpccsystems.com/whitepapers/wp_data_lake_curation_and_governance_with_tombolo.pdf">Tombolo</a>; however, it is not generic but created by HPCC for their own data lake.
A data catalog (in a general context and not specifically related to data lakes) offers <strong>metadata management, data discovery and governance capabilities</strong>, allowing users to search for data assets, their context and lineage. Some of the most common data catalogs are briefly described in the Table below.
</div>
<br/>

## Cloud based approaches

<div align="justify">
This section briefly summarizes the available approaches for the most common cloud providers related to data lakes (Google, IBM, Amazon and Microsoft).
<br/>
Data lakes in <strong>Google Cloud</strong> are typically offered as a suite with other services (summary table below).
</div>
<br/>

|Concept|Description|
|---|---|
|**DataFlow**|Unified stream and batch data processing that's serverless, fast, and cost-effective <br/> [https://cloud.google.com/dataflow/](https://cloud.google.com/dataflow/) .|
|**Cloud Data Fusion**|Fully managed, cloud-native data integration at any scale to build ETL/ELT pipelines.<br/>[https://cloud.google.com/data-fusion](https://cloud.google.com/data-fusion) .|
|**BigQuery**|Serverless, highly scalable and cost-effective enterprise data warehouse designed for business agility (built-in ML/AI and BI for insights). <br/>[https://cloud.google.com/bigquery/](https://cloud.google.com/bigquery/)|
|**Dataproc**|Fully managed and highly scalable service for running Apache Hadoop, Apache Spark, Apache Flink, Presto, and 30+ open source tools and frameworks <br/>[https://cloud.google.com/dataproc/?hl=en](https://cloud.google.com/dataproc/?hl=en) |
|**Cloud storage** |Globally, unified, scalable and durable object reference service for storing unstructured data. <br/>[https://cloud.google.com/storage/](https://cloud.google.com/storage) |

<div align="justify">
It is important to note that cloud providers offer a wide variety of different services and tools, which may relate to each other, and listing all of them is beyond the scope of this document. For Google, one can find a useful description through its <a href="https://cloud.google.com/docs?hl=en">Google cloud documentation</a>. From the point of view of data lakes and related tools, the most common services and tools are depicted in the Figure below. For some data lake design patterns on Google (full stack, unified batch/streaming model, lambda streaming) the reader can check <a href="https://www.unifieddatascience.com/data-lake-design-patterns-on-google-cloud">here</a>.
</div>
<br/>

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_imp_google_1.jpg?raw=true" alt="Google related products fro data lakes" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" />

<br/>


<div align="justify">
Data lakes by <strong>IBM</strong> are offered within the watsonx family of products (AI and data platform)
</div>
<br/>

|Concept|Description|
|---|---|
|**Watsonx.ai studio**|New foundational models, generative AI and machine learning <br/> [https://www.ibm.com/products/watsonx-ai](https://www.ibm.com/products/watsonx-ai) .|
|**Watsonx.data**|Fit-for-purpose data store, built on an open lakehouse architecture.<br/>[https://www.ibm.com/products/watsonx-data](https://www.ibm.com/products/watsonx-data) .|
|**Watsonx.governance toolkit**|Accelerate AI workflows built with responsibility, transparency and explainability <br/>[https://www.ibm.com/products/watsonx-governance](https://www.ibm.com/products/watsonx-governance) |


<div align="justify">
The general process is depicted in the Figure below (source:IBM) for a base solution, but depending on the application scope (Big Data, Logging, IoT) it may differ slightly. For example, in a Big Data application, all data is ingested into IBM Cloud Object Storage (step 1- grey circle in the middle of the Figure), a service able to store huge amounts of data. Afterwards, the IBM Analytics Engine provides deployment of Hadoop and Spark to analyse the data (step 2). Finally, the Watson Data Science Workbench is used to analyse the data, build AI models, provide insights and dashboards (step 3).
</div>
<br/>

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_imp_ibm_1.jpg?raw=true" alt="IBM cloud architecture. Source : IBM" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" />

<div align="justify">
The vision of IBM is quite flexible and can coexist and integrate with other platforms, such as AWS, as depicted in the Figure below (source:IBM). It is an attempt to align and support hybrid environments (public, private and edge environments).  IBM promotes the use of data lakehouses, as a combination of advantages from data warehouses and data lakes, even in hybrid-cloud scenarios
</div>
<br/>

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_imp_ibm_2.jpg?raw=true" alt="IBM cloud architecture. Source : IBM" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" />

<br/>

<div align="justify">
Data lakes by <strong>AWS</strong> are offered as a set of services combining data storage and analytics solutions.
</div>
<br/>

|Concept|Description|
|---|---|
|**AWS Lambda**|Compute service to run code in an automated self-managed environment (servers, clusters), for serverless applications <br/> [https://aws.amazon.com/lambda/](https://aws.amazon.com/lambda/)|
|**Amazon OpenSearch Service**|Provides robust search (and analytics) capabilities (log files, messages, metrics, config info, documents) , including built-in OpenSearch dashboards and Kibana <br/>[https://aws.amazon.com/opensearch-service/](https://aws.amazon.com/opensearch-service/)|
|**Amazon Cognito**|User authentication and access control <br/>[https://aws.amazon.com/cognito/](https://aws.amazon.com/cognito/) |
|**AWS Glue**|Serverless service for data transformation (discovery, preparation, integration) that allows building and monitoring ETL pipelines for data lakes <br/> [https://aws.amazon.com/glue/](https://aws.amazon.com/glue/)|
|**Amazon Athena**|Serverless analytics service able to analyse huge amounts of data (built on open-source Trino and Apache Spark) <br/>[https://aws.amazon.com/athena/](https://aws.amazon.com/athena/)|
|**Amazon S3**|Simple Storage Service to store and protect data for various use cases (data lakes, back-up, low-cost archiving, etc.) <br/>[https://aws.amazon.com/s3/](https://aws.amazon.com/s3/) |
|**Amazon DynamoDB**|Serverless, NoSQL, fully managed database <br/>[https://aws.amazon.com/dynamodb/](https://aws.amazon.com/dynamodb/) |

<div align="justify">
Although the basic and nuclear core of the data lake is Amazon S3, a bunch of additional services are usually employed by AWS users to facilitate their work in tagging, searching, sharing, transforming and analysing the data. Siemens use AWS services to build what they call <a href="https://youtu.be/C0T5xEWQz3g?si=Ih3TPHFfDFCLhEOk">Data Lake 2 Go</a>. Toyota is another AWS client through its <a href="https://aws.amazon.com/blogs/big-data/enhancing-customer-safety-by-leveraging-the-scalable-secure-and-cost-optimized-toyota-connected-data-lake/">Connected Data Lake </a>
A simple example of data lakes on AWS is provided in the Figure below, which also includes an <a href="https://github.com/aws-solutions/aws-data-lake-solution">example code in GitHub</a>
</div>
<br/>

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_imp_aws_1.jpg?raw=true" alt="IBM cloud architecture. Source : IBM" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" />
