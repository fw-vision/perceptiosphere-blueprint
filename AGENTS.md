# Agents — Perceptiosphere Registry

> This is the living index of all agents available in this Perceptiosphere instance. It maps each agent to its functional unit, model tier, prompt file, and current implementation status.
>
> **Maintained by:** Chief of Staff (COS)  
> **Architecture plan:** See `docs/plans/` for implementation notes

---

## Model Tiers

| Tier | Use Case | Cost Profile |
|------|----------|-------------|
| **Tier 1** | Reasoning, planning, orchestration ONLY. Never for heavy writing/reading. | High |
| **Tier 2** | General writing, research, analysis, review, prose output | Low-Medium |
| **Tier 2C** | Code generation ONLY | Low-Medium |
| **Tier 2.5** | Light structured tasks, fast navigation, extraction | Low |
| **Tier 3** | Fast scanning, metadata, formatting | Lowest |

---

## Team 1: Knowledge Core

> The foundational agents that power the CORE metabolic cycle (Collect, Organize, Reflect, Execute).

| Agent | Subagent Key | Tier | Prompt | Status |
|-------|-------------|------|--------|--------|
| **Chief of Staff (COS)** | `reasoning` / `plan` | 1 | `00_Protocol/Agents/prompts/cos.md` | Active |
| **Librarian** | `librarian` | 2 | `00_Protocol/Agents/prompts/librarian.md` | Active |
| **Discovery Researcher** | `researcher` | 2 | `00_Protocol/Agents/prompts/discovery-researcher.md` | Active |
| **Structural Reflector** | `reflector` | 2 | `00_Protocol/Agents/prompts/structural-reflector.md` | Active |

### Workflows

- **Ingestion Loop:** `01_Inflow/Inbox/` or `01_Inflow/AI_Research/` → Librarian detects source type → decomposes into `02_Sandbox/` (ACCESS atoms) → files Source note in `Sources/{T1_Primary|T2_Authoritative|T3_Professional|T4_Signal}/` → archives original to `_Archived/Raws/`
- **Source Enrichment Loop:** Librarian creates stub Sources (`status: stub`, `enrichment_needed: true`) → COS batches enrichment requests → Researcher fills metadata (DOI, ISBN, URL, publisher) → status promoted to `seed`
- **Research Loop:** COS scopes brief → Researcher dispatched → Report in `01_Inflow/AI_Research/` → Librarian processes as `ai-synthesis` + traces upstream primary sources
- **Reflection Loop:** Reflector scans `02_Sandbox/` → Curation proposals → Principal approves → `03_Curated/`
- **Meta Loop (Agents Building Agents):** Researcher investigates role → Librarian decomposes → COS drafts new prompt → Principal approves

---

## Team 2: Operations Support

> Daily operations, transcript processing, and security agents.

| Agent | Subagent Key | Tier | Prompt | Status |
|-------|-------------|------|--------|--------|
| **Executive Assistant (EA)** | — | 2.5 | `00_Protocol/Agents/prompts/executive-assistant.md` | Planned |
| **Daily Journal** | `journal` | 2.5 | `00_Protocol/Agents/prompts/daily-journal.md` | Planned |
| **Transcript Analyst** | `transcript` | 2.5 | `00_Protocol/Agents/prompts/transcript-analyst.md` | Planned |
| **Privacy Auditor** | `privacy` | 3 | `00_Protocol/Agents/prompts/privacy-auditor.md` | Planned |

### Workflows

- **Meeting Flow:** Recording → Transcript Analyst extracts decisions/actions → EA populates calendar + tasks
- **Journal Flow:** Voice notes → Daily Journal synthesizes → deposits in `01_Inflow/` → Librarian processes
- **Privacy Flow:** Privacy Auditor scans `02_Sandbox/` → flags PII → redacts before Collective sync

---

## Team 3: Research & Content Output

> Content creation, critique, and technical implementation agents.

