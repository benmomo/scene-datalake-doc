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
The front-end is basically a web server (nginx) acting as a proxy with a set of web pages that give access to all services related to the SCENE data lake, as depicted in the Figure below:

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
2. Click **Identity-->Users**, and then **Create User**
3. Provide a unique name (e.g. `testuser`) and a password
4. Assign a policy from the ones available (e.g., you can assigne the tespoolicy you have created in the previous step)

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_minio3.jpg?raw=true" alt="Minio user" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" /> 

<br/>

After that, youn now log in into the Minio UI with his user and password.
There is another way, which is the typical way used by applications, and it employs the API. The API is S3-compatible. Examples are provided via Jupyter Notebook

## Using the Minio API (Jupyter Notebook)

There are two common ways to interact with the SCENE Data Lake (Minio) programmatically using Python:

- **MinIO Python SDK (`minio` package)**: A dedicated library developed by the MinIO team.
- **Boto3 (`boto3` package)**: Amazon’s official SDK for AWS services, fully compatible with S3 APIs — and therefore also works seamlessly with MinIO.

In this guide, we will use **boto3**, which is a robust, well-documented library and often familiar to developers working with cloud environments. It can be used directly in a Jupyter Notebook to upload, download, and list files in the MinIO-powered data lake.
In the front-end, just click on the **Example** list:


<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_jupyter1.jpg?raw=true" alt="Minio user" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" /> 

<br/>

On the left panel, you can see a small set of files that serve as examples of using the API. The first one (01 minio_upload_file.ypynb) provides an example of basic access for uploading, listing and downloading a file

```
# 0. Load libraries and common configuration. Install necessary packages
!pip install boto3 certifi

import boto3
from botocore.client import Config
import os
import ssl
import certifi
import sys
import warnings
warnings.filterwarnings('ignore')

#Some issues might appear (SSL verification error) with yhe client if python is not properly configured. 
# You might find this line useful to skip the error 
ssl._create_default_https_context = ssl._create_unverified_context

# MinIO server connection information
minio_url = 'https://s3api.scene.local'  # Replace with your MinIO instance URL
access_key = 'testuser'       # Replace with your actual access key
secret_key = 'testscene'       # Replace with your actual secret key

# Initialize a session using boto3
session = boto3.session.Session()

# Create a client with the MinIO server
# Add "verify=False" tothe list if you have troubles with SSL verification
s3_client = session.client(
    's3',
    verify=False,
    endpoint_url=minio_url,    
    aws_access_key_id=access_key,
    aws_secret_access_key=secret_key,
    config=Config(signature_version='s3v4'),
    region_name='us-east-1'  # You can choose any region name. Not applicable here
)
print("Libraries loaded successfully")


# 1. Upload a file to the Data Lake

file_path='athens.png'
bucket_name = 'testbucket'     # Bucket to upload the file to
object_name = 'images/athens2.png'    # Object name in the bucket (can be a path like 'folder/file.txt')

# Upload the file

s3_client.upload_file(file_path, bucket_name, object_name)
print("Upload successful")

# 2. List all files from a bucket within a Data Lake
# List objects in the bucket
response = s3_client.list_objects(Bucket=bucket_name)

# Print each file name (key)
if 'Contents' in response:
    for file in response['Contents']:
        print(file['Key'])
else:
    print("No files found in the bucket.")


# 3. Download file from a Data Lake

# File details
download_path='athens_download.png'
bucket_name='testbucket'
object_name = 'images/athens2.png'    

# Download the file
s3_client.download_file(bucket_name, object_name, download_path)
print(f"Downloaded {object_name} to {download_path}")


# 4. Delete a file from the Data Lake

# Delete the file
s3_client.delete_object(Bucket=bucket_name, Key=object_name)
print("Delete successful")

```


<br/><br/>




