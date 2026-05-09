# VocAI-JobGraph: AI Agent Architecture for Vocational Education Capability Graph Construction
An open-source system architecture that uses vertical AI Agents to transform fragmented recruitment data into structured, standardized capability graphs for vocational education programs. Designed to be domain-agnostic and scalable across any vocational discipline — piloted with medical aesthetics as the first case study. Built as a pro-bono technology consulting project for A Better Community (ABC), a nonprofit empowering underrepresented communities through workforce development.

## About This Repository
This repository documents the system architecture and solution design I created as a volunteer technology consultant for ABC's vocational education AI initiative, in partnership with Polus International College.
The college operates 5 schools, 50 programs, 17,000+ enrolled students, and ~600 faculty members, with a 30-year track record of producing 60,000+ graduates at a 97%+ employment rate — the only private provincial-level demonstration vocational college in China. Yet like most vocational institutions, it faces a fundamental challenge: how to systematically align 50 diverse curricula with rapidly evolving market demands — a process that currently requires months of manual effort per program with no structured data pipeline.
This project represents the 0-to-1 cold start — designing a universal AI Agent architecture that can be applied program-by-program, starting from a single pilot and scaling to full institutional coverage. We selected medical aesthetics as the first pilot due to its high market fragmentation and urgent curriculum alignment needs.

I served as the Solution Architect, responsible for:
- Designing the domain-agnostic AI Agent pipeline architecture that can be replicated across any vocational discipline
- Creating the 4-stage analytical framework: Framework Construction → Data Preparation → Mapping & Association → Analysis & Application
- Specifying the dual-layer unique identifier system (A-code / B-code) for data lineage and traceability
- Defining the 3-step AI semantic reasoning approach for role normalization, capability extraction, and skill deduplication
The implementation was carried out by the project team based on this architecture, using Coze (ByteDance) as the agent orchestration platform.

## The Problem
China's vocational education system is undergoing rapid transformation. Institutions like Polus International College must continuously align their curricula with market demand across dozens of programs — but the current process is entirely manual, slow, and unscalable:
- **Scale:** 50 programs × hundreds of relevant job types = thousands of JDs to analyze, with no automated pipeline
Manual bottleneck: A single program's curriculum alignment takes 2+ months of expert review; full institutional coverage (5,000+ course-level reviews) is practically impossible
- **Teacher quality variance:** Among ~600 faculty, teaching quality varies; standardized capability benchmarks are needed but don't exist in structured, data-driven form
- **JD fragmentation:** Across any vocational domain, job descriptions are inconsistent — different titles for the same role, vague skill requirements, noise data obscuring real competency needs
- **No feedback loop:** Even when market analysis is done manually, there's no systematic mechanism to feed findings back into curriculum design
Traditional keyword-based NLP approaches fail because job semantics require deep contextual reasoning — especially in specialized vocational domains where market slang, academic terminology, and regulatory language coexist.

## Solution: A Universal Architecture
The architecture strictly separates domain-agnostic infrastructure (pipeline, identifier system, agent orchestration, graph schema) from domain-specific configuration (capability standards, terminology dictionaries, data sources). Switching from medical aesthetics to automotive technology or early childhood education requires only swapping the configuration layer — not rebuilding the system.
### Core Design Principle














