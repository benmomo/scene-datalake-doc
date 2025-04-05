# SCENE-O User Guide

This guide explains how to use the **SCENE Ontology (SCENE-O)** for semantic annotation, search, and integration within the SCENE platform. It is intended for technical users, developers, and data annotators involved in film-related metadata enrichment or semantic processing.

SCENE-O is a modular, scalable, and Linked Data-compliant ontology designed to describe the full film production pipeline — from pre-production elements like scripts and locations, to post-production metadata, audience feedback, and distribution insights.



## 1. Introduction

SCENE-O supports:

- 🎬 **Semantic description of media assets** (videos, images, audio, scripts)
- 🔎 **Ontology-based search and recommendation**
- 🔗 **Integration with Linked Open Data (LOD)** ecosystems
- 🧠 **Enrichment for AI/ML pipelines** (genre detection, mood tagging, etc.)

The ontology is available in standard RDF/OWL formats and can be explored visually, queried semantically, or used as part of automated data ingestion pipelines.



## 2. Exploring the Ontology

SCENE-O is published in RDF and OWL formats and can be accessed through multiple tools:

### 🔎 2.1 Visual Exploration with WebVOWL

To explore the structure of SCENE-O graphically, we recommend loading it into [WebVOWL](https://webvowl.scene.local/) fro mthe front-end (Ontology Viewer). You can go to the 'Ontology' item in the bottom menu and select SCENE-O among other ontologies that are also listed

You will see:

- **Blue nodes**: Classes (e.g., `Scene`, `Asset`, `Person`)
- **Arrows**: Object properties (e.g., `hasCharacter`, `wasDirectedBy`)
- **Labels**: Human-readable descriptions



### 🧠 2.2 Semantic Structure Overview

SCENE-O reuses and extends elements from existing vocabularies, including:

| Reused From | Example Classes / Properties |
|-------------|------------------------------|
| `schema.org` | `CreativeWork`, `Person`, `Organization`, `Event` |
| `EBUCorePlus` | `MediaAsset`, `Shot`, `Scene`, `TechnicalMetadata` |
| `Dublin Core` | `dc:title`, `dc:creator`, `dc:subject` |
| `OMC` | `AssetVersion`, `WorkflowTask`, `EditorialRole` |

### 🧩 2.3 Key SCENE-O Classes

| Class | Description |
|-------|-------------|
| `Scene` | A meaningful narrative unit in a film or video |
| `Shot` | A continuous sequence captured by the camera |
| `Character` | A fictional or real persona in the narrative |
| `Asset` | A multimedia file or supporting document |
| `Location` | Real-world or fictional filming location |
| `Tag` | A semantic keyword or theme associated with content |

> 🔧 All classes include labels, comments, and alignments to external vocabularies where relevant.



### 📁 2.4 Accessing SCENE-O Files

You can download the ontology files [here] (https://scene.local/ontology/scene.ttl) in TTL formats. You can also get related ontologies at:

- [DublinCore] (https://scene.local/ontology/dublincore.owl) (OWL)
- [EbuCorePlus] (https://scene.local/ontology/ebucoreplus.owl) (OWL)
- [OMC] (https://scene.local/ontology/omc.ttl) (TTL)
- [OMD] (https://scene.local/ontology/omd.ttl) (TTL)
- [Schema.org] (https://scene.local/ontology/schemaorg.owl) (OWL)

Alternatively, there is the [data lake repository](https://github.com/benmomo/scene-datalake)

## 3. Annotating Data Using SCENE-O

SCENE-O enables rich semantic annotation of multimedia content such as video clips, images, scripts, and related documents. These annotations can be expressed using RDF triples, JSON-LD fragments, or Turtle syntax — and can later be stored, queried, or linked to external datasets.

This section demonstrates how to annotate data manually using SCENE-O terms.


### 🧠 3.1 RDF Annotation Example (Turtle)

Here's a simple example of a scene annotation using Turtle (`.ttl`) syntax:

```
@prefix schema: <http://schema.org/> .
@prefix sceneo: <http://scene-project.eu/ontology#> .
@prefix dc: <http://purl.org/dc/elements/1.1/> .

<http://example.org/scene/42> a sceneo:Scene ;
    dc:title "Final confrontation at the castle" ;
    sceneo:hasLocation <http://example.org/location/castle> ;
    sceneo:hasCharacter <http://example.org/character/hero> ;
    sceneo:hasEmotion sceneo:Suspense ;
    sceneo:isPartOf <http://example.org/asset/film-01> .
```

### 💬 3.2 JSON-LD Annotation Example

Below is the same annotation expressed in `JSON-LD`, a format suitable for embedding in metadata, scripts, or ingestion tools:

```json
{
  "@context": {
    "sceneo": "http://scene-project.eu/ontology#",
    "dc": "http://purl.org/dc/elements/1.1/"
  },
  "@id": "http://example.org/scene/42",
  "@type": "sceneo:Scene",
  "dc:title": "Final confrontation at the castle",
  "sceneo:hasLocation": { "@id": "http://example.org/location/castle" },
  "sceneo:hasCharacter": { "@id": "http://example.org/character/hero" },
  "sceneo:hasEmotion": { "@id": "sceneo:Suspense" },
  "sceneo:isPartOf": { "@id": "http://example.org/asset/film-01" }
}
```

This format is ideal for use in pipelines like **Apache NiFi, Node-RED**, or **Jupyter Notebooks**, where JSON is a preferred and easily parsable format.

### 🏷️ 3.3 Common Annotation Targets

Below are typical annotation targets within the SCENE platform, along with example uses of SCENE-O terms:

| Target             | Example Annotation                                           |
|--------------------|--------------------------------------------------------------|
| **Video Clip**     | `sceneo:Asset` with type `schema:VideoObject`               |
| **Script Segment** | `sceneo:Scene` with `dc:subject` and `sceneo:hasCharacter`   |
| **Location Tag**   | `sceneo:hasLocation` with link to external URI or vocabulary |
| **Emotion or Mood**| `sceneo:hasEmotion` (e.g., `sceneo:Romantic`, `sceneo:Tense`) |

Using consistent semantic annotations improves the quality of search, linking, and reasoning over the data.


### 🔗 3.4 Connecting to External Vocabularies

SCENE-O annotations are designed to integrate with external Linked Data vocabularies to enhance interoperability. You can link to:

- **Wikidata** for entities like `Person`, `Location`, `Genre`, etc.
- **GeoNames** or **OpenStreetMap** for precise geographic references
- **Europeana** and other cultural vocabularies for tagging cultural elements

Example (Turtle syntax):

```
<http://example.org/scene/42> sceneo:hasLocation <http://www.geonames.org/2643743/london.html> .
```

## 4. Integrating SCENE-O into Workflows

Semantic annotations using SCENE-O are not just metadata — they are active components of the SCENE data pipeline. This section describes how SCENE-O is used during ingestion, enrichment, and querying, and how it fits into real tools like **Apache NiFi**, **Node-RED**, and **Jupyter Notebooks**.


### 🔄 4.1 Semantic Annotations in Ingestion Pipelines

Ingestion tools like **Apache NiFi** and **Node-RED** are used to collect multimedia files (videos, scripts, images) and their metadata. SCENE-O annotations can be embedded directly into the metadata objects or generated during processing.

#### Example: Ingesting a script with annotations
1. A `POST` request is made to a Node-RED endpoint with a JSON body that includes:
   - Script text
   - SCENE-O tags (e.g., `sceneo:hasEmotion`, `dc:title`)
2. Node-RED or NiFi parses and validates the content.
3. Metadata is stored in MongoDB or MinIO alongside the original asset.



### ⚙️ 4.2 Connecting SCENE-O to MinIO

Semantic annotations can be stored:
- As **sidecar metadata files** in MinIO (e.g., `.jsonld`)
- Embedded within larger compound objects (e.g., a video bundle)

> Recommended: Use consistent file naming and folder structures to keep annotations aligned with media files.



### 📓 4.3 Querying with Jupyter Notebooks

In the SCENE environment, Jupyter Notebooks allow you to interact with annotated data using Trino or SPARQL.

#### Example: Search for romantic scenes in beach locations

```sql
SELECT *
FROM scenes
WHERE hasEmotion = 'sceneo:Romantic'
  AND hasLocation LIKE '%beach%'
```
You can also perform federated SPARQL queries if the annotations are published to a triplestore or knowledge graph.


### 🧪 4.4 Validation and Testing

To ensure your semantic annotations conform to the SCENE-O ontology, it’s important to validate both structure and semantics. Here are recommended tools and methods:

- ✅ **Protégé**: Load your RDF or OWL files into Protégé to check:
  - Class and property usage
  - Ontology alignment and inheritance
  - Data consistency

- ✅ **SHACL (Shapes Constraint Language)**: Define validation rules for expected structures. For example:
  - `sceneo:Scene` must have at least one `sceneo:hasLocation`
  - `sceneo:Asset` must include a `dc:title` and be linked via `sceneo:isPartOf`

- ✅ **WebVOWL**: Use this visualization tool to inspect the graph layout and ensure relationships are meaningful and connected as expected.

These validation steps are especially useful during:
- Ingestion testing
- Ontology updates
- Pilot integration phases

