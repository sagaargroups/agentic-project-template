# 🤖 AI Agent Setup Directive

**ATTENTION AI AGENT:** You have just been given access to the Agentic Project Template. Your job is to transform this generic template into a fully-configured, project-specific environment. Follow the exact sequence below.

> **CRITICAL RULE:** Do NOT delete the `.agents/` directory or its structure. It must remain intact as the operating system for this project.

---

## Step 1: Gather Project Context

Before making ANY file changes, ask the human founder the following questions:

1. **What is the name of this new project/brand?**
2. **What is the core vision or one-liner for this project?**
3. **What is the primary tech stack?** (e.g., Next.js, Python/FastAPI, React Native, No-code)
4. **What industry does this project serve?** (e.g., FinTech, HealthTech, E-Commerce, EdTech)
5. **Where should the codebase live?** (Inside this directory or should the repo root be the project?)

*Do not proceed to Step 2 until the founder answers ALL questions.*

---

## Step 2: Select Industry Skills & Plugins

Present this menu to the founder. They select which skill bundles their project needs:

### Industry Skills (from `.agents/skills/`)
```
Which industry skills does your project need? (Select all that apply)

☐ _universal              — Cross-industry essentials (always recommended)
☐ information-technology   — Production standards, UI system, DevOps
☐ healthcare              — Clinical workflows, medicine categories, HIPAA
☐ fintech                 — Financial compliance, trading, payments
☐ ecommerce               — Store setup, inventory, fulfillment
☐ edtech                  — Learning management, curriculum design
☐ legal                   — Contract analysis, compliance frameworks
☐ marketing-media         — Content strategy, social media, SEO
☐ manufacturing           — Supply chain, quality control
☐ real-estate             — Property management, listings
☐ hospitality             — Booking systems, guest experience
☐ logistics               — Fleet management, routing
☐ agriculture             — Crop planning, supply chain
```

### Plugins (from `.agents/plugins/`)
```
Which plugin bundles do you need?

☐ brand-establishment     — Brand identity, voice, logo, IP protection
☐ super-intelligence      — Claude Skills, researched articles, automation
```

After selection:
1. **Keep** only the selected industry folders inside `.agents/skills/`
2. **Delete** all unselected industry folders (keep `_universal/` always)
3. **Keep** only selected plugin folders inside `.agents/plugins/`

---

## Step 3: Configure the Brain

1. **Update `.agents/brain/context.md`:** Replace all `[PLACEHOLDER]` fields with the specific vision, tech stack, industry, conventions, and guardrails.
2. **Update `.agents/brain/readme.md`:** Replace the project name if needed.
3. **Clear personal folders (working, learning, tasks):** Remove example content but keep `context.md` and `readme.md`.

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

- **Daily logs** → `.agents/brain/tasks/` with date headers and ✅/🚧/🔜 sections
- **Session archives** → `.agents/brain/working/session_YYYY-MM-DD.md`
- **Learning** → `.agents/brain/learning/` with descriptive filenames and source links

---

## Step 7: Finalization

1. Create the first daily log documenting the setup.
2. Notify the founder the environment is ready.
3. Ask if they want to create project-specific skills in `.agents/skills/`.

---

## Step 8: Clone & Contribute (Show This to the User)

After setup is complete, present the following guide to the founder:

---

### 🔽 How to Get More Skills from the Community

The repo grows over time. To grab new skills others have built:

**Option A: AI-Driven (Recommended)**
1. Open [CLONE_WITH_AI.md](CLONE_WITH_AI.md)
2. Copy the contents and paste into your AI agent
3. The AI will detect what you already have and offer only new items

**Option B: Manual Git**
```bash
# 1. Add the template repo as a remote
git remote add warehouse https://github.com/sagaargroups/agentic-project-template.git

# 2. Fetch without merging
git fetch warehouse main

# 3. Copy a specific skill into your project
git checkout warehouse/main -- project-itself/.agents/skills/[industry]/[skill-name]

# 4. Or copy a specific plugin
git checkout warehouse/main -- project-itself/.agents/plugins/[plugin-name]
```

> **You only pull what you need.** Your project stays clean.

---

### 🔼 How to Contribute Your Skills Back

When you build a skill during your work and want to share it:

**Option A: Let your AI do it**
> Tell your agent: *"Run the contribution-router skill on this and submit it."*

**Option B: Manual PR**
```bash
# 1. Fork the template repo on GitHub
# 2. Clone your fork
git clone https://github.com/[your-username]/agentic-project-template.git
cd agentic-project-template

# 3. Add your skill to the correct industry folder
mkdir -p project-itself/.agents/skills/[industry]/[skill-name]
# Copy your SKILL.md into it

# 4. Push and open a PR
git checkout -b skill/[skill-name]
git add .
git commit -m "[SKILL] skill-name — one-line description"
git push origin skill/[skill-name]
```

**Contribution checklist:**
- [ ] Name is `kebab-case`, max 3 words
- [ ] `SKILL.md` has YAML frontmatter (`name`, `description`)
- [ ] Placed in the correct industry folder
- [ ] No hardcoded secrets
- [ ] PR title: `[SKILL] skill-name` or `[PLUGIN] plugin-name`

---

## Standards Reference

### Naming Standard
- Always `kebab-case`, max 3 words
- Skills = specific actions (`keyword-research`, not `seo`)
- Industry folders = domain verticals (`information-technology`, not `my-dev-stuff`)

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
