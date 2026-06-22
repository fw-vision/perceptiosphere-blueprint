# ACCESS — Knowledge Atom Taxonomy

> **Origin:** Perceptiosphere Architecture  
> **Version:** 3.0 (revised 2026-06-21)  
> **Purpose:** Defines the six categories for organizing semantic atoms in the Sandbox and Curated Mesh.

---

## Overview

**ACCESS** is the taxonomic framework for classifying knowledge atoms within the Perceptiosphere. Every piece of decomposed information is filed into one of six categories, each with its own subfolder in `02_Sandbox/` and `03_Curated/`.

The two zones serve different purposes:

- **`02_Sandbox/`** — AI-autonomous working knowledge. All credibility levels coexist here. Agents create and modify freely. This is the cognitive workspace where ideas develop, get cross-referenced, and accumulate credibility over time.
- **`03_Curated/`** — Collective published knowledge mesh. Content here is curated for external sharing and community consumption. Promotion from Sandbox to Curated is a conscious decision.

Files use **wiki article titles** as filenames (e.g., `Compounding Content Systems.md`) for natural Obsidian linking. Classification lives in frontmatter — never in the filename.

---

## Naming Convention

All files use natural wiki article titles:

| Category | Example Filename | Wiki Link |
|----------|-----------------|-----------|
| Cards | `Compounding Content Systems.md` | `[[Compounding Content Systems]]` |
| Ecosystem (person) | `People/Larry Smith.md` | `[[Larry Smith]]` |
| Ecosystem (org) | `Organizations/Contently, Inc.md` | `[[Contently, Inc.]]` |
| Ecosystem (role) | `Roles/Editorial Director.md` | `[[Editorial Director]]` |
| Sources | `T2_Authoritative/Enterprise Publishing Taxonomy (Source).md` | `[[Enterprise Publishing Taxonomy (Source)]]` |
| Calendar (meeting) | `2026-05-15 Meeting — Innovation Ecosystems Strategy.md` | `[[2026-05-15 Meeting — Innovation Ecosystems Strategy]]` |
| Artifacts | `Content Team Operational Model.md` | `[[Content Team Operational Model]]` |

**Rules:**
- Use title case for proper nouns and concepts
- Append `(Source)` suffix to Source notes for disambiguation
- Organizations include legal suffix if commonly used (Inc., LLC, etc.)
- No prefixes like `concept-`, `org-`, `pattern-` in filenames
- Calendar entries use `YYYY-MM-DD` date prefix for natural chronological sorting
- Wiki-links use short form only (e.g., `[[Larry Smith]]` not `[[Ecosystem/People/Larry Smith]]`) — Obsidian resolves via unique filename matching

---

## Type System

The P-Sphere extends the content type enum to cover all knowledge entities:

```
atom | note | source | person | organization | role
```

| Type | Description | Primary ACCESS Folder |
|------|-------------|----------------------|
| `atom` | Atomic knowledge unit — a single concept, pattern, or claim | Cards/ |
| `note` | Standard note, MOC, draft, or working document | Cards/, Artifacts/, Spaces/ |
| `source` | Citation record — provenance metadata for a consumed source | Sources/ |
| `person` | Individual profile — a specific human being | Ecosystem/ |
| `organization` | Company, institution, agency, or collective | Ecosystem/ |
| `role` | Archetypal function or position (not tied to specific person) | Ecosystem/ |

---

## Card Subtypes

Cards (`type: atom`) are further classified by `subtype`:

| Subtype | Description |
|---------|-------------|
| `concept` | A named idea, definition, or named framework |
| `pattern` | Recurring behavior or structural regularity |
| `challenge` | Tension, problem, or unresolved question |
| `framework` | A structured analytical model or lens |
| `workflow` | A step-by-step operational process |
| `model` | A formal theory or system model |
| `signal` | An early indicator or weak signal of change |
| `metric` | A measurable indicator or KPI |
| `claim` | A specific assertion with supporting evidence |
| `technique` | A specific method or tactic |
| `scenario` | A futures narrative or possibility space |
| `technology` | A specific technology (current/emerging/hypothetical) |

---

## Status Lifecycle

The **physical folder location** determines the access boundary. The `status` field is confirmatory. The **credibility system** tracks knowledge maturity within Sandbox independently of promotion to Curated.

