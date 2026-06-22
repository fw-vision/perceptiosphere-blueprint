# Agents — Perceptiosphere Registry

> This is the living index of all agents in your Perceptiosphere instance. Start with the two included agents, then expand the fleet as your needs evolve using the FORGE process.
>
> **Maintained by:** Chief of Staff (COS)

---

## Model Tiers

| Tier | Use Case | Cost Profile |
|------|----------|-------------|
| **Tier 1** | Reasoning, planning, orchestration ONLY | High (use sparingly) |
| **Tier 2** | Writing, research, analysis, review | Medium |
| **Tier 2C** | Code generation ONLY | Medium |
| **Tier 3** | Scanning, metadata, formatting | Low |

---

## Included Agents

| Agent | Subagent Key | Tier | Prompt | Role |
|-------|-------------|------|--------|------|
| **Chief of Staff (COS)** | `reasoning` / `plan` | 1 | `00_Protocol/Agents/prompts/cos.md` | Orchestrator: delegates, synthesises, tracks credibility |
| **Researcher** | `researcher` | 2 | `00_Protocol/Agents/prompts/researcher.md` | External research with proper source filing and credibility tiers |

### Core Workflows

- **Research Loop:** COS scopes brief → Researcher dispatched → Report in `01_Inflow/AI_Research/` → COS processes findings into Sandbox atoms
- **Credibility Loop:** COS tracks `principal_reviews` when you validate notes; Sources increment `source_citations` on referenced Cards
- **Promotion Loop:** COS identifies high-credibility collective-worthy notes → recommends Curated promotion → you approve

---

## Expanding Your Fleet

The Perceptiosphere is designed for fleet growth. When you identify a recurring task that should be delegated:

1. **Flag** the need (FORGE: F)
2. **Orient** by checking if an existing agent could handle it (FORGE: O)
3. **Refine** a new prompt in `00_Protocol/Agents/prompts/` (FORGE: R)
4. **Gate** — review and approve the new agent (FORGE: G)
5. **Execute** — add it to this registry and your `opencode.json` (FORGE: E)

### Common Agents to Add

| Agent | Role | When to Add |
|-------|------|-------------|
| **Librarian** | Decomposes raw input into ACCESS atoms | When you have consistent inflow to process |
| **Reflector** | Identifies patterns and promotion candidates | When your Sandbox has 50+ atoms |
| **Writer** | Creates content from knowledge atoms | When you publish regularly |
| **Critic** | Reviews and improves drafts | When quality matters for external output |
| **Transcript Analyst** | Processes meeting recordings | When you record meetings |
| **Journal** | Synthesises voice notes | When you use voice capture |
| **Privacy Auditor** | Scans for PII before sharing | When you share knowledge externally |
| **Coder** | Implements technical projects | When you build software |

---

## Brand Contexts

Agents load brand voice dynamically via `.brand/context.md` files:

| Organisation | Path | Domain |
|-------------|------|--------|
| {{ORG_1}} | `04_Efforts/{{ORG_1}}/.brand/context.md` | {{description}} |

<!--
  Replace the table above with YOUR organisations.
  Each org should have a .brand/context.md file.
  See 04_Efforts/.brand/context.sample.md for the template.
-->

---

## Configuration

- **Master config:** `./opencode.json` (created from `opencode.json.sample`)
- **Prompt directory:** `00_Protocol/Agents/prompts/`
- **Template directory:** `00_Protocol/Templates/`
- **Schema directory:** `00_Protocol/Schema/`
