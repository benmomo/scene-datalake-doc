# User guide 

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

To explore the structure of SCENE-O graphically, we recommend loading it into [WebVOWL](https://webvowl.scene.local/). You can go to the 'Ontology' item in the bottom menu and select SCENE-O among other ontologies that are also listed

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

Alternatively, there is the [datalñake repository](https://github.com/benmomo/scene-datalake)

## 3. Annotating Data Using SCENE-O

SCENE-O enables rich semantic annotation of multimedia content such as video clips, images, scripts, and related documents. These annotations can be expressed using RDF triples, JSON-LD fragments, or Turtle syntax — and can later be stored, queried, or linked to external datasets.

This section demonstrates how to annotate data manually using SCENE-O terms.


### 🧠 3.1 RDF Annotation Example (Turtle)

Here's a simple example of a scene annotation using Turtle (`.ttl`) syntax:

```turtle
@prefix schema: <http://schema.org/> .
@prefix sceneo: <http://scene-project.eu/ontology#> .
@prefix dc: <http://purl.org/dc/elements/1.1/> .

<http://example.org/scene/42> a sceneo:Scene ;
    dc:title "Final confrontation at the castle" ;
    sceneo:hasLocation <http://example.org/location/castle> ;
    sceneo:hasCharacter <http://example.org/character/hero> ;
    sceneo:hasEmotion sceneo:Suspense ;
    sceneo:isPartOf <http://example.org/asset/film-01> .