| Agent | Subagent Key | Tier | Prompt | Status |
|-------|-------------|------|--------|--------|
| **Review Critic** | `critic` | 2 | `00_Protocol/Agents/prompts/review-critic.md` | Planned |
| **Content Strategist** | `strategist` | 2 | `00_Protocol/Agents/prompts/content-strategist.md` | Planned |
| **Content Writer** | `writer` | 2 | `00_Protocol/Agents/prompts/content-writer.md` | Active |
| **SEO/AEO Specialist** | — | 3 | `00_Protocol/Agents/prompts/seo-specialist.md` | Planned |
| **Software Architect** | — | 1 | `00_Protocol/Agents/prompts/software-architect.md` | Planned |
| **Coder** | `coder` | 2C | `00_Protocol/Agents/prompts/coder.md` | Active |

### Workflows

- **Content Flow:** COS loads `.brand/context.md` → Strategist plans → Writer drafts → Critic reviews → Principal approves
- **Code Flow:** Software Architect plans → Coder implements → tests pass → Principal reviews

---

## Team 4: Governance & Strategy

> Specialized domain agents for foresight, policy, and brand governance.

| Agent | Subagent Key | Tier | Prompt | Status |
|-------|-------------|------|--------|--------|
| **Foresight Analyst** | — | 1 | `00_Protocol/Agents/prompts/foresight-analyst.md` | Planned |
| **Policy Advisor** | — | 1 | `00_Protocol/Agents/prompts/policy-advisor.md` | Planned |
| **Brand Guardian** | — | 2 | `00_Protocol/Agents/prompts/brand-guardian.md` | Planned |

### Workflows

- **Foresight Flow:** COS briefs → Foresight Analyst applies futures methodology → scenario outputs → Librarian decomposes
- **Brand Audit Flow:** Brand Guardian scans recent content → drift report → COS flags for Principal

---

## Brand Contexts

> Agents load brand voice dynamically via `.brand/context.md` files stored with each organization.

| Organization | Path | Domain |
|-------------|------|--------|
| {{ORG_1}} | `04_Execute_Efforts/{{ORG_1}}/.brand/context.md` | {{description}} |
| {{ORG_2}} | `04_Execute_Efforts/{{ORG_2}}/.brand/context.md` | {{description}} |

<!--
  Replace the table above with YOUR organizations.
  Each org should have a .brand/context.md file.
  See 04_Execute_Efforts/.brand/context.sample.md for the template.
-->

---

## Configuration

- **Master config:** `./opencode.json` (created from `opencode.json.sample`)
- **Prompt directory:** `00_Protocol/Agents/prompts/`
- **Template directory:** `00_Protocol/Templates/`
- **Research directory:** `00_Protocol/Research/` (Output-Templates/ + Investigation-Prompts/)
- **Schema directory:** `00_Protocol/Schema/`

---

## Workspace Layout

> The Perceptiosphere vault is an Obsidian vault. Code repositories can live as **sibling folders** in the same parent directory, each with their own git history.

```
~/work/                              (or your preferred workspace root)
├── my-perceptiosphere/              ← This vault
│   ├── 00_Protocol/                 System blueprints, agents, schemas
│   ├── 01_Collect_Inflow/           Raw inputs (Inbox, Clips, Journal, AI_Research)
│   ├── 02_Organize_Sandbox/         AI-decomposed atoms (ACCESS)
│   ├── 03_Reflect_Curated/          Validated knowledge mesh
│   ├── 04_Execute_Efforts/          Brand contexts and effort plans
│   ├── _Archived/                   Processed raw files
│   └── .obsidian/                   Vault config
│
├── my-project-a/                    ← Git repo: project A
├── my-project-b/                    ← Git repo: project B
└── experiments/                     ← Git repo: sandbox projects
```

### Convention for Agents

- **Brand context:** `04_Execute_Efforts/{ORGNAME}/.brand/context.md` (inside vault)
- **Code repos:** `../{ORGNAME}/` relative to vault root (sibling folder)
- **Inflow sources:** `01_Collect_Inflow/Inbox/` (web clips), `01_Collect_Inflow/Journal/` (voice notes)
