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
┌────────────────────────────────────┐
│  Domain Configuration (per program)│
│  • Capability standards│
│  • Terminology dictionary│
│  • Data sources & keywords│
│            ▲ SWAP THIS LAYER PER PROGRAM ▲│
├───────────────────────────────────────────┤
│  Domain-Agnostic Infrastructure│
│  • AI Agent pipeline (4-stage)│
│  • Dual identifier system (A-code / B-code)│
│  • Capability graph schema (3-tier)│
│  • Orchestration engine │
└────────────────────────────────────────────┘

## Pilot: Medical Aesthetics

## About the Partners

## License
MIT License — see LICENSE.

