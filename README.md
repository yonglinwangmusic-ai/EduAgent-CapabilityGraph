# EduAgent-CapabilityGraph
# AI Agent Architecture for Vocational Education Capability Graph Construction
ystem architecture design for transforming fragmented recruitment data into structured capability graphs for vocational education, using vertical AI Agents. Domain-agnostic — piloted with medical aesthetics. Created as a pro-bono consulting project for A Better Community (ABC), a social enterprise mobilizing professional volunteers to provide management consulting for social organizations in China.
## My Role
I served as volunteer Solution Architect for this project. This repository documents my architecture and solution design work. The implementation was carried out by the broader project team (~15 volunteers) on the Coze (ByteDance) platform.
## Background
This project serves Polus International College — a vocational institution with 5 schools, 50 programs, 17,000+ students, and ~600 faculty, established in 1993 with 60,000+ graduates and a 97%+ employment rate.
The college faces a core challenge shared by all vocational institutions: aligning curricula with market demand at scale. Manual curriculum review takes 2+ months per program; covering all 50 programs with structured, data-driven analysis is practically impossible without automation.
This project is the 0-to-1 cold start — building a reusable AI Agent architecture that can be applied program-by-program, starting from a single pilot and scaling toward full institutional coverage.
## Problem Analysis
Across any vocational domain, recruitment data suffers from the same structural issues:
1. Title Fragmentation: Different employers use different titles for the same core role. Without standardization, it's impossible to build a stable taxonomy or compare roles across organizations.
2. Capability Opacity: Competency requirements are buried in unstructured JD text, mixed with noise (salary, benefits, promotional language). Abstract descriptions like "good communication skills" cannot be directly mapped to educational outcomes.
3. No Shared Ontology: Unlike mature professions with established occupational standards, most vocational fields lack a structured job-skill ontology that bridges market language and educational frameworks.
4. No Feedback Loop: Even when market analysis is done manually, findings cannot be systematically fed back into curriculum design, course planning, or teaching evaluation.
Why Traditional NLP Fails
- Keyword-based approaches cannot handle the contextual reasoning required: domain-specific slang vs academic terminology, implicit skill requirements, and the need to transform raw JD language into measurable educational competency statements.
## Solution Architecture
### Core Design Principle
Strict separation between domain-agnostic infrastructure (reusable across any program) and domain-specific configuration (swapped per program). Adding a new vocational discipline requires only changing the configuration — not rebuilding the system.
#### Architecture Separation Diagram
```
┌────────────────────────────────────────────────────────┐
│  Domain Configuration (per program)                     │
│  • Capability standards                                 │
│  • Terminology dictionary                               │
│  • Data sources & keywords                              │
│            ▲ SWAP THIS LAYER PER PROGRAM ▲              │
├────────────────────────────────────────────────────────┤
│  Domain-Agnostic Infrastructure                         │
│  • AI Agent pipeline (4-stage)                          │
│  • Dual identifier system (A-code / B-code)             │
│  • Capability graph schema (3-tier)                     │
│  • Orchestration engine                                 │
└────────────────────────────────────────────────────────┘
```
#### 4-Stage Analytical Pipeline
```
Stage 1              Stage 2              Stage 3               Stage 4
Framework            Data                 Mapping &             Analysis &
Construction         Preparation          Association           Application

National/Intl.  →    Multi-platform  →    JD capability    →    Capability radar
standards            JD ingestion,        items matched         per direction;
build initial        cleaning &           to std. units;        teaching & market
capability           standardization      association           insight reports
framework                                 matrix built
     ↑                                         │
     └──── Framework dynamic update loop ──────┘
```
#### Key Design Components
Dual Identifier System: A-code tags every original JD; B-code maps to standardized positions. This preserves data lineage for weight computation, continuous updates, and root-cause tracing — and works identically across any domain.
3-Step AI Semantic Reasoning: Decomposed into three focused agents rather than one monolithic LLM call, enabling independent optimization:
1. Role Normalization — map diverse titles to canonical roles
2. Capability Extraction — extract structured elements: Context + Action + Measurable Outcome + Constraints
3. Skill Deduplication & Weighting — merge equivalent skills, compute frequency-based weights
#### 3-Tier Capability Graph Schema
Universal schema referenced from national vocational standards, WorldSkills, and OBE methodology:
The capability graph follows a 3-tier schema (Work Tasks → Capability Definition → Teaching Support) referencing national vocational standards, 
WorldSkills, and OBE methodology. The detailed framework was developed by the Capability Graph team.
## Pilot: Medical Aesthetics
Selected as the first pilot due to extreme title fragmentation, rapid market evolution, and critical medical/non-medical compliance boundaries. Results:
1. 388 JDs processed from major recruitment platforms
2. 6 standardized role categories identified
3. 18 capability modules defined across roles
4. Interactive knowledge graph, skill frequency analysis, and professional fit radar generated
## About the Partners
A Better Community (ABC) — Founded in 2008, ABC is China's first social enterprise that mobilizes professional volunteers to provide management consulting for social organizations. With 6 chapters (Beijing, Shanghai, Chengdu, Shenzhen, Guangzhou, Hangzhou), ABC has engaged 3,100+ professional volunteers across 300+ consulting projects in education, environment, social services, and more.
Polus International College — Est. 1993. 5 schools, 50 programs, 17,000+ students, 60,000+ graduates, 97%+ employment rate. China's only private provincial-level demonstration vocational college.
## License
MIT License — see LICENSE.

