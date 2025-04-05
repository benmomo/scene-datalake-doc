# Semantics in the Film-making Industry

The film industry has traditionally relied on basic metadata and manual tagging for cataloguing and managing audiovisual content. However, the rise of large-scale digital archives, AI-assisted workflows, and semantic technologies has sparked a growing interest in more structured, machine-understandable representations of film knowledge — particularly through **ontologies**.

In the SCENE project, a dedicated effort was made to explore existing **film-related ontologies and vocabularies** that could enrich the semantic layer of data lakes. This section outlines the most relevant models currently used in the industry and cultural heritage domain.

---

## Why Semantics Matter in Film

Semantic technologies allow us to:

- Represent knowledge in a structured, interoperable way
- Enable **automated reasoning**, recommendation, and semantic search
- Support **cross-domain linking** (e.g., film metadata + cultural heritage archives)
- Improve **data discovery** and annotation during all film production stages

> Semantics is a key enabler for building **Linked Open Data (LOD)** graphs and enhancing metadata quality and retrieval.

---

## Key Ontologies in the Film & Media Domain

| Ontology | Description | Focus Area |
|----------|-------------|------------|
| **Schema.org** | A widely used vocabulary for structured data on the web. Includes types for `Movie`, `TVSeries`, `Person`, etc. | General metadata / Creative works |
| **EBUCorePlus** | Developed by the European Broadcasting Union. Offers rich technical and editorial metadata for audiovisual content. | Broadcasting / Media archives |
| **Dublin Core** | A simple, general-purpose standard for describing digital and physical resources. Often used in cultural heritage contexts. | Cross-domain / Archival |
| **OMC (Ontology for Media Creation)** | Created by MovieLabs. Models the full film production pipeline — including workflows, assets, and roles. | Film production lifecycle |
| **IPTC Video Metadata Hub** | Developed by the International Press Telecommunications Council. Provides a controlled vocabulary for video metadata. | Journalism / Metadata for video distribution |

---

## Reusability in SCENE

These ontologies are not adopted wholesale in SCENE, but rather:

- **Reviewed for relevant concepts and properties**
- **Partially re-used or aligned** in the design of SCENE-O
- Serve as **reference models** to ensure compatibility with tools like Europeana, Wikidata, or cultural databases

Examples of reused entities:
- `schema:Person`, `schema:Organization`, `schema:CreativeWork`
- EBUCore’s descriptors for `Shot`, `Scene`, `Asset`
- Dublin Core elements like `dc:title`, `dc:creator`, `dc:subject`

---

## Challenges in the Current Landscape

While many ontologies exist, their adoption in the film industry is still limited due to:

- Reliance on **custom or ad-hoc metadata**
- Low semantic richness in existing data
- Lack of tooling or awareness about semantic technologies
- Fragmentation between industry domains (e.g., production vs. archival)

---

## Semantic Contribution of SCENE

SCENE builds on this landscape by:
- Bridging media and cultural ontologies into one unified semantic layer
- Supporting dynamic annotations and tag generation
- Providing semantic interoperability across tools and pilots

To see how these ontologies are used as a foundation for SCENE's own model, see the next section: [Designing the SCENE Ontology](../designing-the-scene-ontology/)





   




 
