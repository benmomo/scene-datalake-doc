# Designing the SCENE Ontology

The **SCENE Ontology (SCENE-O)** is a domain-specific semantic model developed to support the annotation, retrieval, and interoperability of film-related data within the SCENE platform.

Unlike existing ontologies, which often cover either generic metadata or specific media production aspects, SCENE-O is designed to be:

- **Agnostic**: reusable across different film genres, production pipelines, and cultural domains
- **Scalable**: extendable through modular vocabularies
- **Interoperable**: aligned with Linked Data principles and existing ontologies



## Purpose of SCENE-O

SCENE-O aims to enable:

- Rich semantic annotation of multimedia content (e.g., scenes, shots, locations, people)
- Ontology-driven **semantic search** in the data lake
- Integration of metadata from different sources (videos, scripts, social media)
- Compatibility with other tools in the SCENE architecture (e.g., Media Asset Manager, AI modules)

> SCENE-O is the semantic backbone that connects the technical infrastructure with human-understandable concepts.



## Ontology Composition

SCENE-O reuses and extends concepts from key ontologies:

| Source Ontology | Reused Concepts |
|------------------|-----------------|
| **Schema.org** | `CreativeWork`, `Person`, `Event`, `Organization` |
| **EBUCorePlus** | `MediaAsset`, `Scene`, `Shot`, `TechnicalMetadata` |
| **OMC** (MovieLabs) | `ProductionWorkflow`, `AssetVersion`, `EditorialTask` |
| **Dublin Core** | `dc:title`, `dc:subject`, `dc:creator` |

These were merged selectively to cover the SCENE workflow and mapped into the ontology using RDF/OWL standards.



## Example: Ontology Snapshot

The figure below shows the ontology loaded into the **WebVOWL viewer**.

<img src="https://github.com/benmomo/scene-ontology-doc/blob/main/docs/img/dl_ontology1.jpg?raw=true" alt="SCENE Ontology" style=" display: block;  margin-left: auto;  margin-right: auto; width: 100%;" />



## Ontology Layers and Entities

SCENE-O groups entities into three core domains:

1. **Production & Content** : `Scene`, `Shot`, `Script`, `Asset`, `Storyboard`
2. **People & Roles**:  `Director`, `Editor`, `Cinematographer`, `Actor`, `Character`
3. **Context & Semantics**: `Location`, `Theme`, `Genre`, `CulturalReference`, `Emotion`, `Tag`

Each entity is linked using object properties (e.g., `hasActor`, `takesPlaceIn`, `hasGenre`) and annotated with metadata.



## Methodology and Tools

SCENE-O was built following best practices in ontology engineering:

### 💡 Methodology
- **Requirements-driven**: Terms were gathered through user stories and pilot use cases.
- **Reusability-first**: Emphasis on aligning with existing standards over creating new terms.
- **Iterative modeling**: Continuous feedback from technical and domain partners.

### 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **Protégé** | Ontology modeling and validation (OWL/RDF export) |
| **WebVOWL** | Visual inspection and validation |
| **Jupyter Notebooks** | Semantic querying and integration testing |
| **Custom API (planned)** | To expose ontology-based search functionality |

--

## Semantic Features Enabled

With SCENE-O, the platform supports:

- ✅ Ontology-based tagging and metadata enhancement
- 🧠 AI integration (e.g., for emotion detection or genre classification)
- 🔗 Linked Data export for external publishing



## Example Use Case

🎬 A director uploads a video clip and a script. SCENE-O is used to:

- Tag scenes with `hasEmotion` and `hasLocation`
- Link the director and actors to existing `Person` instances
- Annotate script fragments with `dc:subject` and `schema:CreativeWork`

These annotations enable cross-pilot semantic search (e.g., "Find all romantic scenes shot in coastal regions") or integration with Europeana-style archives.



## Next Steps and Maintenance

- SCENE-O is published as an RDF/OWL ontology (Turtle and JSON-LD)
- Documentation and usage guidelines are provided through this portal
- The ontology is versioned and maintained on the SCENE GitHub repository
- Feedback from pilots will guide future updates and extensions