```
02_Sandbox/  →  AI autonomous zone (agents create/modify freely; all credibility levels)
03_Curated/  →  Collective published mesh (Principal approves promotion; for external sharing)
```

| Status | Meaning | Expected Location |
|--------|---------|-------------------|
| `private` | Never visible, internal only | Sandbox |
| `stub` | Placeholder — needs Researcher enrichment (Sources only) | Sandbox |
| `seed` | Newly created, raw (default for agent output) | Sandbox |
| `wip` | Being developed or enriched | Sandbox |
| `ready` | Reviewed, high credibility, available for Curated promotion | Sandbox |
| `published` | Live in Curated mesh for collective consumption | Curated |
| `unlisted` | Accessible but hidden from public indexes | Either |

**Key principle:** A note can reach `canonical` credibility level in Sandbox without ever being promoted to Curated. Credibility measures knowledge quality; promotion to Curated is a separate decision about whether that knowledge is suitable for collective sharing.

---

## Credibility Scoring System

The credibility system tracks knowledge quality as a **computed score** based on three signal types, weighted by authority. This lets you use AI agents to expand your cognitive reach while maintaining clear trust signals.

### Credibility Fields (ordered by decreasing authority weight)

```yaml
credibility:
  principal_reviews: 0      # Active human validations (weight: 5x)
  source_citations: 0       # Cross-references from Source atoms or external publications (weight: 3x)
  agent_validations: 0      # Cross-validation events by agents (weight: 1x)
  level: seed               # Auto-computed from weighted score
```

### Level Computation

```
score = (principal_reviews x 5) + (source_citations x 3) + (agent_validations x 1)
```

| Score Range | Level | Meaning |
|-------------|-------|---------|
| 0 | seed | Untouched since creation |
| 1-4 | emerging | Some engagement, not yet reliable |
| 5-14 | reviewed | Curator or sources have engaged meaningfully |
| 15-29 | validated | Strong confidence; multiple signals converge |
| 30+ | canonical | Foundational knowledge; heavily cited and reviewed |

### When to Increment

| Event | Field to Increment |
|-------|-------------------|
| You explicitly confirm/validate a note | `principal_reviews` |
| A Source atom links to this Card | `source_citations` |
| An external publication cites this concept | `source_citations` |
| An agent cross-references this note in analysis | `agent_validations` |

**Design principle:** Human judgment (5x) outweighs real-world citations (3x), which outweigh AI validation (1x). A single human review is worth as much as five agent cross-validations. This ensures the system scales your attention without diluting your authority.

---

## Frontmatter Standard

Frontmatter is **lean**. Content, summaries, and elaboration live in the markdown body.

### Required Fields (all atoms)

```yaml
---
title: "Article Title"
type: atom | note | source | person | organization | role
status: seed | wip | ready | published | unlisted | private
created_date: 2026-05-17
tags: []
---
```

### Conditional Fields

```yaml
subtype:            # Required for Cards (see Card Subtypes table)
confidence:         # Required for Cards: high | medium | low
source_type:        # Required for Sources (see Source Classification section)
output_type:        # Only for Principal's own published work (see Output Types table)
credibility_tier:   # Required for Sources: 1 | 2 | 3 | 4
enrichment_needed:  # Boolean — flags stub Sources for Researcher dispatch
publish_date:       # Only when status = published
domain:             # Knowledge domain IDs from domain taxonomy
source:             # Wiki-link to source atom: "[[Source Title (Source)]]"
agent:              # Provenance: librarian | researcher | reflector | principal
related:            # Array of wiki-links to connected atoms
description:        # One-sentence description (for quick scanning in Dataview)
```

### Anti-Patterns

**Never put these in frontmatter:**
- Full summaries or multi-sentence descriptions
- Arrays of principles, challenges, or benefits
- Operational workflows or step-by-step processes
- Quotes or extracted content

These belong in the **markdown body**.

---

## Confidence Levels

| Level | Meaning | Criteria |
|-------|---------|----------|
| **high** | Directly stated in source | Explicit assertion by credible source with citation |
| **medium** | Reasonably inferred | Logical deduction from stated facts; supported by context |
| **low** | Speculative | Extrapolation, hypothesis, or single-source claim without corroboration |

