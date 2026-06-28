# public-data-metadata
This repository serves as the metadata backbone for a public evidence and dataset archive.  
It contains **structured metadata**, **schema definitions**, and **dataset descriptors** used to generate a public-facing site through GitHub Pages.

No datasets are stored in this repository.  
Instead, this repository provides a stable, platform‑agnostic catalog that describes datasets hosted externally.

---

## Purpose

The goal of this repository is to maintain a **neutral, durable, and transparent metadata system** for public datasets.  
It enables:

- A consistent structure for describing datasets
- Version tracking and provenance
- Schema definitions for validation
- A public GitHub Pages site that displays dataset information
- Links to externally stored datasets without referencing specific vendors or platforms

This separation ensures long-term stability and avoids dependency on any particular storage provider.

---

## Repository Structure

public-data-metadata/

│

├── _data/

│   ├── dataset_catalog.yaml      # Master dataset index

│   ├── schemas/                  # JSON schema definitions

│   │   ├── complaint_schema.json

│   │   ├── evidence_schema.json

│   │   └── timeline_schema.json

│   └── sources.yaml              # Optional: provenance for external storage
│
├── datasets/

│   ├── complaints_2019.md        # Dataset detail pages (auto-rendered)

│   ├── complaints_2020.md

│   ├── evidence_archive.md

│   └── ...

│

└── docs/

├── index.html                # GitHub Pages homepage

├── dataset.html              # Template for dataset detail pages

├── styles.css                # Site styling

└── _config.yml               # Jekyll configuration

---

## Metadata System Overview

### 1. Dataset Catalog (`_data/dataset_catalog.yaml`)

This YAML file is the central registry of all datasets.  
Each dataset entry includes:

- **id** — unique identifier  
- **title** — human-readable name  
- **description** — summary of dataset contents  
- **version** — semantic version number  
- **records** — number of records or files  
- **updated** — last update timestamp  
- **tags** — classification keywords  
- **storage** — external location information  
- **resources** — list of files or folders associated with the dataset  
- **schema** — reference to a JSON schema definition  

Example entry:

```yaml
- id: complaints_2020
  title: Complaints Filed (2020)
  description: Complaints filed with agencies during the year 2020.
  version: "1.0.1"
  records: 1332
  updated: "2021-03-12"
  tags: ["complaints", "filings", "public-records"]
  storage:
    type: external
    location: drive
    url: "https://example.com/external-folder"
  resources:
    - complaints_2020.csv
    - complaints_2020.json
    - evidence/
  schema: complaint_schema.json

All dataset metadata is neutral and does not reference any specific company or vendor.

2. Schema Definitions (_data/schemas/)
Schema files define the structure of each dataset type.
They ensure consistency across years and support validation.

Example fields include:
- identifiers
- dates
- agency names
- status fields
- evidence paths
Schemas are written in standard JSON Schema format.

3. Dataset Pages (/datasets/*.md)
Each dataset has a corresponding Markdown file that acts as a lightweight wrapper:
---
layout: dataset
dataset: complaints_2020
title: Complaints Filed (2020)
---
The GitHub Pages site uses this metadata to render a full dataset detail page automatically.

4. GitHub Pages Site (/docs/)
The /docs directory contains:
- the homepage
- dataset detail templates
- styling
- Jekyll configuration

The site dynamically reads metadata from _data/dataset_catalog.yaml and renders:
- dataset cards
- catalog tables
- metadata panels
- external dataset links
- schema references
This creates a clean, structured interface similar to modern open‑data portals.

# External Storage
Datasets referenced in this repository are stored externally.
The metadata system treats external storage generically using the following fields:
storage:
  type: external
  location: drive
  url: "https://example.com/external-folder"
This approach avoids naming any specific service provider and allows storage to be moved or replaced without changing the metadata structure.

# Versioning & Provenance
Each dataset entry includes:
- a semantic version number
- a last-updated timestamp
- optional provenance fields in sources.yaml
This ensures transparency and traceability across updates.

# Contributing
To add or update a dataset:
- Edit _data/dataset_catalog.yaml
- Add or update schema files in _data/schemas/
- Create a dataset page in /datasets/
- Commit and push changes
GitHub Pages will rebuild automatically

# License
All metadata in this repository is intended for public use and may be reused freely.
