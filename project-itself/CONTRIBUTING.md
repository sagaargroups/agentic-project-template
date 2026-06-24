# 🤝 Contributing to the Agentic Project Template

Thank you for helping build the future of AI-first software development! This guide explains how to contribute to the **warehouse folders** — the community-growing parts of this template.

---

## What You Can Contribute

| Contribution Type | Where It Goes | Format |
|---|---|---|
| 🤖 Agent Skills | `brain/0_warehouse-skills/` | `SKILL.md` with YAML frontmatter |
| 🔧 Helper Tools | `brain/1_warehouse-tools/` | Folder with `README.md` |
| 📝 Documentation | Anywhere | Markdown files |
| 💡 Ideas & Proposals | `brain/think_tank/` | Markdown files |
| 🐛 Bug Reports | GitHub Issues | Issue template |

---

## Contributing a New Skill

Skills are instructions that tell AI agents *how to behave*. They live in `brain/0_warehouse-skills/`.

### 1. Create the Folder
```
brain/0_warehouse-skills/
└── your-skill-name/
    ├── SKILL.md          # Required — main instruction file
    ├── README.md          # Optional — human-readable guide
    ├── scripts/           # Optional — helper scripts
    └── examples/          # Optional — usage examples
```

### 2. Write the SKILL.md
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

### 3. Submit a PR
- Branch from `main`
- Title: `[SKILL] your-skill-name`
- Include a brief description of what the skill does and when to use it

---

## Contributing a New Tool

Tools are runnable utilities that solve specific problems. They live in `brain/1_warehouse-tools/`.

### 1. Create the Folder
```
brain/1_warehouse-tools/
└── your-tool-name/
    ├── README.md          # Required — what it does, how to run it
    ├── [source files]     # The actual tool code
    └── .env.example       # Required if tool needs configuration
```

### 2. Write the README.md
Include:
- **What it does** (one paragraph)
- **Prerequisites** (runtime, dependencies)
- **How to run it** (exact commands)
- **Environment variables** (if any)

### 3. Submit a PR
- Branch from `main`
- Title: `[TOOL] your-tool-name`
- Include a brief description and usage example

---

## Code Standards

- **No hardcoded secrets.** Use `.env` files and include `.env.example`.
- **No framework lock-in.** Skills and tools should be as framework-agnostic as possible.
- **Self-contained.** Each skill/tool should work independently.
- **Documented.** If a human can't understand it, it's not ready to merge.

---

## Pull Request Process

1. Fork the repository
2. Create a feature branch (`git checkout -b skill/my-new-skill`)
3. Add your contribution to the appropriate warehouse folder
4. Ensure your contribution includes all required files
5. Submit a Pull Request with a clear description
6. Wait for review — maintainers will test with AI agents before merging

---

## Questions?

Open an issue or start a discussion. We're building this together.
