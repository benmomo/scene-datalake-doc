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
|Structured, semi-structured, unstructured, raw/binary,Batch processing, Data refinement/cleaning|**Data**|Structured, processed, Low latency, Complex joins.|
|Schema-on-read|**Processing**|Schema-on-write.|
|Designed for Low-cost storage (store older/backup data)|**Storage**|Expensive for large data volumes.|
|Highly agile, reconfiguration feasible|**Agility**|Less agile, reconfiguration typically not feasible (fixed).|
|Maturing (relatively new tech)|**Security**|Mature technology.|
|Data scientists (sandbox for data exploration)|**Users**|Business professionals (Dashboards).|

Data lakes can be useful under different generic scenarios, as presented in the Table below

|Scenario|Description|
|---|---|
|**Support for traditional and emerging data sources**|Analyze in real-time information (huge data) from various origins: customer, demographics, employee, social data, external data, etc.|
|**Data exploration sandbox**|Capacity to retrieve specific datasets and attributes from the whole data store through filtering techniques, to be later used in analytic tools.|
|**Extended customer analysis**|Analysis of user behavior through all their possible interactions (coming from various sources).|
|**Centralized Discovery**|Single centralized discovery engine for discovering and managing published datasets.|

<div align="justify">
Another aspect to reflect on is the relationship between <strong>data lakes</strong> and <strong>data mesh</strong>. Initially, when <strong>Big Data</strong> started to be a hype, there was a general <strong>market trend</strong> to store all sorts of data into a common <strong>centralized repository</strong> (e.g., data lake) and check later their <strong>potential</strong> through analytics.
</div>
<br/>

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_dataflow.jpg?raw=true" alt="Ontology spectrum" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" />

<br/>

<div align="justify">
Though it seemed a good idea, there were some drawbacks. As data volumes grew, so did the complexity of managing these lakes, leading to <strong>data silos</strong>, inconsistent <strong>data quality</strong>, and difficulties in deriving meaningful insights. 
From a <strong>data mesh</strong> perspective, a paradigmatic shift that recognizes the need for a more <strong>decentralized, domain-oriented</strong> approach. Unlike the centralized model of data lakes, data mesh decentralizes data ownership, empowering individual domain teams to treat data as a product. This transformation is driven by the recognition that domain experts <strong>understand their data best</strong> and can <strong>manage</strong> it effectively. By fostering a <strong>culture of ownership, accountability, and collaboration</strong>, data mesh not only resolves the challenges of data lakes but also unleashes the potential of diverse, high-quality data. It allows organizations to <strong>adapt swiftly</strong> to changing business needs, democratize data access, and foster innovation by enabling cross-functional teams to seamlessly collaborate, transforming raw data into valuable insights. This shift is not just technological but also cultural, acknowledging that the future of data lies in the hands of those who understand it most intimately – the experts within the domains.
Data mesh can be seen as an <strong>evolution</strong> of data lakes, not a replacement. This means that data lakes already have their meaning and usefulness as a first phase, <strong>facilitating</strong> the way towards the data mesh, which should be considered as a medium or long-term step. The <strong>SCENE project</strong> is focussed on data lakes and this first phase, considering the immature (technological) status of the film-making industry, at least for the majority of the main stakeholders who have limited IT knowledge and/or resources. Additionally, <strong>data lakes pave the way towards data mesh</strong> by identifying the different domains and subdomains for data treatment and their interactions across the whole film pipeline (pre-production, production, post-proc, distribution). Moreover, considering the <strong>evolution</strong> of data approaches in the last 40 years (see Figure below), it seems more sensible to focus on a <strong>data lakehouse</strong>, as an <strong>extension</strong> of a data lake, still centralised and conceptually more similar to a data mesh
</div>

br/>

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_evolution.jpg?raw=true" alt="Ontology spectrum" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" />

<br/>

<div align="justify">
Finally, besides describing the different technological approaches to manage data, it is also important to not forget the <strong>meaning of data</strong> within an enterprise and the value it generates. The digital transformation accelerates the way data impacts an organization, as presented in the Table below.
</div>

<br/>

|Phase|Description|
|---|---|
|**1. Resctive**|Structured data is mainly managed locally and used reactively.|
|**2. Informative**|Structured data is managed and analysed centrally to inform the business department.|
|**3. Predictive**|Captured data comes in big volumes and allows advanced analytics so as to make predictions leading to business decisions.|
|**4. Transformative**|Data helps the company transform towards its business purpose in an efficient way by handling data anytime, anywhere .|

