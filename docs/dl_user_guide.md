# Data Lake User guide 

This user guide explains how to interact with the SCENE Data Lake, with a primary focus on MinIO — the central component responsible for managing storage and access to multimedia files and associated metadata in the SCENE ecosystem.


## Introduction: Working with MinIO-Centric Data Lakes

The SCENE project leverages a modular, open-source architecture to support the entire film production pipeline with cognitive tools and semantic enrichment. At the heart of its Data Lake lies **MinIO**, an S3-compatible object storage solution designed to handle vast amounts of unstructured film-related data — from raw footage and audio to metadata and annotations. MinIO provides:

  - **Efficient object storage** for video, audio, images, and text
  - **Scalability** across multiple nodes and environments
  - **Fine-grained access control** through users, buckets, and policies
  - **Compatibility** with cloud-native tools and Jupyter-based APIs

While other components (such as Apache NiFi, Node-RED, and MongoDB) provide supporting functionalities for ingestion, transformation, and querying, **MinIO acts as the backbone for persistent storage** and serves as the main entry/exit point for data within the SCENE platform.


## Front-end
The front-end is basically a web server (nginx) acting as proxy with a set of web page that gives access to all services related to the SCENE datalae, as depicted in the Figure below:

  - By clicking on the **Ontology viewer** icon/link, the user will be redirected to the Ontology view, which has its own UI
  - The **Data Lake UI** redirects to the Minio Front-end. Minio represents the core part of the data lake
  - The **Code repository** icon links directly to the public GitHub repository.
  - The **Documentation** link provides access to an online documentation portal (via readthedocs)
  - The **idP** provides access to KeyCloak, in order to manage identity and access
  - The **Data Ingestion** link provides access to an **Apache NiFi** instance to set up **advanced data ingestion** procedures
  - The **Data Flows** link provides access to a **Node-red** instance to set up **simple data ingestion** procedures
  - The **SQL DB** link provides access to a **Trino UI** instance to monitor Trino (SQL database)
  - The **NoSQL DB** link provides access to a **Mongo UI** to monitor Mongo (noSQL database)
  - The **Examples** link provides access to a **Jupyter Notebook** instance with some useful examples to access and use Minio through its API

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_frontend.jpg?raw=true" alt="frontend" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" /> 




## Using MinIO

MinIO is an open-source, high-performance object storage service with full compatibility with the Amazon S3 API. In SCENE, MinIO stores all film-related assets — from raw camera footage to scripts, images, and metadata JSON files — in scalable buckets accessible to all platform components.

**MinIO is used to:**

  - Organize data into buckets per project or media type
  - Manage access credentials and custom policies
  - Interact programmatically via REST API or SDKs
  - Power semantic queries and machine learning tools


**Buckets** are logical partitions — you can think of them as "folders" for specific content types (videos, scripts, metadata, etc.).

You can **create buckets** by doing the following:

1. Access the MinIO web interface (typically at `http://<your-ip>:9000`, but if you use the SCENE data lake it could be something as `https://s3ui.scene.local`, depending on your DNS domain)
2. Log in with your admin or user credentials
3. Click **Create Bucket**
4. Provide a unique name (e.g. `testb`)
5. Set some optional parameters (versioning, object locking and quota) 

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_minio1.jpg?raw=true" alt="Minio bucket" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" /> 

<br/>

The next step is to create (at least) one **policy** for the bucket. You can **create a policy** by doing the following:

1. Access the MinIO web interface as before
2. Click **Policies**, and then **Create Policy**
3. Provide a unique name (e.g. `testpolicy`)
4. Provide the policy in the specific format

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_minio2.jpg?raw=true" alt="Minio policy" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" /> 

<br/>

Policies have a special (JSON) format. Below you can find one example that allows certain actions on the bucket called **testbucket**


```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetBucketLocation",
                "s3:ListBucket",
                "s3:ListBucketMultipartUploads"
            ],
            "Resource": [
                "arn:aws:s3:::testbucket"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:AbortMultipartUpload",
                "s3:DeleteObject",
                "s3:GetObject",
                "s3:ListMultipartUploadParts",
                "s3:PutObject"
            ],
            "Resource": [
                "arn:aws:s3:::testbucket/*"
            ]
        }
    ]
}
```

<br/>
The next step is to create one **user**. You can **create a user** by doing the following:

1. Access the MinIO web interface as before
2. Click **Identity-->Users**, and then **Create USer**
3. Provide a unique name (e.g. `testuser`) and a password
4. Assign a policy from the ones available (e.g., you can assigne the tespoolicy you have created in the previous step)

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_minio3.jpg?raw=true" alt="Minio user" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" /> 

<br/>

<br/><br/>




