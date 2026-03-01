# EDU AI Agent - ABC Consulting Volunteering Project
A Vertical AI Agent System for Medical Aesthetics Job Semantic Standardization & Capability Graph Construction
## Background
In the medical aesthetics industry, job descriptions (JDs) are highly fragmented:
  1. Different titles may represent the same core role
  2. Similar responsibilities are expressed using inconsistent language
  3. Noise data (salary, location, benefits) obscures semantic structure
  4. Capability requirements are not standardized

This fragmentation makes it difficult to:
  1. Build structured talent taxonomie
  2. Analyze skill trends
  3. Compare roles across organizations
  4. Train AI systems reliably

Traditional keyword-based parsing is insufficient because job semantics require deep contextual reasoning.
This project introduces a vertical AI Agent architecture that standardizes job roles and constructs a structured capability graph using large language models.
## Overview
MedAI-JobGraph is a domain-specific AI system that:
  1. Standardizes semantically equivalent job titles
  2. Generates official job taxonomies
  3. Creates dual-layer unique identifiers
  4. Extracts structured capability elements
  5. Aggregates and deduplicates skills
  6. Computes skill weights
  7. Outputs a reusable job capability graph
This is not a generic AI Agent framework, but a vertical intelligence system optimized for high-accuracy domain reasoning.
## Workflow
![System Architecture](images/whiteboard_exported_image.png)
## Objective 
### Core Objectives
Transform unstructured JD text into structured role intelligence
Build a stable role–skill ontology
Enable measurable skill weight computation
Support feedback-loop evolution
### Long-Term Vision
Become the capability standard layer for medical aesthetics hiring
Provide structured APIs for ATS / LMS / HR analytics
Evolve into a vertical AI Agent platform for talent intelligence
## Analytic Flow
```
Raw JD Data
    ↓
Filtering & Preprocessing
    ↓
JD-Level Unique ID (A-ID)
    ↓
Semantic Role Analysis (LLM)
    ↓
Role Deduplication & Merge
    ↓
Official Role Name Generation
    ↓
Role-Level Unique ID (B-ID)
    ↓
JD ↔ Official Role Mapping
    ↓
Skill Extraction (LLM Parsing)
    ↓
Skill Structuring
    ↓
Skill Semantic Deduplication
    ↓
Frequency Statistics
    ↓
Weight Calculation
    ↓
Job Capability Graph Output
```
## Example Output
