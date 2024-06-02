# Data Lake Architectures

<div align="justify">
A simplified overview of a data lake is depicted in the Figure below. The <strong>ingestion layer</strong> is responsible for <strong>processing</strong> the different input data sources. This processing should be understood in a simple way without any relevant transformation of the data (the term ETL -extract, transform, load – is used for data warehouses). The input data are then stored in the <strong>storage layer</strong>, preserving its nature (structured, semi-structured, unstructured or raw data). Two additional layers go together with the storage layer:
<ul>
  <li>
<strong>Governance layer</strong>: it is responsible for implementing and enforcing data policies on the system. It is a short of control layer able to manage pipelines of data. Note that for data lakes, <strong>governance</strong> and <strong>data quality</strong> is a big challenge: poorly managed data lakes are called <strong>data swamps</strong> when there is a lot of duplicated, inaccurate or incomplete data. Therefore, a successful data lake implies being aware of the relevance of data and metadata for a given organization.
   </li>
   <li>
<strong>Analysis layer</strong>: this layer is responsible for providing supporting tools to prepare the data, extract features or train the data.
 </li>
</ul>
Outputs of the analysis layer are expected to feed the <strong>application layer</strong>, which can be implemented in the form of a simple dashboard or an app if users are intended to consume that data. Additionally, the application layer can also take part of the output data and feed a data warehouse.
 
</div>

<br/>
<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_arch1.jpg?raw=true" alt="Ontology spectrum" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" />
<br/>

<div align="justify">
From an <strong>AI perspective</strong>, the four AI typical phases map to the following layers:
<ul>
  <li><strong>Collect</strong>: ingestion layer and storage layer</li>
  <li><strong>Organize</strong>: analysis layer and storage layer</li>
  <li><strong>Analyze</strong>: analysis layer</li>
  <li><strong>Infuse</strong>: application layer</li>
</ul>

From a <strong>logical perspective</strong>, and considering a <strong>Hadoop architecture</strong>, there are <strong>three</strong> layers, as depicted in the Figure below. Hadoop is a typical reference technology used in data lakes, due to the way is supports large volumes of data (Big Data).
The <strong>first layer</strong> (input layer) considers all different <strong>input data sources</strong> that should be handled and stored. They are typically divided into: (i) traditional data that has typically been managed from the internal <strong>operational systems</strong> (ERP, CRM and billing), and (ii) emerging data sources that have been added in the last years to enhance the operational picture and better study a particular situation. These data can be either internal or external data.

The <strong>second layer</strong> includes various tools and sublayers. First, the <strong>ingestion sublayer</strong> provides a set of converters for the different input sources, without altering the original structure; it will basically allow further <strong>search and discovery</strong> one the data is stored in the layer, typically in the form of a <strong>distributed and scalable file system</strong>.
The <strong>third layer</strong> refers to the <strong>visualization of data</strong> and the <strong>user profiles</strong> accessing to such visualization.  In most cases, common users are data scientists, analysts, developers or administrators; however, sometimes also some specific (business) users might have access to this data, such a CEO or CTO that need to have some information as soon as possible.
</div>

<br/>
<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_arch2.jpg?raw=true" alt="Ontology spectrum" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" />
<br/>

<div align="justify">
From an operational point of view of the quality of the data within the data lake (more commonly used in data lakehouses), there are typically three areas or phases (see Figure below) that have various names in the data engineering terminology:
<ul>
  <li>
  The first phase refers to the bronze, landing or raw zone, where data is typically stored without any modification to preserve the original format. Data tagging – both automated and manual – is also included in this zone. Sometimes there is a previous supporting transient zone to facilitate the ingestion.</li>
  <li>
    The second phase is the silver, refinery, stage or trusted zone, where data is filtered and cleaned according to the needs of the company (defined by data scientists). The result is data ready for processing. Here the schemas of the data are defined as needed.</li>
  <li>
    The third phase is the gold, refined, curated or production zone with business level data (e.g. loaded into Hive) that is continuously updated and can be delivered to users and apps. Sometimes this phase is ‘externalized’ to a data warehouse.</li>
</ul>
</div>

<br/>
<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_arch3.jpg?raw=true" alt="Ontology spectrum" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" />
<br/>

