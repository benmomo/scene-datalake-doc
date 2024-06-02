# Data Lake Introduction

<div align="justify">
In the rapidly evolving landscape of data management, a common challenge emerges: the proliferation of diverse and sometimes **overlapping terminology**. As organizations strive to harness the <strong>power of data</strong> for informed decision-making, they encounter a large set of terms like <strong>data lake, data warehouse, data mart, data fabric, data lake house</strong>, and many more. <br/>
These terms often represent distinct concepts, but their boundaries can blur, causing <strong>confusion</strong> and miscommunication among data professionals and stakeholders. Hence, a comprehensive reference terminology seems sensible to not only define these concepts but also establish clear boundaries and relationships among them. A summary reference table is provided in the Table below. 
</div>

|Concept|Description|
|---|---|
|**Data Lake** |- Central and reliable repository to store and process large amounts of data, which can be structured (relational databases), semi-structured (CSV, JSON), unstructured (documents, e-mails) or **binary** (images, audio, video). It is able to store data in its **native format** and process multiple data types;<br/><br/> - Can be deployed on premises or in the cloud (e.g. Amazon, Microsoft, Google); - Intended for **general analysis** and **reports** from raw/massive data (**data scientists** using AI techniques and languages such as SQL, Python, R); - Simple architecture (James Dixon): Hadoop File System (**HDFS**) with lots of folders/files;<br/><br/> - Media and entertainment sector typically uses data lakes to improve its recommendation system;<br/><br/> - **Pros**: High availability, fast access and processing, relatively cheap (cost/size);<br/><br/> - **Cons**: Limited quality and data governance.|
|**Data Warehouse** |- Data repository for **filtered** (processed) and **structured** data with a **specific** purpose;<br/><br/> -	Typical target users are **business**-oriented people (**decision-making**);<br/><br/> -	Serves as **single source of truth** for a company across multiple knowledge domains;<br/><br/> - Source data (transactional systems, relational DBs) are converted from raw to high-quality data via **ETL** (Extract, Transform and Load) tools;<br/><br/> - Changes are **less flexible** and **less typical** than for data lakes;<br/><br/> -	**Pros**: data already processed saving disk size, data useful for non-technical, high-performance for queries, governance model more robust (compared to data lake);<br/><br/> - **Cons**: cost (compared to data lake), none to very limited support to unstructured data, delay until ‘fresh’ processed data arrives (limitation for RT).|
|**Data Mart** |- **Subset** of Data warehouse more specific to a **particular domain** (e.g., finance).|


## TBC