---

## Source Classification

### Source Types (`source_type`)

Every Source note MUST have a `source_type` field. This determines its filing subfolder, required metadata, and credibility weight.

| `source_type` | Subfolder | Description | Key Metadata |
|---------------|-----------|-------------|--------------|
| `book` | `Sources/T2_Authoritative/` | Full monograph | `isbn`, `publisher`, `edition` |
| `book-chapter` | `Sources/T2_Authoritative/` | Section in an edited volume | `isbn`, `book_title`, `editors` |
| `paper` | `Sources/T1_Primary/` | Journal article, conference paper, or preprint | `doi`, `journal` or `conference` |
| `thesis` | `Sources/T1_Primary/` | Doctoral, masters, or research proposal | `institution`, `degree_type` |
| `report` | `Sources/T2_Authoritative/` | White paper, policy doc, market analysis, govt report | `institution` |
| `standard` | `Sources/T1_Primary/` | ISO, W3C, patent, technical spec, software docs | `issuing_body`, `identifier` |
| `dataset` | `Sources/T1_Primary/` | Structured data, APIs, statistical sources | `provider`, `url` |
| `blog` | `Sources/T3_Professional/` | Web article on a blog (own or third-party) | `url`, `site_name` |
| `article` | `Sources/T3_Professional/` | News, magazine, newsletter piece | `url`, `publication` |
| `essay` | `Sources/T3_Professional/` | Long-form published argument/analysis | `url` |
| `video` | `Sources/T3_Professional/` | YouTube, talks, lectures, webinars | `url`, `channel`, `duration` |
| `podcast` | `Sources/T3_Professional/` | Audio episode | `url`, `show_name`, `episode` |
| `course` | `Sources/T3_Professional/` | Online course, MOOC, workshop material | `url`, `platform` |
| `presentation` | `Sources/T3_Professional/` | Slide deck, keynote, conference talk | `event_name`, `event_date` |
| `ai-synthesis` | `Sources/T4_Signal/` | AI-generated dispatch or summary (secondary source) | `model`, `source_count` |

### Output Types (`output_type`) — Principal's Intellectual Production

When a Source note represents the Principal's own published work, it receives BOTH `source_type` AND `output_type`. The shared types align with `source_type`; the output-only types extend the taxonomy for foresight and creative work.

**Shared types** (valid as both `source_type` and `output_type`):

`book` · `book-chapter` · `paper` · `thesis` · `report` · `blog` · `essay` · `presentation` · `video` · `podcast` · `course`

**Output-only types** (only valid as `output_type`):

| `output_type` | Description | Example |
|---------------|-------------|---------|
| `white-paper` | Self-published research/position paper | |
| `yellow-paper` | Technical specification or protocol doc | |
| `peer-reviewed-paper` | Published in a peer-reviewed journal | JIDS articles |
| `lexicon` | Published vocabulary/definitions | yoursite.com/lexicon |
| `influence` | Review/commentary on a formative work | Book review, intellectual response |
| `review` | Formal review of a paper/book/tool | |
| `media-script` | Video/audio scripts, show notes | |
| `futures-scenario` | Foresight-structured scenario narrative | Published scenarios |
| `signal` | Futures signal write-up | Weak/strong signal observations |
| `driver` | Futures driver analysis | Macro-trend or forcing function |
| `design-fiction` | Speculative design artifact/narrative | |

### Credibility Tiers (`credibility_tier`)

Indicates the citation weight of a source. Use this to prioritize references when writing research papers (Tier 1-2), blog posts (Tier 1-3), or futures scenarios (all tiers valid as signals).

| Tier | Label | Typical Source Types |
|------|-------|---------------------|
| **1** | Primary/Empirical | `paper` (peer-reviewed), `thesis`, `dataset`, `standard` |
| **2** | Authoritative | `book`, `book-chapter`, `report` (institutional) |
| **3** | Informed/Professional | `blog`, `article`, `essay`, `video`, `podcast`, `course`, `presentation` |
| **4** | Indicative/Signal | `ai-synthesis` |

**Tier Rationale and Commentary:**

