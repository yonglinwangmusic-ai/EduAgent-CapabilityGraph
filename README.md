# VocAI-JobGraph: AI Agent Architecture for Vocational Education Capability Graph Construction
An open-source system architecture that uses vertical AI Agents to transform fragmented recruitment data into structured, standardized capability graphs for vocational education programs. Designed to be domain-agnostic and scalable across any vocational discipline — piloted with medical aesthetics as the first case study. Built as a pro-bono technology consulting project for A Better Community (ABC), a nonprofit empowering underrepresented communities through workforce development.

# About This Repository
This repository documents the system architecture and solution design I created as a volunteer technology consultant for ABC's vocational education AI initiative, in partnership with Polus International College (四川国际标榜职业学院).
The college operates 5 schools, 50 programs, 17,000+ enrolled students, and ~600 faculty members, with a 30-year track record of producing 60,000+ graduates at a 97%+ employment rate — the only private provincial-level demonstration vocational college in China. Yet like most vocational institutions, it faces a fundamental challenge: how to systematically align 50 diverse curricula with rapidly evolving market demands — a process that currently requires months of manual effort per program with no structured data pipeline.
This project represents the 0-to-1 cold start — designing a universal AI Agent architecture that can be applied program-by-program, starting from a single pilot and scaling to full institutional coverage. We selected medical aesthetics as the first pilot due to its high market fragmentation and urgent curriculum alignment needs.
I served as the Solution Architect, responsible for:

Designing the domain-agnostic AI Agent pipeline architecture that can be replicated across any vocational discipline
Creating the 4-stage analytical framework: Framework Construction → Data Preparation → Mapping & Association → Analysis & Application
Specifying the dual-layer unique identifier system (A-code / B-code) for data lineage and traceability
Defining the 3-step AI semantic reasoning approach for role normalization, capability extraction, and skill deduplication
Designing the capability graph schema referencing national vocational standards, WorldSkills standards, and OBE methodology
Planning the phased rollout strategy: single-program pilot → methodology validation → multi-program scaling

The implementation was carried out by the project team based on this architecture, using Coze (ByteDance) as the agent orchestration platform.

# The Problem
China's vocational education system is undergoing rapid transformation. Institutions like Polus International College must continuously align their curricula with market demand across dozens of programs — but the current process is entirely manual, slow, and unscalable:

Scale: 50 programs × hundreds of relevant job types = thousands of JDs to analyze, with no automated pipeline
Manual bottleneck: A single program's curriculum alignment takes 2+ months of expert review; full institutional coverage (5,000+ course-level reviews) is practically impossible
Teacher quality variance: Among ~600 faculty, teaching quality varies; standardized capability benchmarks are needed but don't exist in structured, data-driven form
JD fragmentation: Across any vocational domain, job descriptions are inconsistent — different titles for the same role, vague skill requirements, noise data obscuring real competency needs
No feedback loop: Even when market analysis is done manually, there's no systematic mechanism to feed findings back into curriculum design

Traditional keyword-based NLP approaches fail because job semantics require deep contextual reasoning — especially in specialized vocational domains where market slang, academic terminology, and regulatory language coexist.

# Solution: A Universal Architecture
The architecture strictly separates domain-agnostic infrastructure (pipeline, identifier system, agent orchestration, graph schema) from domain-specific configuration (capability standards, terminology dictionaries, data sources). Switching from medical aesthetics to automotive technology or early childhood education requires only swapping the configuration layer — not rebuilding the system.
## Core Design Principle

┌──────────────────────────────────────────────────────────────────┐
│                    Domain Configuration Layer                     │
│                                                  │
│  ┌──────────────┐ ┌──────────────┐ ┌────────────────────────┐    │
│  │ Capability   │ │ Terminology  │ │ Data Sources           │    │
│  │ Standards    │ │ Dictionary   │ │ & Keywords             │    │
│  │   │ │       │ │                     │    │
│  └──────────────┘ └──────────────┘ └────────────────────────┘    │
│                    ▲ SWAP THIS LAYER PER PROGRAM ▲               │
├──────────────────────────────────────────────────────────────────┤
│                 Domain-Agnostic Infrastructure                    │
│                   (领域无关基础设施)                                │
│                                                                   │
│  ┌─ Agent Pipeline ──────────────────────────────────────────┐   │
│  │ Ingestion → Cleaning → Normalization → Extraction →       │   │
│  │ Deduplication → Weight Computation → Graph Generation     │   │
│  └───────────────────────────────────────────────────────────┘   │
│  ┌─ Identifier System ──┐  ┌─ Graph Schema ────────────────┐   │
│  │ A-Code (raw JD)       │  │ Typical Tasks → Capability    │   │
│  │ B-Code (std. position)│  │ Modules → Standards → Levels  │   │
│  └───────────────────────┘  └───────────────────────────────┘   │
│  ┌─ Orchestration ──────────────────────────────────────────┐   │
│  │ Coze Workflow Engine + LLM Routing + State Management     │   │
│  └───────────────────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────────┘
## Phased Rollout Strategy
Phase 0 (This Project)          Phase 1                    Phase 2
本项目 — 0→1 冷启动              方法论验证                  规模化推广

