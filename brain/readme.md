# 🧠 The Brain

This directory is the **central intelligence hub and operating system** for this project. It is designed for both **humans** and **AI agents** to read, write, and maintain.

> **Rule:** Both humans and AI agents must read `context.md` in this directory before making any architectural decisions.

## 📂 Structure

| Folder | Type | Purpose |
|--------|------|---------|
| `context.md` | 🤖 AI | Master context, vision, tech stack, guardrails, and playbooks |
| `readme.md` | 👤 Human | This file — explains the brain to humans |
| `0_warehouse-skills/` | 📦 Warehouse | Community-contributed agent skills, workflows, and automations |
| `1_warehouse-tools/` | 🔧 Warehouse | Community-contributed helper apps, scripts, and utilities |
| `2_working/` | 📝 Personal | Day-to-day working sessions, docs, wiki drafts |
| `3_learning/` | 🔬 Personal | Persistent research, learning, and knowledge accumulation |
| `4_tasks-and-logs/` | 📋 Personal | Task checklists, daily logs, and contribution records |
| `think_tank/` | 💡 Strategic | Growth direction, future possibilities, brainstorms |

### Warehouse Internal Structure
Both warehouses (`0` and `1`) share the same internal organization:

| Subfolder | What It Stores |
|-----------|---------------|
| `skills/` or `tools/` | Individual, single-purpose items |
| `plugins/` | Bundled multi-item packages for large workflows |
| `third-party/` | Items cloned or adapted from external sources |

### Warehouses vs. Personal Folders
- **Warehouses (0, 1):** Community-growing shared libraries. They expand as contributors add new skills and tools.
- **Personal Folders (2, 3, 4):** Your project's private memory. They grow as your project evolves.
- **Think Tank:** Strategic layer — plan the project's future direction.

---

## 🔄 CRUD Guidelines

### 👤 For Human Founders
- **Create:** Write ideas, playbooks, and "if X then Y" scenarios into `context.md`.
- **Read:** Review `context.md` monthly to ensure the AI's understanding matches your goals.
- **Update:** If tech stack, branding, or mission pivots, update `context.md` immediately.
- **Delete:** Move deprecated ideas to a `graveyard.md` rather than deleting — so the AI learns from past decisions.

### 🤖 For AI Agents
- **Create:** When completing a milestone, log it in `4_tasks-and-logs/`. When learning a repeatable task, create a skill in `0_warehouse-skills/skills/`.
- **Read:** ALWAYS read `context.md` at the start of every complex task.
- **Update:** If you refactor a core system, update `context.md`. Do NOT overwrite the human's vision.
- **Delete:** Agents are NOT permitted to delete playbooks or vision statements. Flag outdated content with `> ⚠️ REVIEW:` for the human founder.

---

## 📏 The Dual-File Standard

Every folder inside `brain/` must contain exactly two files:

| File | Audience | Purpose |
|------|----------|---------|
| `context.md` | 🤖 AI Agents | Machine-readable operational boundaries, allowed contents, and guardrails |
| `readme.md` | 👤 Humans | Human-readable explanation of what this folder is for and how to use it |
