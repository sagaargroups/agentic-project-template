# 🤝 Contributing to the Agentic Project Template

Thank you for helping build the future of AI-first software development! This guide explains how to contribute skills, plugins, and tools.

---

## What You Can Contribute

| Contribution Type | Where It Goes | Format |
|---|---|---|
| 🤖 Industry Skills | `.agents/skills/[industry]/` | `SKILL.md` with YAML frontmatter |
| 🤖 Universal Skills | `.agents/skills/_universal/` | `SKILL.md` with YAML frontmatter |
| 📦 Plugins | `.agents/plugins/` | `plugin.json` + `skills/` subfolder |
| 🔧 Tool Registry | `.agents/tool-registry/registry.json` | JSON entry |
| 📝 Documentation | Anywhere | Markdown files |
| 💡 Ideas & Proposals | `.agents/brain/think-tank/` | Markdown files |
| 🐛 Bug Reports | GitHub Issues | Issue template |

---

## Contributing a New Skill

Skills are instructions that tell AI agents *how to behave*. They live in `.agents/skills/`.

### 1. Pick the Right Industry Folder
| If your skill is for... | Place it in... |
|---|---|
| Any project (cross-industry) | `skills/_universal/` |
| Software development | `skills/information-technology/` |
| Healthcare | `skills/healthcare/` |
| Finance | `skills/fintech/` |
| E-commerce | `skills/ecommerce/` |
| Education | `skills/edtech/` |
| Legal | `skills/legal/` |
| Marketing/Media | `skills/marketing-media/` |
| Manufacturing | `skills/manufacturing/` |
| Real Estate | `skills/real-estate/` |
| Hospitality | `skills/hospitality/` |
| Logistics | `skills/logistics/` |
| Agriculture | `skills/agriculture/` |
| New industry | Propose it in your PR |

### 2. Create the Folder
```
.agents/skills/[industry]/
└── your-skill-name/
    ├── SKILL.md          # Required — main instruction file
    ├── README.md          # Optional — human-readable guide
    ├── scripts/           # Optional — helper scripts
    └── examples/          # Optional — usage examples
```

### 3. Write the SKILL.md
```yaml
---
name: your-skill-name
description: "One-line description of what this skill does."
---

# Your Skill Title

## Purpose
What does this skill do and when should an AI agent activate it?

## Instructions
Step-by-step instructions for the AI agent...

## Guardrails
- What the agent should NEVER do when using this skill
- What the agent should ALWAYS do
```

### 4. Submit a PR
- Branch from `main`
- Title: `[SKILL] your-skill-name`
- Include a brief description of what the skill does and when to use it

---

## Contributing a New Plugin

Plugins bundle multiple skills for a domain workflow.

### 1. Create the Folder
```
.agents/plugins/
└── your-plugin-name/
    ├── plugin.json        # Required — metadata
    └── skills/
        ├── skill-a/
        │   └── SKILL.md
        └── skill-b/
            └── SKILL.md
```

### 2. Write plugin.json
```json
{
  "name": "your-plugin-name",
  "description": "One-line description.",
  "skills": ["skill-a", "skill-b"]
}
```

### 3. Submit a PR
- Title: `[PLUGIN] your-plugin-name`

---

## Adding a Tool to the Registry

Add an entry to `.agents/tool-registry/registry.json`:

```json
{
  "name": "tool-name",
  "description": "What it does.",
  "type": "mcp|cli|api",
  "setup_url": "https://...",
  "docs_url": "https://..."
}
```

---

## Code Standards

- **No hardcoded secrets.** Use `.env` files and include `.env.example`.
- **No framework lock-in.** Skills should be as framework-agnostic as possible.
- **Self-contained.** Each skill/tool should work independently.
- **Documented.** If a human can't understand it, it's not ready to merge.

---

## Pull Request Process

1. Fork the repository
2. Create a feature branch (`git checkout -b skill/my-new-skill`)
3. Add your contribution to the appropriate folder
4. Ensure your contribution includes all required files
5. Submit a Pull Request with a clear description
6. Wait for review — maintainers will test with AI agents before merging

---

## Questions?

Open an issue or start a discussion. We're building this together.
