# ⚙️ Skills, Agents & Automations Context

> **Folder Purpose:** The central repository for all AI agent instructions, MCP configurations, custom workflow scripts, and automation blueprints. This is the "engine room" of the Sagaar-Universe.

## 1. Allowed Contents
- Agent skills (in `.md` format with YAML frontmatter)
- MCP server configurations and integrations
- CI/CD workflow templates (GitHub Actions, etc.)
- Autonomous automation scripts

## 2. Operational Rules
- **Universal Standard:** Every skill or workflow added here must follow the standard structure: Name, Purpose, Triggers, and Constraints.
- **Modularity:** Automations should be self-contained. Avoid tight coupling between disparate agent skills.
- **Testing First:** Do not deploy an automation to a live project before running a dry-run test here.

## 3. AI Guardrails
- **NEVER** execute an unverified or newly generated workflow script without the founder's explicit approval.
- **ALWAYS** update the documentation of a skill if you modify its behavior.