**T1 — Primary/Empirical:** The bedrock of the knowledge graph. These sources have undergone peer review, formal validation, or represent direct empirical data. They carry the highest citation weight because their claims have been subjected to systematic scrutiny. When constructing arguments in academic writing or formal reports, T1 sources form the evidentiary foundation. Includes: peer-reviewed journal articles, doctoral and master's theses, formally published datasets with methodology, ISO/W3C/IEEE standards, patents, and technical specifications.

**T2 — Authoritative:** Published works by recognized authorities — typically with editorial oversight but not necessarily peer-reviewed in the academic sense. Books undergo editorial review and represent sustained, structured arguments. Institutional reports (from governments, think tanks, international organizations) carry organizational credibility. These are strong supporting evidence and can anchor conceptual frameworks. Includes: monographs, edited volumes, book chapters, white papers from credible institutions, government policy documents, market analyses from established research firms.

**T3 — Professional/Informed:** The working knowledge layer — published by practitioners, educators, and domain professionals. These sources are valuable for current thinking, practical applications, emerging trends, and professional discourse, but lack the formal validation of T1-T2. They represent the "state of practice" rather than the "state of knowledge." Excellent for contextualizing academic claims in real-world application, identifying emerging patterns, and capturing practitioner wisdom. Includes: professional blogs, news articles, essays, conference presentations, video lectures, podcasts, online courses, webinars.

**T4 — Signal/Indicative:** AI-generated syntheses, social media posts, unverified claims, and early-stage intelligence. These are not citable as evidence but serve as discovery vectors — they point toward where to look next. AI dispatches (our own research system output) live here because they are secondary sources that synthesize and interpret primary materials. Their value is in aggregation and pattern-spotting, not in standalone authority. The Librarian traces their upstream citations back to T1-T3 sources for proper attribution. Includes: AI research dispatches, LLM-generated summaries, social media threads, informal signals, unverified community reports.

Note: The Principal's own peer-reviewed papers get Tier 1. Own blog posts get Tier 3. This reflects citation weight, not quality.

### Source Filing Structure

Sources are organized by credibility tier in physical subfolders. The `source_type` field captures format; the physical folder signals citation weight at a glance.

```
02_Sandbox/Sources/
├── Sources.md          (Dataview index — queries all tiers)
├── T1_Primary/         (Tier 1: peer-reviewed papers, theses, datasets, standards)
├── T2_Authoritative/   (Tier 2: books, institutional reports, book chapters)
├── T3_Professional/    (Tier 3: blogs, articles, talks, courses, presentations)
└── T4_Signal/          (Tier 4: AI synthesis, social posts, unverified)
```


---

## The Six ACCESS Categories

### A — Artifacts

**Location:** `02_Sandbox/Artifacts/` or `03_Curated/*/Artifacts/`

Significant intellectual output — substantial working documents, synthesized drafts, and polished deliverables. Artifacts are "compound" — they reference multiple Cards and Sources.

**Contains:** Research syntheses, draft manuscripts, strategy documents, operational models, design specs.

**When to use:** The source material warrants a multi-section synthesis rather than atomic decomposition.

---

### C — Calendar

**Location:** `02_Sandbox/Calendar/` or `03_Curated/*/Calendar/`

Time-bound data — events, milestones, meetings, deadlines, and temporal markers. Calendar entries use date-prefixed filenames for natural chronological ordering within the flat folder.

**Naming:** `YYYY-MM-DD Meeting — Topic.md` or `YYYY-MM-DD Milestone — Description.md`

**Subtypes:**

| Subtype | Description | Source |
|---------|-------------|--------|
| `meeting` | Recorded conversation or call with identified participants | Plaud recordings, manual notes |
| `milestone` | Project achievement, completion marker, or deliverable date | Project tracking |
| `event` | Attended or referenced event (conference, symposium, workshop) | Calendar, invitations |
| `deadline` | Hard date for a deliverable, submission, or commitment | External requirements |
| `reflection` | Voice note, braindump, or solo thinking session | Plaud solo recordings, journal |

**Contains:** Meeting notes, project milestones, historical events, timeline markers for futures scenarios.

**When to use:** The information has a specific temporal anchor that matters for its interpretation. Meetings with named participants always get a Calendar atom (not just a task or action item).

**Frontmatter (Calendar-specific fields):**

