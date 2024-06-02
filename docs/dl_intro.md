# Data Lake Introduction

<div align="justify">
In the rapidly evolving landscape of data management, a common challenge emerges: the proliferation of diverse and sometimes <strong>overlapping terminology</strong>. As organizations strive to harness the <strong>power of data</strong> for informed decision-making, they encounter a large set of terms like <strong>data lake, data warehouse, data mart, data fabric, data lake house</strong>, and many more. <br/>
These terms often represent distinct concepts, but their boundaries can blur, causing <strong>confusion</strong> and miscommunication among data professionals and stakeholders. Hence, a comprehensive reference terminology seems sensible to not only define these concepts but also establish clear boundaries and relationships among them. A summary reference table is provided in the Table below. 
</div>
<br/>

|Concept|Description|
|---|---|
|**Data Lake** |- Central and reliable repository to store and process large amounts of data, which can be structured (relational databases), semi-structured (CSV, JSON), unstructured (documents, e-mails) or **binary** (images, audio, video). It is able to store data in its **native format** and process multiple data types;<br/><br/> - Can be deployed on premises or in the cloud (e.g. Amazon, Microsoft, Google); - Intended for **general analysis** and **reports** from raw/massive data (**data scientists** using AI techniques and languages such as SQL, Python, R); - Simple architecture (James Dixon): Hadoop File System (**HDFS**) with lots of folders/files;<br/><br/> - Media and entertainment sector typically uses data lakes to improve its recommendation system;<br/><br/> - **Pros**: High availability, fast access and processing, relatively cheap (cost/size);<br/><br/> - **Cons**: Limited quality and data governance.|
|**Data Warehouse** |- Data repository for **filtered** (processed) and **structured** data with a **specific** purpose;<br/><br/> -	Typical target users are **business**-oriented people (**decision-making**);<br/><br/> -	Serves as **single source of truth** for a company across multiple knowledge domains;<br/><br/> - Source data (transactional systems, relational DBs) are converted from raw to high-quality data via **ETL** (Extract, Transform and Load) tools;<br/><br/> - Changes are **less flexible** and **less typical** than for data lakes;<br/><br/> -	**Pros**: data already processed saving disk size, data useful for non-technical, high-performance for queries, governance model more robust (compared to data lake);<br/><br/> - **Cons**: cost (compared to data lake), none to very limited support to unstructured data, delay until ‘fresh’ processed data arrives (limitation for RT).|
|**Data Mart** |- **Subset** of Data warehouse more specific to a **particular domain** (e.g., finance).|
|**Data Lakehouse** |- Combines the best from Data Lakes and Data Warehouse: (i) flexibility and cost-effectiveness from a Data Lake, and (ii) performance and structure of a DW;<br/><br/>- Open data formats: Apache **Parquet**, Apache **Avro**;<br/><br/>- Open table format for analytic datasets (metadata layer): Apache Iceberg, providing SQL interface;<br/><br/>- Support for different engines (Spark, Trino, Flink, Presto, Hive, etc.).|
|**Data fabric** |- **Unified** and **integrated** approach to data management and access across an organization;<br/><br/>- It **unifies data from various sources**, such as databases, data lakes, cloud platforms, and streaming data, into a single, cohesive view;- It emphasizes **data integration**, transformation, and harmonization to ensure data consistency and quality;<br/><br/>- It includes features for **data governance**, security, and compliance, ensuring that data is managed in a controlled and secure manner;<br/><br/>- It often involves the creation of an **abstraction layer** that hides the underlying complexity of data storage and retrieval, making it easier for users to access and work with data.|
|**Data mesh** |- **Architectural** and **organizational** approach to data management;<br/><br/>- **Data** is treated **as a Product**, which are broken down into data silos. Six main features: discoverable, addressable, self-describing, trustworthy, secure, interoperable;<br/><br/>- The responsibility for data is **decentralized** and is given to different teams or domains, each one in charge of their own (data) products for the **end-to-end data lifecycle** (collection, storage, quality and access);<br/><br/>- It typically includes a **Data Catalog** that helps users discover and access data products from various domains;<br/><br/>- It **scales horizontally** by adding more domain-specific teams;<br/><br/>- Requires **skilled data professionals** and **significant investment**;<br/><br/>- **Four pillars**: Domain Oriented decentralization, Data as a Product, Self-serve data infrastructure as a platform, Federated Computational Governance;<br/><br/>- **No standard definition** of a data mesh;<br/><br/>- **Difficult** to see the big picture for **combining data**;<br/><br/>- Some **implementations** by companies (Intuit, Adevinta, HelloFresh, etc.).|
|**Database** |- **Structured collection** of data organized and stored in a computer system;<br/><br/>- Designed to **efficiently manage** and **manipulate** large volumes of data;<br/><br/>- **Ensures data integrity** and **consistency** through internal rules;<br/><br/>- Provide powerful **query languages** (e.g., SQL) to retrieve data by applying various operations on the data (filter, sort, join, etc.);<br/><br/>- Support for **concurrent access** and **transactional** management.|

<div align="justify">
Before diving into any initial comparison, it is important to split some terms from the previous table into two main sets:
<ul>
  <li>
    <strong>Tools</strong>, represented by <strong>data warehouse, data lakes</strong> and <strong>data lakehouses</strong>. A tool is a narrow technological aspect, even if it can be broken down into several subcomponents.
  </li>
  <li>
     <strong>Models/Methods</strong>, represented by <strong>data fabric</strong> and <strong>data mesh</strong>. A model is a wide general concept covering various technological and even non-technological aspects.
  </li>
</ul>
Let’s first focus on the tools. Considering the previous definitions (descriptions), probably the most confusing terms due to potential conceptual overlap are <trong>data lakes</strong> and <strong>data warehouse</strong>. A comparison table is provided below. Anyway, there are new technological proposals merging both approaches in what it is called <strong>data lakehouse</strong>. 
</div>

<br/>
|Data Lake (staging & preparation)|Aspect|Data warehouse (serving, security & compliance)|
|---|---|---|
|Structured, semi-structured, unstructured, raw/binary,Batch processing, Data refinement/cleaning Schema-on-read |**Data**|Structured, processed, Low latency, Complex joins, Schema-on-write.|



## TBC