┌─────────────────┐      ┌─────────────────┐      ┌─────────────────┐
│ 1 Pilot Program │      │ 3-5 Programs    │      │ 50 Programs     │
│ 医美专业试点      │─────→│ Cross-domain    │─────→│ Full Coverage   │
│                 │      │ validation      │      │ 全校覆盖         │
│ • Architecture  │      │ 跨学科验证       │      │                 │
│   design        │      │                 │      │ • Automated     │
│ • Pipeline      │      │ • Refine config │      │   pipeline      │
│   validation    │      │   switching     │      │ • Continuous    │
│ • 388 JDs →     │      │ • Optimize      │      │   market        │
│   6 std. roles  │      │   prompts       │      │   tracking      │
│ • Proof of      │      │ • Build shared  │      │ • Curriculum    │
│   concept       │      │   components    │      │   auto-update   │
└─────────────────┘      └─────────────────┘      └─────────────────┘

# Architecture Details
## 4-Layer System Architecture
┌─────────────────────────────────────────────────────────────┐
│  Layer 1: User Interaction & Input / 用户交互与输入层           │
│  ┌──────────┐  ┌──────────┐  ┌─────────────────────────┐   │
│  │ Excel    │  │ Web      │  │ Coze Workflow Trigger    │   │
│  │ Upload   │  │ Search   │  │ + Knowledge Graph View   │   │
│  └──────────┘  └──────────┘  └─────────────────────────┘   │
├─────────────────────────────────────────────────────────────┤
│  Layer 2: Orchestration & Scheduling / 编排与调度层            │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Coze Workflow Engine                                 │   │
│  │  ├── Context Pipeline    ├── Task Router              │   │
│  │  └── State Monitor       └── Parallel Loop Control    │   │
│  └──────────────────────────────────────────────────────┘   │
├─────────────────────────────────────────────────────────────┤
│  Layer 3: LLM Agent Collaboration / LLM智能体协作层           │
│  Semantic Cleaning → Filter & A-Code → Role Std. →          │
│  Data Split → Subgraph Agents → Graph Merge →               │
│  Skill Weight → Graph Viz → Viz Config → HTML Upload        │
├─────────────────────────────────────────────────────────────┤
│  Layer 4: Infrastructure & Storage / 基础设施与存储展现层       │
│  Temp Data Store  ←→  Web Assembly + HTML  ←→  Object Store │
└─────────────────────────────────────────────────────────────┘
## 4-Stage Analytical Pipeline
Stage 1 — Framework Construction (框架构建)
Input national/international vocational standards → Build initial capability framework with standard unit library and keyword anchor database.
Stage 2 — Data Preparation (数据准备)
Ingest multi-platform JDs → Clean, structure, and standardize using anchor-point matching → Output structured JD database.
Stage 3 — Mapping & Association (映射与关联, core stage)
Core matching logic: map JD capability items → standard capability units, via exact match (validate), refinement (enrich), or new tagging (iterate framework). Output: association matrix linking every JD to capability units. Framework dynamic update loop feeds back to Stage 1.
Stage 4 — Analysis & Application (分析与应用)
Aggregate analysis to generate capability radar by direction + teaching & market insight reports.

# Design Decisions
Why Vertical AI Agents over Traditional NLP?
Every vocational domain has colloquial terminology diverging from textbook language — requiring LLM contextual reasoning, not pattern matching. JD texts mix structured requirements with promotional noise. Capability descriptions are abstract and need transformation into measurable competency statements aligned with Bloom's Taxonomy (L1–L4). Vertical AI Agents deploy specialized LLM reasoning at each pipeline stage with domain-specific prompts that can be swapped per program.
Why Dual Identifier System (A-Code / B-Code)?
The A-code preserves every original JD's lineage; the B-code maps it to a standardized position. This enables weight computation, continuous updates without losing historical mappings, and root-cause analysis. This mechanism is domain-agnostic — it works identically across any vocational field.
Why 3-Step AI Semantic Understanding?
A single LLM call attempting simultaneous title normalization, capability extraction, and skill deduplication produces unreliable results. Decomposing into three focused agents allows independent optimization: (1) Role Normalization Agent, (2) Capability Extraction Agent (Context + Action + Measurable Outcome + Constraints), (3) Skill Deduplication & Weighting Agent.

# Capability Graph Schema
Three-Tier Framework (Universal) 















