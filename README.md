# Perceptiosphere (P-Sphere)

[![License: CC BY-SA 4.0](https://img.shields.io/badge/Content-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![License: MIT](https://img.shields.io/badge/Config-MIT-blue.svg)](https://opensource.org/licenses/MIT)

An **AI-native cognitive operating system** for managing high-velocity information through teamed AI agents, forming Hybrid Intelligence (HI) partnerships.

The Perceptiosphere is built for domain experts who require a sovereign, structured method for transforming environmental noise into actionable knowledge. It rejects the passivity of standard AI tools in favour of an active, agent-driven approach to personal knowledge management.

---

## The CORE Methodology

The P-Sphere functions as a metabolic process for cognition. Information moves through four phases:

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   COLLECT   │───▶│  ORGANIZE   │───▶│   REFLECT   │───▶│   EXECUTE   │
│  (Inflow)   │    │  (Sandbox)  │    │  (Curated)  │    │  (Efforts)  │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
  Raw signals       AI decomposition    Human curation     Projects &
  from environment  into atoms          into knowledge     outputs
                                        mesh
```

1. **Collect** — Ingest raw signals: articles, transcripts, voice notes, web clips, RSS feeds
2. **Organize** — AI agents decompose material into semantic atoms using the ACCESS taxonomy
3. **Reflect** — Human operator curates validated insights into a permanent knowledge mesh
4. **Execute** — Transform reflected knowledge into projects, publications, and decisions

---

## The ACCESS Taxonomy

Knowledge atoms are classified into six categories:

| Category | Description | Folder |
|----------|-------------|--------|
| **A**rtifacts | Finalized outputs, drafts, deliverables | `Artifacts/` |
| **C**ards | Atomic concepts, patterns, and claims | `Cards/` |
| **C**alendar | Time-bound events, meetings, decisions | `Calendar/` |
| **E**cosystem | People, organizations, and roles | `Ecosystem/` |
| **S**ources | Citation records with credibility tiers | `Sources/` |
| **S**paces | Maps of Content (MOCs), dashboards | `Spaces/` |

Sources are further tiered by credibility:
- **T1 Primary** — Original research, patents, raw data
- **T2 Authoritative** — Peer-reviewed, established publishers
- **T3 Professional** — Industry reports, expert blogs, conference talks
- **T4 Signal** — Social media, news, AI-generated summaries

---

## Multi-Agent Architecture

The P-Sphere uses a **Chief of Staff (COS)** orchestrator that delegates to specialist subagents:

```
                    ┌──────────────────┐
                    │  Chief of Staff  │  (Tier 1 — Reasoning)
                    │   Orchestrator   │
                    └────────┬─────────┘
                             │
         ┌───────────────────┼───────────────────┐
         │                   │                   │
    ┌────▼────┐       ┌─────▼─────┐      ┌─────▼─────┐
    │ Team 1  │       │  Team 2   │      │  Team 3   │
    │Knowledge│       │Operations │      │  Output   │
    │  Core   │       │ Support   │      │ Research  │
    └────┬────┘       └─────┬─────┘      └─────┬─────┘
         │                  │                   │
    Librarian          Transcript          Writer
    Researcher         Journal             Critic
    Reflector          Privacy             Strategist
                                           Coder
```

### Model Tiers

The system assigns models by cognitive cost:

| Tier | Use Case | Example Models |
|------|----------|----------------|
| **Tier 1** | Reasoning, planning, orchestration ONLY | Claude Opus, GPT-4o |
| **Tier 2** | Writing, research, analysis, review | Claude Sonnet, Qwen3 80B |
| **Tier 2C** | Code generation ONLY | Qwen3 Coder, Claude Sonnet |
| **Tier 2.5** | Light structured tasks, fast navigation | Qwen3 32B, Gemini Flash |
| **Tier 3** | Scanning, metadata, formatting | GPT-4o-mini, small open models |

---

## Repository Structure

```
perceptiosphere/
├── 00_Protocol/                 ← System blueprint (tracked by Git)
│   ├── Agents/prompts/          Agent system prompts
│   ├── Schema/                  Knowledge taxonomy definitions
│   ├── Templates/               Obsidian frontmatter templates
│   ├── Research/                Research dispatch templates
│   └── Rituals/                 Daily/weekly workflow protocols
│
├── 01_Collect_Inflow/           ← Raw inputs (NOT tracked)
│   ├── Inbox/                   Web clips, articles, PDFs
│   ├── AI_Research/             AI-generated research reports
│   └── Journal/                 Voice notes, daily reflections
│
├── 02_Organize_Sandbox/         ← AI-decomposed atoms (NOT tracked)
│   ├── Cards/                   Concepts, patterns, claims
│   ├── Sources/                 Citation records (T1-T4)
│   ├── Ecosystem/               People, orgs, roles
│   ├── Calendar/                Meetings, events
│   ├── Artifacts/               Drafts, outputs
│   └── Spaces/                  MOCs, dashboards
│
├── 03_Reflect_Curated/          ← Validated knowledge (NOT tracked)
│   ├── Sovereign/               Private deep-context knowledge
│   └── Collective/              Shared/federated knowledge
│
├── 04_Execute_Efforts/          ← Active projects (NOT tracked)
│   └── .brand/                  Brand context files for each org
│
├── _Archived/Raws/              ← Processed originals (NOT tracked)
│
├── AGENTS.md                    Living agent registry
├── opencode.json                Your local config (from .sample)
├── opencode.json.sample         Annotated starter config
└── .gitignore                   Structure-only tracking firewall
```

**Git tracks only the Protocol layer** — your knowledge content stays local and sovereign.

---

## Getting Started

See **[SETUP.md](./SETUP.md)** for the full installation and configuration guide.

Quick start:
1. Clone or fork this repository
2. Copy `opencode.json.sample` → `opencode.json` and fill in your model endpoints
3. Point Obsidian at the root folder
4. Start the CORE cycle: drop material into `01_Collect_Inflow/Inbox/` and invoke the Librarian

---

## Licence

- **Content** (prompts, schemas, templates, documentation): [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
- **Configuration and code**: [MIT](https://opensource.org/licenses/MIT)

See [LICENSE](./LICENSE) for full details.

---

## Origin

The Perceptiosphere was developed by [Francis Wang](https://fcwang.com) as part of doctoral research into hybrid intelligence and the future of knowledge work. It is maintained as an open framework through [FW.VISION](https://fw.vision).
