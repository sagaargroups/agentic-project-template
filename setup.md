# 🤖 AI Agent Setup Directive

**ATTENTION AI AGENT:** You have just been given access to the Agentic Project Template. Your job is to transform this generic template into a fully-configured, project-specific environment. Follow the exact sequence below.

> **CRITICAL RULE:** Do NOT delete the `brain/` structure or `.agents/` directory. They must remain intact as the operating system for this project.

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

## Step 2: Configure the Brain

Once you have the answers, perform the following actions:

1. **Update `brain/context.md`:** Replace all `[PLACEHOLDER]` fields with the specific vision, tech stack, industry, conventions, and guardrails for this project.
2. **Update `brain/readme.md`:** Replace the project name if needed.
3. **Leave warehouse folders (0, 1) intact:** These contain community-contributed skills and tools that are project-agnostic.
4. **Clear personal folders (2, 3, 4):** Remove any example/template content from `2_working/`, `3_learning/`, and `4_tasks-and-logs/` — but keep the `context.md` and `readme.md` files.

---

## Step 3: Initialize the Project

1. **Initialize Fresh Git:**
   ```bash
   rm -rf .git
   git init
   ```
2. **Rename the Root Directory** (if needed): Rename to `[Project-Name]`.
3. **Set up `project-itself/`:** If the codebase lives here, scaffold the appropriate structure for the chosen tech stack.

---

## Step 4: Scaffold Brand Architecture (Optional)

If this is a brand/product project, create the following folder tree inside the root or `project-itself/`:

```text
├── brand-identity/    (Logo, colors, typography, brand voice)
├── registration/      (Account setup checklists)
├── docs/              (Architecture and organization)
├── wiki/              (Public-facing docs, llms.txt)
├── seo/               (Keywords, listings, GEO)
└── ops/               (Infrastructure, legal, security)
```

---

## Step 5: Daily Workflow Setup

Explain the following workflow to the founder:

### Daily Contribution Tracking
After each working session, create or update a daily log in `brain/4_tasks-and-logs/`:
```markdown
## [YYYY-MM-DD]
### ✅ Completed
- [What was accomplished]

### 🚧 In Progress
- [What's being worked on]

### 🔜 Next
- [What's planned]
```

### Working Session Archiving
Save significant AI-human working sessions as `session_YYYY-MM-DD.md` in `brain/2_working/`.

### Learning Accumulation
When discovering useful patterns, frameworks, or research, save them in `brain/3_learning/` with clear filenames and source links.

---

## Step 6: Finalization

1. **Create the first daily log** in `brain/4_tasks-and-logs/` documenting the setup.
2. **Notify the founder** that the environment is fully scaffolded and ready.
3. **Ask the founder** if they want to create any project-specific skills in `.agents/skills/`.

---

## Agent Skill Standard

When creating new skills for `.agents/skills/`, follow this format:

```
skill-name/
└── SKILL.md
```

### SKILL.md Format:
```yaml
---
name: skill-name
description: "One-line description of what this skill does."
---

# Skill Title

[Detailed instructions for the AI agent...]
```
