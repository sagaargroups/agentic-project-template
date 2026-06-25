# 🤖 AI Agent Setup Directive

**ATTENTION AI AGENT:** You have just been given access to the Agentic Project Template. Your job is to transform this generic template into a fully-configured, project-specific environment. Follow the exact sequence below.

> **CRITICAL RULE:** Do NOT delete the `.brain/` structure or `.agents/` directory. They must remain intact as the operating system for this project.

---

## Step 1: Gather Project Context

Before making ANY file changes, ask the human founder the following questions:

1. **What is the name of this new project/brand?**
2. **What is the core vision or one-liner for this project?**
3. **What is the primary tech stack?** (e.g., Next.js, Python/FastAPI, React Native, No-code)
4. **What industry does this project serve?** (e.g., FinTech, HealthTech, E-Commerce, EdTech)
5. **Where should the codebase live?** (Inside `project-itself/` or should the repo root be the project?)

*Do not proceed to Step 2 until the founder answers ALL questions.*

---

## Step 2: Select Skill Bundles

Present this menu to the founder. They select which plugin bundles their project needs:

```
Which skill bundles does your project need? (Select all that apply)

☐ brand-establishment    — Brand identity, voice, logo, IP protection
☐ development            — Frontend, backend, API, testing, MCP builder
☐ content-engine         — Topic research, script writing, video prompts
☐ seo-geo                — Keyword research, on-page SEO, GEO strategy
☐ devops-pipeline        — CI/CD, Docker, monitoring, infrastructure
☐ data-analytics         — Dashboards, reports, A/B testing, metrics
☐ finance-ops            — Invoicing, tax, expenses, audit support
☐ legal-compliance       — Privacy policy, terms, IP protection
☐ productivity           — Task management, meetings, time tracking
☐ sales-growth           — Lead gen, CRM, pitch decks, onboarding
```

After selection:
1. **Keep** only the selected plugin folders inside `.brain/0_warehouse-skills/plugins/`
2. **Delete** all unselected plugin folders
3. **Always keep** `skills/` (meta-skills like `contribution-router`) and `third-party/` intact

---

## Step 3: Configure the Brain

1. **Update `.brain/context.md`:** Replace all `[PLACEHOLDER]` fields with the specific vision, tech stack, industry, conventions, and guardrails.
2. **Update `.brain/readme.md`:** Replace the project name if needed.
3. **Clear personal folders (2, 3, 4):** Remove example content but keep `context.md` and `readme.md`.

---

## Step 4: Initialize the Project

1. **Initialize Fresh Git:**
   ```bash
   rm -rf .git
   git init
   ```
2. **Rename the Root Directory** (if needed): Rename to `[Project-Name]`.
3. **Set up codebase:** Scaffold the appropriate structure for the chosen tech stack.

---

## Step 5: Scaffold Brand Architecture (Optional)

If the founder selected `brand-establishment`, create:

```text
├── brand-identity/    (Logo, colors, typography, brand voice)
├── registration/      (Account setup checklists)
├── docs/              (Architecture and organization)
├── wiki/              (Public-facing docs, llms.txt)
├── seo/               (Keywords, listings, GEO)
└── ops/               (Infrastructure, legal, security)
```

---

## Step 6: Daily Workflow Setup

Explain to the founder:

- **Daily logs** → `brain/4_tasks-and-logs/` with date headers and ✅/🚧/🔜 sections
- **Session archives** → `brain/2_working/session_YYYY-MM-DD.md`
- **Learning** → `brain/3_learning/` with descriptive filenames and source links

---

## Step 7: Finalization

1. Create the first daily log documenting the setup.
2. Notify the founder the environment is ready.
3. Ask if they want to create project-specific skills in `.agents/skills/`.

---

## Standards Reference

### Naming Standard
- Always `kebab-case`, max 3 words
- Skills = specific actions (`keyword-research`, not `seo`)
- Plugins = domain categories (`content-engine`, not `my-stuff`)

### SKILL.md Format
```yaml
---
name: skill-name
description: "One-line description of what this skill does."
---

# Skill Title

[Instructions for the AI agent...]
```

### Plugin Format
```
plugin-name/
├── plugin.json          # name, description, skills list
└── skills/
    └── skill-name/
        └── SKILL.md
```
