# Perceptiosphere Blueprint

[![License: CC BY-SA 4.0](https://img.shields.io/badge/Content-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![License: MIT](https://img.shields.io/badge/Config-MIT-blue.svg)](https://opensource.org/licenses/MIT)

An **AI-native cognitive operating system** for domain experts who need to transform information overload into structured, credible knowledge through teamed AI agents.

The Perceptiosphere is not a note-taking app. It is a framework for building a **Hybrid Intelligence partnership** between you and a fleet of AI agents, each with a defined role in your cognitive workflow.

---

## What This Blueprint Gives You

This repository is the **open starter kit**. It provides the core principles, folder scaffolding, and two foundational agent prompts to get you running:

| Included | What It Does |
|----------|-------------|
| **CORE Process** | The 4-stage cognitive metabolism (Collect, Organize, Reflect, Execute) |
| **ACCESS Taxonomy** | 6-category knowledge classification system |
| **FORGE Evolution** | How your agent fleet evolves over time |
| **Credibility Scoring** | AI-augmented knowledge quality tracking |
| **COS Agent** | The orchestrator that delegates and synthesises |
| **Researcher Agent** | Demonstrates how sources are filed with proper credibility tiers |
| **Templates** | Obsidian-ready frontmatter for every atom type |
| **Folder scaffolding** | Git-tracked system layer + gitignored knowledge layer |

---

## The CORE Process

Information moves through four metabolic stages:

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   COLLECT   │───▶│  ORGANIZE   │───▶│   REFLECT   │───▶│   EXECUTE   │
│  (Inflow)   │    │  (Sandbox)  │    │  (Curated)  │    │  (Efforts)  │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
  Raw signals       AI decomposition    Human curation     Projects &
  from environment  into atoms          for collective     outputs
                                        sharing
```

1. **Collect** — Ingest raw signals: articles, transcripts, voice notes, web clips
2. **Organize** — AI agents decompose material into semantic atoms using the ACCESS taxonomy
3. **Reflect** — Credibility scoring tracks knowledge maturity; validated knowledge can be curated for collective sharing
4. **Execute** — Transform knowledge into projects, publications, and decisions

---

## The ACCESS Taxonomy

Every knowledge atom is classified into one of six categories:

| Category | Description | Folder |
|----------|-------------|--------|
| **A**tlas | Discovery layer: maps, indexes, navigation | `Atlas/` |
| **C**ards | Atomic concepts, patterns, and claims | `Cards/` |
| **C**alendar | Time-bound events, meetings, decisions | `Calendar/` |
| **E**cosystem | People, organisations, and roles | `Ecosystem/` |
| **S**ources | Citation records with credibility tiers (T1-T4) | `Sources/` |
| **S**paces | Domain containers with agent skills and MOCs | `Spaces/` |

### Source Credibility Tiers

| Tier | Label | Examples |
|------|-------|----------|
| **T1** | Primary/Empirical | Peer-reviewed papers, theses, datasets, standards |
| **T2** | Authoritative | Books, institutional reports, book chapters |
| **T3** | Professional | Blogs, articles, talks, courses, presentations |
| **T4** | Signal | AI-generated summaries, social media, unverified |

---

## The Credibility Scoring System

Instead of manually promoting files between folders, the Perceptiosphere tracks knowledge quality as a **computed score** based on three signal types, weighted by authority.

```yaml
credibility:
  principal_reviews: 0      # Human validations (weight: 5x)
  source_citations: 0       # Real-world source cross-references (weight: 3x)
  agent_validations: 0      # AI agent cross-validations (weight: 1x)
  level: seed               # Auto-computed from weighted score
```

### Level Computation

```
score = (principal_reviews x 5) + (source_citations x 3) + (agent_validations x 1)
```

| Score | Level | Meaning |
|-------|-------|---------|
| 0 | seed | Untouched since creation |
| 1-4 | emerging | Some engagement, not yet reliable |
| 5-14 | reviewed | Curator or sources have engaged meaningfully |
| 15-29 | validated | Strong confidence; multiple signals converge |
| 30+ | canonical | Foundational knowledge; heavily cited and reviewed |

**Key insight:** This system lets you use AI agents to expand your cognitive reach while maintaining a clear signal of what you can actually trust. A note validated by you once (5 points) outweighs five agent cross-validations (5 points). Real-world citations add weight without requiring your time. The system scales your attention.

---

## The FORGE Evolution Process

Your agent fleet is not static. FORGE governs how agents evolve:

| Phase | Action |
|-------|--------|
| **F**lag | An agent or Principal identifies a gap, friction, or improvement opportunity |
| **O**rient | COS contextualises the issue within the broader system |
| **R**efine | Propose a specific change (new agent, prompt revision, schema update) |
| **G**ate | Principal reviews and approves/rejects |
| **E**xecute | Change is implemented, versioned, and logged |

This means your system improves with use. Agents that don't work get revised. New agents get added when roles emerge. The protocol tracks every change.

---

## Multi-Agent Architecture

The system uses a **Chief of Staff (COS)** at the top, delegating to specialist agents:

```
                    ┌──────────────────┐
                    │  Chief of Staff  │  (Tier 1 — Reasoning)
                    │   Orchestrator   │
                    └────────┬─────────┘
                             │
         ┌───────────────────┼───────────────────┐
         │                   │                   │
    ┌────▼────┐       ┌─────▼─────┐      ┌─────▼─────┐
    │Knowledge│       │Operations │      │  Output   │
    │  Core   │       │  Support  │      │ Creation  │
    └────┬────┘       └─────┬─────┘      └─────┬─────┘
         │                  │                   │
    Researcher         (your agents)        (your agents)
    (included)         (you define)         (you define)
```

This Blueprint includes the **COS** and **Researcher** prompts. The COS shows you how orchestration works. The Researcher shows how knowledge enters the system with proper sourcing. You build the rest of the fleet based on your needs.

### Model Tiers

| Tier | Use Case | Cost Profile |
|------|----------|-------------|
| **Tier 1** | Reasoning, planning, orchestration | High (use sparingly) |
| **Tier 2** | Writing, research, analysis | Medium |
| **Tier 2C** | Code generation | Medium |
| **Tier 3** | Scanning, metadata, formatting | Low |

---

## Repository Structure

```
perceptiosphere/
├── 00_Protocol/                 ← System blueprint (tracked by Git)
│   ├── Agents/prompts/          Agent system prompts (COS + Researcher)
│   ├── Schema/                  Knowledge taxonomy definitions
│   └── Templates/               Obsidian frontmatter templates
│
├── 01_Inflow/                   ← Raw inputs (NOT tracked)
│   ├── Inbox/                   Web clips, articles, PDFs
│   ├── AI_Research/             AI-generated research reports
│   └── Journal/                 Voice notes, daily reflections
│
├── 02_Sandbox/                  ← AI working knowledge (NOT tracked)
│   ├── Atlas/                   Maps of Content, navigation
│   ├── Cards/                   Concepts, patterns, claims
│   ├── Calendar/                Meetings, events, milestones
│   ├── Ecosystem/               People, organisations, roles
│   ├── Sources/                 Citation records (T1-T4 subfolders)
│   └── Spaces/                  Domain containers with skills
│
├── 03_Curated/                  ← Collective knowledge mesh (NOT tracked)
│   ├── Atlas/                   Published navigation
│   ├── Cards/                   Validated, shareable concepts
│   ├── Calendar/                Public meeting minutes, event reviews
│   ├── Ecosystem/               Published network maps
│   ├── Sources/                 Curated bibliography
│   └── Spaces/                  Published domain collections
│
├── 04_Efforts/                  ← Active projects (NOT tracked)
│   └── .brand/                  Brand context files
│
├── AGENTS.md                    Agent registry
├── opencode.json.sample         Starter config
└── .gitignore                   Tracks only Protocol layer
```

**Git tracks only the Protocol layer.** Your knowledge stays local and sovereign.

---

## Getting Started

See **[SETUP.md](./SETUP.md)** for the full installation guide.

Quick start:
1. Clone or fork this repository
2. Copy `opencode.json.sample` → `opencode.json` and fill in your model endpoints
3. Open in Obsidian
4. Drop material into `01_Inflow/Inbox/` and invoke the COS

---

## Going Deeper

This Blueprint gives you the framework. The full Perceptiosphere implementation includes:

- **Complete agent fleet** (15+ specialist agents for writing, critique, strategy, privacy, transcription)
- **FORGE governance system** with proposal workflows and version tracking
- **Neo4j graph integration** for deep network analysis and embeddings
- **Multi-brand coordination** patterns for managing multiple organisations
- **Playbooks** for specific workflows (research coordination, content publishing, annotation systems)
- **Space skills system** for domain-specific agent orientation

These are available through consulting, the forthcoming book, and the FW.VISION community.

**Learn more:** [fw.vision](https://fw.vision) | [findcongwang.com](https://findcongwang.com)

---

## Licence

- **Content** (prompts, schemas, templates, documentation): [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
- **Configuration and code**: [MIT](https://opensource.org/licenses/MIT)

---

## Origin

The Perceptiosphere was developed by [Francis Wang](https://findcongwang.com) as part of doctoral research into hybrid intelligence and the future of knowledge work. It is maintained as an open framework through [FW.VISION](https://fw.vision).
