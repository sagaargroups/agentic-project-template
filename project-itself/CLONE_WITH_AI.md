# 🤖 AI-Driven Selective Clone — Paste This Into Your AI Agent

> **For users:** Copy this entire file's content and paste it into your AI coding agent (Cursor, Claude Code, Antigravity, Windsurf, GitHub Copilot, etc.). The AI will handle everything — you just answer questions.

---

**ATTENTION AI AGENT:** You are being given a selective-clone directive. Your job is to help this user get exactly what they need from the `agentic-project-template` repository — without cloning the entire thing. Follow the steps below in exact order. Do everything on the user's behalf. The user should only answer your questions, nothing else.

**REPO:** `https://github.com/sagaargroups/agentic-project-template`
**BASE PATH:** `project-itself/`

---

## STEP 1 — Understand the User's Project

Before touching the remote repo, understand what the user already has.

**Action:** Read the user's current working directory structure (use `ls -la`, `find . -maxdepth 3 -type f | head -60`, or equivalent).

**Extract:**
- Project name (from folder name, `package.json`, `pyproject.toml`, `README.md`, etc.)
- Tech stack (from config files: `package.json` → JS/TS, `requirements.txt` → Python, `Cargo.toml` → Rust, `go.mod` → Go, etc.)
- Industry signals (folder names like `health/`, `finance/`, `ecommerce/`, or keywords in README)
- Whether `.agents/` directory already exists (and what's inside it)
- Current folder structure depth and conventions

**Store this context internally. You will use it in Step 4.**

> **RULE:** If you cannot determine the industry or tech stack from files alone, ask the user ONE combined question:
> "What industry is your project in, and what's your primary tech stack?"

---

## STEP 2 — Read the Remote Repo (No Cloning)

**Action:** Fetch the full repo file tree using the GitHub API:

```bash
curl -s "https://api.github.com/repos/sagaargroups/agentic-project-template/git/trees/main?recursive=1" | grep '"path"' | head -200
```

If the above fails (rate limit, branch name), try:
```bash
curl -sL "https://github.com/sagaargroups/agentic-project-template/tree/main/project-itself" -o /dev/null -w "%{http_code}"
```

If both fail, tell the user: "I can't reach the repo right now. Please check your internet or try again later." and STOP.

**Parse the tree** to identify all paths under `project-itself/.agents/`.

---

## STEP 3 — Build the Inventory

From the file tree, categorize everything available. The repo uses this structure:

```
.agents/
├── brain/              # Project intelligence
├── skills/             # 🌍 Industry-organized skills (The God Book)
│   ├── _universal/     # Cross-industry (always needed)
│   ├── information-technology/
│   ├── healthcare/
│   ├── fintech/
│   ├── ecommerce/
│   ├── edtech/
│   ├── legal/
│   ├── marketing-media/
│   ├── manufacturing/
│   ├── real-estate/
│   ├── hospitality/
│   ├── logistics/
│   ├── agriculture/
│   └── ... (grows over time)
├── workflows/          # Multi-step automation flows
├── plugins/            # Bundled multi-skill packages
└── tool-registry/      # MCP & tool catalog (registry only)
```

### A. Brain (`project-itself/.agents/brain/`)
| Folder | What It Contains |
|---|---|
| `context.md` | Master AI context template (tech stack, guardrails, playbooks) |
| `readme.md` | Human guide to the brain system |
| `working/` | Day-to-day working sessions & docs |
| `learning/` | Persistent research & knowledge |
| `tasks/` | Task checklists & daily logs |
| `think-tank/` | Growth direction, strategy, vision docs |

### B. Universal Skills (`project-itself/.agents/skills/_universal/`)
Read each folder to get SKILL.md descriptions:

```bash
curl -s "https://raw.githubusercontent.com/sagaargroups/agentic-project-template/main/project-itself/.agents/skills/_universal/project-setup/SKILL.md" | head -5
```

**Known universal skills:**
- `context-blueprint` — How to write `context.md` files
- `project-baseline` — Mandatory files every project needs
- `project-setup` — The setup directive skill
- `readme-blueprint` — How to write `README.md` files
- `warehouse-ecosystem` — Full warehouse architecture & contribution flow
- `contribution-router` — Auto-classify and route contributions
- `agentic-skill-creator` — Create production-grade agentic skills with MCP tools
- `skill-creator` — Third-party skill creator with templates and scripts

### C. Industry Skills (`project-itself/.agents/skills/[industry]/`)
Each industry folder contains skills specific to that domain. Read the tree to discover what's populated:

- `information-technology/` — Production standards, UI system, and more
- `healthcare/` — Clinical workflows, medicine categories, compliance
- `fintech/` — Financial workflows, compliance, trading
- `ecommerce/` — Store setup, inventory, fulfillment
- `edtech/` — Learning management, curriculum design
- `legal/` — Contract analysis, compliance frameworks
- `marketing-media/` — Content strategy, social media, SEO
- `manufacturing/` — Supply chain, quality control
- `real-estate/` — Property management, listings
- `hospitality/` — Booking systems, guest experience
- `logistics/` — Fleet management, routing
- `agriculture/` — Crop planning, supply chain

> **NOTE:** Not all industry folders may have content yet. The repo grows over time. Check the tree for populated folders.

### D. Plugins (`project-itself/.agents/plugins/`)
Read each `plugin.json`:

```bash
curl -s "https://raw.githubusercontent.com/sagaargroups/agentic-project-template/main/project-itself/.agents/plugins/brand-establishment/plugin.json"
```

**Known plugins:**
- `brand-establishment` — Brand identity, voice, logo, IP protection, business prelaunch
- `super-intelligence` — Claude Skills, researched articles, social media automation, universal automation

### E. Tool Registry (`project-itself/.agents/tool-registry/`)
- `registry.json` — Central catalog of MCP servers & external tools

### F. Root Files (`project-itself/`)
- `README.md` — Project overview & quick start
- `setup.md` — AI agent setup directive (full project init)
- `CONTRIBUTING.md` — How to contribute skills & tools
- `LICENSE` — MIT License
- `.gitignore` — Standard exclusion rules

---

## STEP 4 — Match to User's Context

Using what you learned in Step 1, auto-generate a recommendation:

**Match logic:**
- **Any project** → Always recommend: `brain/` (context.md, readme.md), `skills/_universal/context-blueprint`, `skills/_universal/project-baseline`, `.gitignore`
- **Software/Dev projects** → Add: `skills/information-technology/` (production-standards, ui-system)
- **Brand/Startup** → Add: `plugins/brand-establishment/`
- **Content/Marketing** → Add: `plugins/super-intelligence/` (articles, social-media-automation)
- **Healthcare projects** → Add: `skills/healthcare/`
- **FinTech projects** → Add: `skills/fintech/`
- **E-commerce** → Add: `skills/ecommerce/`
- **Any project wanting to grow** → Add: `brain/think-tank/`, `skills/_universal/warehouse-ecosystem`
- **Projects wanting skill creation** → Add: `skills/_universal/agentic-skill-creator` or `skill-creator`
- **Already has `.agents/`** → Skip what exists, offer only what's missing

---

## STEP 5 — Ask the User (Interactive, Short)

Present your findings in this format. Be concise:

```
Based on your [INDUSTRY] project using [TECH_STACK], here's what I recommend from the Agentic Project Template:

🟢 RECOMMENDED FOR YOU:
  1. [item] — [one-line why]
  2. [item] — [one-line why]
  ...

🟡 MIGHT BE USEFUL:
  1. [item] — [one-line why]
  ...

Pick options by number, or choose:
  A) Take all recommended (🟢)
  B) Take everything (🟢 + 🟡)
  C) Show me the FULL inventory of this repo — I want to browse everything
  D) I need something from a different industry — show me all categories
```

**Wait for user response before proceeding.**

If user picks **C** or **D**, list the complete inventory from Step 3 with descriptions, and let them pick individually.

**After user selects:**
> "These are the items I'll fetch and place in your project: [list]. Shall I proceed?"

Wait for confirmation.

---

## STEP 6 — Fetch & Place

For each selected item, download the raw files and place them in the user's project.

**For individual files:**
```bash
curl -sL "https://raw.githubusercontent.com/sagaargroups/agentic-project-template/main/project-itself/[PATH]" -o "[LOCAL_PATH]"
```

**For entire folders** — use the GitHub API to list contents, then download each file:
```bash
# List folder contents
curl -s "https://api.github.com/repos/sagaargroups/agentic-project-template/contents/project-itself/[FOLDER_PATH]?ref=main"

# Then curl each file's download_url
```

**Placement rules:**
| Source Path | Place In User's Project |
|---|---|
| `project-itself/.agents/...` | `./.agents/...` |
| `project-itself/.gitignore` | `./.gitignore` (merge if exists, don't overwrite) |
| `project-itself/CONTRIBUTING.md` | `./CONTRIBUTING.md` |
| `project-itself/LICENSE` | `./LICENSE` (only if user doesn't have one) |

**Create parent directories** as needed with `mkdir -p`.

**If a file already exists** in the user's project:
> Ask: "You already have [file]. Should I: (1) Skip it, (2) Overwrite it, (3) Save the new one as [file].from-template?"

---

## STEP 7 — Personalize

After placing files, automatically update placeholders:

**In `.agents/brain/context.md`:**
- Replace `[PROJECT NAME]` → user's actual project name
- Replace `[DATE]` → today's date
- Replace `[e.g., FinTech, ...]` → user's actual industry (from Step 1/5)
- Replace `[e.g., TypeScript Node.js ...]` → user's actual tech stack
- Replace other `[PLACEHOLDER]` fields with detected values

**In `.agents/brain/readme.md`:**
- Replace project name references

**Do NOT modify** any SKILL.md files, plugin.json files, or third-party content.

---

## STEP 8 — Summary & Next Steps

Tell the user exactly what was done:

```
✅ Done! Here's what I added to your project:

📁 Files added:
  - .agents/brain/context.md (personalized)
  - .agents/skills/_universal/context-blueprint/
  - .agents/plugins/brand-establishment/
  - ... [list all]

📝 Personalized:
  - context.md → Updated with your project info

🚀 Suggested next steps:
  1. Review .agents/brain/context.md and fill in any remaining [PLACEHOLDER] fields
  2. Tell your AI agent: "Read .agents/brain/context.md" before any major task
  3. Explore the skills you downloaded — each has a SKILL.md with instructions
  4. To get more skills later, paste this prompt again — I'll detect what you already have
```

---

## ERROR HANDLING

- **Network failure:** "Can't reach GitHub. Check internet and retry."
- **Rate limited:** "GitHub API rate limited. Wait 60 seconds or provide a GitHub token."
- **File not found:** Skip silently, note it in summary as "unavailable — may have been moved or renamed"
- **Permission denied:** "I don't have write permission to [path]. Please check your file system permissions."
- **Existing `.agents/` detected:** "You already have an `.agents/` directory. I'll only add items you're missing — nothing will be overwritten without your approval."

---

## RULES FOR THE AI AGENT

1. **You do ALL the work.** The user only answers questions.
2. **Be token-efficient.** Don't dump raw API responses. Summarize.
3. **Never force.** Every destructive action (overwrite, delete) needs user approval.
4. **Be smart about existing content.** If user already has files, merge or skip — don't blindly overwrite.
5. **This is a public repo.** No auth needed. Standard `curl` works.
6. **One question at a time.** Don't overwhelm with 10 questions. Bundle smart.
7. **If you discover something new in the repo** that isn't in this inventory list, include it — the repo grows over time.
8. **After completion, offer:** "Want me to also set up this project fully? Say 'Run setup.md' and I'll configure everything."
