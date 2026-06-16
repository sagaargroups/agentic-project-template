# 🧠 The Sagaar-Universe Brain

This directory (`brain/`) is the central intelligence hub and operating system for the entire agency and all sub-brands. It contains the founder's vision, active projects, AI agent skills, and automated workflows.

**Both Humans and AI Agents must read this directory before making architectural decisions.**

## 📂 Structure
- `context.md` — The master context, vision, timeline, and playbooks.
- `0. skills-agents-workflows-automations-systems/` — AI operations & reusable agent skills.
- `1. projects-docs-&-working/` — Active projects and their specific context.
- `2. Learning-across-time/` — The founder's knowledge base and notes.
- `3. want-&-todo-checklist/` — The roadmap and backlog.

---

## 🔄 CRUD Guidelines (How to Update The Brain)

To keep the brain accurate, follow these rules when Creating, Reading, Updating, or Deleting knowledge.

### 👤 For Human Founders:
- **Create:** When you have a new idea, hypothesis, or "if X then Y" playbook, write it directly into `context.md` under the "Playbooks & Timeline" section.
- **Read:** Review `context.md` monthly to ensure the AI's understanding aligns with your current business goals.
- **Update:** If the tech stack, branding, or core mission pivots, update `context.md` immediately. The AI relies on this.
- **Delete:** Move deprecated ideas or failed experiments to a `graveyard.md` file rather than deleting them, so the AI learns from past mistakes.

### 🤖 For AI Agents:
- **Create:** When deploying a new infrastructure component or completing a major milestone, append a timestamped log to `context.md`. When learning a new repeatable task, scaffold a new skill in `0. skills-agents-workflows-automations-systems/`.
- **Read:** ALWAYS read `context.md` at the start of a new complex task to align with the founder's vision and current tech stack constraints.
- **Update:** If you refactor a core system, update the "Current State" section in `context.md` to reflect the new reality. Do NOT overwrite the "Founder's Vision".
- **Delete:** Agents are NOT permitted to delete playbooks or vision statements. If an agent detects outdated technical context, it must flag it with a `> ⚠️ REVIEW:` tag for the human founder.
