# Perceptiosphere (P-Sphere)

Perceptiosphere means the nested, concentric sphere of context around an entity, in which constitutes their unique perception of the informational world. This starter-kit is a AI-native cognitive operating system developed by Francis Wang in his doctoral research. 

Using the **CORE** (Collect, Organize, Reflect, Execute) process, the P-Sphere allows a human operator to manage high-velocity information through a teamed approach of AI agents, forming Hybrid Intelligence (HI) teams.

This repository serves as the "bootloader" for your personal intelligence stack. It manages the transition from raw environmental noise to structured, sovereign knowledge.

## The CORE Methodology

The P-Sphere functions as a metabolic process for cognition. Information moves through four primary phases:

1. **Collect:** Ingesting raw signals from the environment.
2. **Organize:** Clustering and synthesizing data within a sandbox environment.
3. **Reflect:** Curating and promoting validated insights into a permanent knowledge mesh.
4. **Execute:** Transforming reflected knowledge into tangible outputs and projects.

---

## Repository Structure

The P-Sphere utilizes a flattened folder hierarchy to maintain agility while enforcing the CORE workflow.

### `00_Protocol`

The Blueprint. This is the only folder fully tracked by Git. It contains the instructions, design guidelines, and agent definitions that govern the system.

* **Agent Definitions:** System prompts for the Chief of Staff and specialized sub-agents.
* **Schemas:** Neo4j ontology and GraphRAG metadata standards.
* **Templates:** Obsidian frontmatter and Map of Content (MOC) structures.

### `01_Inflow`

The Sensorium. This is the high-entropy landing zone for all raw data.

* **Inputs:** Plaud audio transcripts, RSS feeds from Inoreader, and web clips.
* **Process:** Agents scan this folder for signals to move into the Sandbox.

### `02_Sandbox`

The Cognitive Sandbox. This is an AI-assisted R&D lab.

* **Function:** An unreviewed wiki where research agents dump initial findings.
* **Usage:** Use this space to bounce ideas off an "AI Consultant" and stress-test concepts before they reach the curated mesh.

### `03_Curated`

The Knowledge Mesh. This is the heart of the P-Sphere. It uses embeddings and Neo4j for GraphRAG.

* **Sovereign (SKMesh):** Private, deep-context knowledge. It remains local and is never tracked by Git.
* **Collective (CKMesh):** Federated knowledge shared with the community. This folder syncs with collaborators like Tao or James.

### `04_Ecosystem`

The Relational Graph. This domain maps the social and professional dependencies of your work.

* **Mapping:** Tracks Persona, Entities, and Roles. It provides the necessary social context for agentic reasoning.

### `05_Artifacts`

The Forge. This is the home for finalized intellectual property.

* **Outputs:** Refined manuscripts, validated reports, and published documentation.

### `06_Efforts`

The Operations Room. This folder tracks active work and physical projects.

* **Action:** Manages project states such as Active, Parked, or Scheduled. It is where **OpenCode** and **OpenWork** agents execute specific tasks.

---

## Technical Infrastructure

### Agent Orchestration

The system utilizes a **Chief of Staff (CoS)** agent as a strategic partner. The CoS manages the cognitive load by directing specialized sub-agents (Coder, Researcher, Ghostwriter) based on the instructions found in `00_Protocol`.

### GraphRAG and Sovereign Intelligence

The `03_Curated` folder is encoded with local embeddings. This allows the AI team to perform complex retrievals that combine semantic search with relational graph traversals. By keeping the **SKMesh** on local hardware (such as a Mac Mini cluster), the operator maintains a private intellectual advantage.

---

## Getting Started

1. **Clone the Repo:** Initialize your local P-Sphere directory.
2. **Configure Agents:** Update the `opencode.json` at the root to point to your local LLM endpoints.
3. **Boot the System:** Point Obsidian to the root folder to begin the CORE cycle.
4. **Structured Reflection:** Set a recurring cadence to move notes from `02_Sandbox` to `03_Curated`.

The Perceptiosphere is built for those who excel in their domain and require a clear, direct, and sovereign method for managing complexity. It rejects the artificial neutrality of standard AI tools in favor of a vigorous, active-voice approach to personal knowledge management.