```yaml
subtype: meeting | milestone | event | deadline | reflection
date_relevant: 2026-05-15          # The date this event occurred (not the processing date)
duration_minutes: 25                # Duration in minutes (for meetings/events)
participants: ["[[Person 1]]"]      # Wiki-links to Ecosystem/People entries
plaud_id: "abc123..."              # Plaud recording ID (for meetings from Plaud)
```

---

### C — Cards

**Location:** `02_Sandbox/Cards/` or `03_Curated/*/Cards/`

Atomic units of thought — the smallest meaningful unit of knowledge that can stand alone. Classified by `subtype` (see Card Subtypes table above).

**Contains:** Concepts, patterns, challenges, frameworks, workflows, models, signals, metrics, claims, techniques, scenarios, technologies.

**When to use:** The information represents a single, self-contained idea that can be linked to other atoms. This is the most common atom type.

---

### E — Ecosystem

**Location:** `02_Sandbox/Ecosystem/{People|Organizations|Roles}/` or `03_Curated/*/Ecosystem/{People|Organizations|Roles}/`

Relational mapping — the people, organizations, and roles that constitute the knowledge landscape.

**Structure:**

```
Ecosystem/
├── Ecosystem.md        (Dataview index — queries all subfolders)
├── People/             (type: person)
├── Organizations/      (type: organization)
└── Roles/              (type: role — archetypal positions, not tied to a specific person)
```

**Types:** `person`, `organization`, `role`

**Filing Rules:**
- People → `Ecosystem/People/` — specific individuals whose identity, relationships, or contributions are worth tracking
- Organizations → `Ecosystem/Organizations/` — companies, institutions, agencies, collectives, or projects with organizational structure
- Roles → `Ecosystem/Roles/` — archetypal functions or positions not tied to a specific person (e.g., "Editorial Director", "In-House Content Manager")

**When to use:** The source references specific actors whose identity, relationships, or operational models are worth tracking.

**Stub Pattern:** The Librarian creates stubs with available info. The Researcher enriches later with web data (Crunchbase, LinkedIn, etc.).

---

### S — Sources

**Location:** `02_Sandbox/Sources/{T1_Primary|T2_Authoritative|T3_Professional|T4_Signal}/` or `03_Curated/*/Sources/`

Citation records — metadata about where knowledge came from. Every ingested source gets a Source atom serving as the provenance record. Sources are classified by `source_type`, assigned a `credibility_tier`, and filed into the subfolder matching their credibility level.

**Subfolders (by credibility):**
- `T1_Primary/` — peer-reviewed papers, theses, datasets, formal standards (Tier 1)
- `T2_Authoritative/` — books, institutional reports, book chapters (Tier 2)
- `T3_Professional/` — blogs, articles, essays, videos, podcasts, courses, presentations (Tier 3)
- `T4_Signal/` — AI-generated dispatches, social posts, unverified sources (Tier 4)

**Naming:** Append `(Source)` to distinguish from same-named concepts. E.g., `Enterprise Publishing Taxonomy (Source).md`

**When to use:** Always — every ingested document gets a Source note. AI dispatches are classified as secondary sources (Signal tier); the Librarian should also create stub Source notes for identifiable upstream primary sources cited within them.

---

### S — Spaces

**Location:** `02_Sandbox/Spaces/` or `03_Curated/*/Spaces/`

High-level orientation zones — Maps of Content (MOCs), area overviews, and navigational structures.

**Contains:** MOCs linking related atoms, area overviews, project indexes, support/process documentation.

**When to use:** When a cluster of atoms needs a navigational hub. Spaces emerge after the Structural Reflector identifies Attraction Centers.

---

## Folder Index Notes

Each ACCESS subfolder contains a folder note (same name as folder, e.g., `Cards/Cards.md`) with Dataview queries for navigation. These show atoms grouped by status and sorted by recency.

---

## Integration with External Publishing (Website/CMS)

Notes that graduate from `03_Curated/` to your website use:
- `output_type` field to determine collection routing (blog, essay, etc.)
- `status: published` to appear in site listings
- `publish_date` for display ordering

The P-Sphere `type` enum is a superset of typical CMS schemas. Ecosystem entries (`organization`, `role`) generally don't publish to the site.

---

**End of Schema**