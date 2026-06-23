# 📦 Warehouse: Skills & Automations — AI Context

> **Folder Type:** Community Warehouse (ever-growing)
> **Audience:** AI Agents

## Purpose
The primary warehouse for reusable AI agent skills, workflow automations, and bundled plugins. Grows over time via community contributions.

## Internal Structure
| Subfolder | What It Stores |
|-----------|---------------|
| `skills/` | Individual, single-purpose AI skills (each with `SKILL.md`) |
| `plugins/` | Bundled multi-skill packages for large workflows |
| `third-party/` | Skills cloned or adapted from external repos (preserve LICENSE) |

## Contribution Standard
- **Individual Skills** → `skills/my-skill/SKILL.md` (YAML frontmatter: `name`, `description`)
- **Plugins** → `plugins/my-plugin/plugin.json` + `skills/` subfolder
- **Third-Party** → `third-party/cloned-skill/` with original LICENSE preserved

## AI Guardrails
- **NEVER** execute an unverified skill without the human's explicit approval.
- **NEVER** delete a community-contributed skill without the founder's permission.
- **ALWAYS** update documentation when modifying a skill's behavior.
- **ALWAYS** preserve original licenses in `third-party/`.
