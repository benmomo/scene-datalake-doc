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


---

## 
