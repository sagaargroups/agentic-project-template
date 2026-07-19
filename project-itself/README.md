<div align="center">

# 🧠 Agentic Project Template

### The Operating System for Human-AI Software Development

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![AI-First](https://img.shields.io/badge/Architecture-AI--First-purple.svg)](#)

**Stop letting AI agents hallucinate your architecture. Give them a brain.**

[Quick Start](#-quick-start) · [How It Works](#-how-it-works) · [Directory Structure](#-directory-structure) · [Contributing](#-contributing)

</div>

---

## 🚀 What Is This?

This is **not** another boilerplate. This is a **structured operating system** for building software projects alongside AI coding agents (Cursor, Claude Code, Windsurf, GitHub Copilot, Antigravity, and more).

**The Problem:** AI agents are powerful, but they hallucinate frameworks, use deprecated libraries, and break your architecture because they don't understand the *rules* of your specific project.

**The Solution:** This template gives your AI agent a `brain/` — a structured directory of context files, guardrails, skills, and playbooks that tell the AI exactly what to do, what tools to use, and most importantly, **what NOT to do**.

### Traditional Repo vs. Agentic Repo

| | Traditional Repo | Agentic Repo (This Template) |
|---|---|---|
| **AI Context** | One massive README.md | Localized `context.md` in every folder |
| **Agent Rules** | None — AI guesses | `.agents/skills/` with explicit guardrails |
| **Knowledge Persistence** | Lost between sessions | `brain/learning/` accumulates over time |
| **Task Tracking** | External tools (Jira, Linear) | `brain/tasks/` with daily logs |
| **Growth Planning** | Scattered notes | `brain/think-tank/` for strategic direction |
| **Industry Skills** | Copy-paste snippets | `skills/[industry]/` organized by vertical |

---

## ⚡ Quick Start

### Option A: Selective Clone (Recommended)
Don't need the whole repo? Use our AI-powered selective clone:

1. Open [CLONE_WITH_AI.md](CLONE_WITH_AI.md)
2. Copy the entire contents
3. Paste it into your AI agent (Cursor, Claude Code, Antigravity, etc.)
4. The AI will understand your project, show you what's available, and copy only what you need

### Option B: Full Clone
```bash
git clone https://github.com/sagaargroups/agentic-project-template.git my-project
cd my-project
```

Then tell your AI agent:
> "Read `setup.md` and follow its instructions to configure this project for me."

---

## 🔍 How It Works

### The Dual-File Standard
Every folder inside `brain/` contains exactly **two files**:

| File | Audience | Purpose |
|------|----------|---------|
| `context.md` | 🤖 AI Agents | Machine-readable boundaries, allowed contents, and guardrails |
| `readme.md` | 👤 Humans | Human-readable explanation and usage guide |

### Everything Lives Inside `.agents/`
The `.agents/` directory is the single root for all intelligence:

```
.agents/
├── brain/              # 🧠 Project intelligence & memory
├── skills/             # 🌍 Industry-organized skills (The God Book)
│   ├── _universal/     #    Cross-industry skills (always needed)
│   └── [industry]/     #    Industry-specific skills
├── workflows/          # ⚡ Multi-step automation flows
├── plugins/            # 📦 Bundled multi-skill packages
└── tool-registry/      # 🔧 MCP & tool catalog (registry only)
```

---

## 📂 Directory Structure

```
agentic-project-template/
│
├── .agents/                                    # 🤖 The God Book — everything AI needs
│   │
│   ├── brain/                                  # 🧠 Project intelligence
│   │   ├── context.md                          #    Master AI context
│   │   ├── readme.md                           #    Master human README
│   │   ├── working/                            #    Day-to-day sessions & docs
│   │   ├── learning/                           #    Research & knowledge
│   │   ├── tasks/                              #    Task checklists & daily logs
│   │   └── think-tank/                         #    Growth & future planning
│   │
│   ├── skills/                                 # 🌍 Skills organized by industry
│   │   ├── _universal/                         #    Cross-industry (always needed)
│   │   │   ├── context-blueprint/              #    How to write context.md
│   │   │   ├── project-baseline/               #    Mandatory project files
│   │   │   ├── project-setup/                  #    Setup directive
│   │   │   ├── readme-blueprint/               #    How to write README.md
│   │   │   ├── warehouse-ecosystem/            #    Warehouse architecture
│   │   │   ├── contribution-router/            #    Auto-classify contributions
│   │   │   ├── agentic-skill-creator/          #    Create production skills
│   │   │   └── skill-creator/                  #    Third-party skill creator
│   │   │
│   │   ├── information-technology/             #    IT skills (UI, production, etc.)
│   │   ├── healthcare/                         #    Healthcare industry
│   │   ├── fintech/                            #    Financial technology
│   │   ├── ecommerce/                          #    E-commerce
│   │   ├── edtech/                             #    Education technology
│   │   ├── legal/                              #    Legal industry
│   │   ├── marketing-media/                    #    Marketing & media
│   │   ├── manufacturing/                      #    Manufacturing
│   │   ├── real-estate/                        #    Real estate
│   │   ├── hospitality/                        #    Hospitality
│   │   ├── logistics/                          #    Logistics
│   │   └── agriculture/                        #    Agriculture
│   │
│   ├── workflows/                              # ⚡ Automation workflows
│   │   └── _universal/                         #    Cross-industry workflows
│   │
│   ├── plugins/                                # 📦 Bundled skill packages
│   │   ├── brand-establishment/                #    Brand identity & prelaunch
│   │   └── super-intelligence/                 #    Claude Skills, research, automation
│   │
│   └── tool-registry/                          # 🔧 MCP & tool catalog
│       └── registry.json                       #    Central tool registry
│
├── .gitignore
├── CLONE_WITH_AI.md                            # 🤖 AI-driven selective clone prompt
├── CONTRIBUTING.md                             # 🤝 How to contribute
├── LICENSE                                     # 📄 MIT License
├── README.md                                   # 📖 This file
└── setup.md                                    # 🤖 AI agent setup directive
```

---

## 🏗️ Industry Coverage

The `skills/` directory is organized by industry. Each industry folder contains skills, best practices, and workflows specific to that vertical. **This grows over time** as our team researches and the community contributes.

| Industry | Status | Coverage |
|---|---|---|
| `_universal` | 🟢 Active | 8 skills — context, setup, baselines, skill creation |
| `information-technology` | 🟢 Active | Production standards, UI system |
| `healthcare` | 🟡 Growing | Clinical workflows, medicine categories |
| `fintech` | 🟡 Growing | Compliance, trading workflows |
| `ecommerce` | 🟡 Growing | Store setup, fulfillment |
| `edtech` | 🟡 Growing | Learning management |
| `legal` | 🟡 Growing | Contract analysis, compliance |
| `marketing-media` | 🟡 Growing | Content strategy, SEO |
| `manufacturing` | 🟡 Growing | Supply chain, quality control |
| `real-estate` | 🟡 Growing | Property management |
| `hospitality` | 🟡 Growing | Booking systems |
| `logistics` | 🟡 Growing | Fleet management |
| `agriculture` | 🟡 Growing | Crop planning |

> **Don't see your industry?** Open a PR or issue — we'll add it.

---

## 🤝 Contributing

We actively welcome contributions — especially to the **skills** and **plugins**!

### What You Can Contribute
- **🤖 New Skills** → Add to `skills/[industry]/` or `skills/_universal/`
- **📦 New Plugins** → Add to `plugins/`
- **🔧 Tool Registry Entries** → Add to `tool-registry/registry.json`
- **📝 Documentation** → PRs welcome
- **💡 Ideas** → Open an issue or add to `brain/think-tank/`

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 🌟 Why This Exists

AI coding agents are transforming software development. But without structure, they create chaos — hallucinating frameworks, using deprecated APIs, and breaking architecture they don't understand.

This template introduces a **paradigm shift**: instead of hoping your AI "figures it out," you give it an explicit operating system. Just like `.gitignore` tells Git what to ignore, `context.md` tells AI how to behave.

**The goal:** Make `context.md` the industry standard for AI-aware repositories.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) — use it, fork it, build on it, share it.

---

<div align="center">

**Built for the AI era. By humans, with AI, for everyone.**

⭐ Star this repo if you believe AI agents deserve better context.

</div>
