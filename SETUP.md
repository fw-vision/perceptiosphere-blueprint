# Setup Guide

This guide walks you through bootstrapping your own Perceptiosphere instance.

---

## Prerequisites

| Requirement | Purpose | Alternatives |
|-------------|---------|--------------|
| **[Obsidian](https://obsidian.md)** | Vault interface, wiki-linking, graph view | Any Markdown editor with wiki-link support |
| **[OpenCode](https://opencode.ai)** | Agent orchestration framework | Any LLM agent framework with subagent support |
| **LLM Proxy** | Routes model requests to your provider(s) | [LiteLLM](https://github.com/BerriAI/litellm), [OpenRouter](https://openrouter.ai), direct API |
| **LLM Access** | At least one model per tier (can share) | See tier recommendations below |
| **Git** | Version control for the Protocol layer | — |

### Minimum Model Requirements

You need at least **one model** to start, but the tier system shines with differentiation:

| Tier | Minimum Viable | Recommended |
|------|---------------|-------------|
| Tier 1 (Reasoning) | Any frontier model | Claude Opus, GPT-4o, Gemini Ultra |
| Tier 2 (Writing) | Same as Tier 1 (shared) | Claude Sonnet, Qwen3 80B |
| Tier 2.5 (Light) | Any mid-range model | Qwen3 32B, Gemini Flash |
| Tier 3 (Scanning) | Any fast/cheap model | GPT-4o-mini, Llama 3, Phi-3 |

**Budget option:** Use a single model (e.g., Claude Sonnet) for all tiers. You lose cost optimization but the architecture still works.

---

## Step 1: Clone and Configure

```bash
# Clone the blueprint
git clone https://github.com/your-username/perceptiosphere-blueprint.git my-perceptiosphere
cd my-perceptiosphere

# Create your local config from the sample
cp opencode.json.sample opencode.json
```

Edit `opencode.json` and replace all `{{PLACEHOLDER}}` values:

| Placeholder | Replace With |
|-------------|-------------|
| `{{LLM_PROXY_BASE_URL}}` | Your LiteLLM or proxy URL (e.g., `http://localhost:4000/v1`) |
| `{{TIER_1_MODEL_ID}}` | Your reasoning model ID (e.g., `openai/gpt-4o`, `anthropic/claude-opus`) |
| `{{TIER_2_MODEL_ID}}` | Your writing model ID |
| `{{TIER_2C_MODEL_ID}}` | Your coding model ID |
| `{{TIER_2_5_MODEL_ID}}` | Your light-tasks model ID |
| `{{TIER_3_MODEL_ID}}` | Your fast/cheap model ID |

---

## Step 2: Set Up Your LLM Proxy (if using LiteLLM)

```bash
# Install LiteLLM
pip install litellm[proxy]

# Create a config (litellm_config.yaml)
cat > litellm_config.yaml << 'EOF'
model_list:
  - model_name: your-tier1-model
    litellm_params:
      model: anthropic/claude-opus-4
      api_key: sk-...
  - model_name: your-tier2-model
    litellm_params:
      model: anthropic/claude-sonnet-4
      api_key: sk-...
EOF

# Start the proxy
litellm --config litellm_config.yaml --port 4000
```

---

## Step 3: Open in Obsidian

1. Open Obsidian
2. "Open folder as vault" → select your cloned directory
3. Trust the vault when prompted

### Recommended Plugins (optional)

- **Templater** — For using the `00_Protocol/Templates/` with hotkeys
- **Dataview** — For querying atoms by frontmatter fields
- **Graph Analysis** — For visualizing knowledge connections

---

## Step 4: Customize the COS Prompt

Edit `00_Protocol/Agents/prompts/cos.md`:

1. Replace `{{PRINCIPAL_NAME}}` with your name
2. Fill in the Organizations Under Management table with your projects/brands
3. Update the `.brand/context.md` paths to match your organizations

---

## Step 5: Create Your Brand Context (optional)

If you manage multiple projects or brands, create a context file for each:

```bash
# Example: create a brand context
cp 04_Execute_Efforts/.brand/context.sample.md 04_Execute_Efforts/.brand/my-project.context.md
```

Edit the context file with your brand's voice, audience, and constraints.

---

## Step 6: First Run — Test the System

```bash
# Start OpenCode in the vault directory
opencode

# Test the COS agent responds
> What agents are available?

# Test the Librarian by dropping a file into Inbox
# Copy any article/PDF into 01_Collect_Inflow/Inbox/
> Process the inbox
```

---

## Step 7: Establish Your Rituals

The P-Sphere includes three ritual protocols in `00_Protocol/Rituals/`:

| Ritual | Frequency | Purpose |
|--------|-----------|---------|
| Morning Planning | Daily | Assess load, prioritize tasks, set intentions |
| Evening Shutdown | Daily | Archive completed work, flag tomorrow's priorities |
| Weekly Review | Weekly | Promote sandbox atoms, identify patterns, adjust strategy |

These reference a generic `{{TASK_MANAGER}}` — replace with your tool (Sunsama, Todoist, Things, etc.) or remove the integration steps entirely.

---

## Directory Conventions

### What Git tracks (committed)
- `00_Protocol/` — The entire system blueprint
- `AGENTS.md` — Agent registry
- `.gitignore` — Tracking rules
- `README.md`, `SETUP.md`, `LICENSE`

### What stays local (never committed)
- `opencode.json` — Your actual config with real endpoints
- `01_Collect_Inflow/` through `04_Execute_Efforts/` — All knowledge content
- `_Archived/` — Processed raw materials
- `.env`, secrets, local overrides

### Sync strategy
- **Git:** Protocol layer only (shareable system design)
- **SyncThing / iCloud / Dropbox:** Full vault across your devices (optional)
- **Never mix:** Don't put content in Git; don't put secrets in sync

---

## Upgrading from the Blueprint

When the upstream blueprint releases updates:

```bash
# Add upstream remote (one-time)
git remote add upstream https://github.com/fw-vision/perceptiosphere-blueprint.git

# Fetch and merge Protocol updates
git fetch upstream
git merge upstream/main --no-commit

# Review changes — only Protocol files should be affected
git diff --staged

# Commit if satisfied
git commit -m "Merge upstream blueprint updates"
```

Your content folders are gitignored, so merges will never touch your knowledge.

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| "Model not found" errors | Verify your proxy is running and model IDs match exactly |
| Agents don't delegate | Check `opencode.json` permission block — subagents must be listed |
| Librarian creates wrong folder structure | Ensure `02_Organize_Sandbox/` subfolders exist (check `.keep` files) |
| Git tracking content files | Run `git rm --cached -r 01_Collect_Inflow/` then commit |

---

## Next Steps

1. **Read `AGENTS.md`** to understand the full agent roster and workflows
2. **Explore `00_Protocol/Schema/access-atoms.md`** for the complete taxonomy
3. **Customize templates** in `00_Protocol/Templates/` for your domain
4. **Start collecting** — the system activates when material flows in
