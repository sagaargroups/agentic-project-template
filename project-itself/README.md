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
| **Knowledge Persistence** | Lost between sessions | `brain/3_learning/` accumulates over time |
| **Task Tracking** | External tools (Jira, Linear) | `brain/4_tasks-and-logs/` with daily logs |
| **Growth Planning** | Scattered notes | `brain/think_tank/` for strategic direction |
| **Community Sharing** | Copy-paste snippets | Warehouse folders for skills & tools |

---

## ⚡ Quick Start

### 1. Clone the Template
```bash
git clone https://github.com/[your-username]/agentic-project-template.git my-project
cd my-project
```

### 2. Let Your AI Agent Set It Up
Open the project in your AI coding environment (Cursor, Antigravity, etc.) and tell your agent:

> "Read `setup.md` and follow its instructions to configure this project for me."

Your AI will ask you a few questions (project name, tech stack, vision), then automatically:
- Update all context files with your project-specific info
- Initialize a fresh Git repository
- Scaffold the brand architecture
- Prepare the brain for your project's lifecycle

### 3. Start Building
Your project codebase goes inside `project-itself/` (or use the root as the parent). The `brain/` grows with you — accumulating skills, learning, and context over time.

---

## 🔍 How It Works

### The Dual-File Standard
Every folder in `brain/` contains exactly **two files**:

| File | Audience | Purpose |
|------|----------|---------|
| `context.md` | 🤖 AI Agents | Machine-readable boundaries, allowed contents, and guardrails |
| `readme.md` | 👤 Humans | Human-readable explanation and usage guide |

This means your AI agent always knows the rules, and you always know what's going on.

### The Brain Architecture
```
brain/
├── context.md              # 🎯 Master context (tech stack, vision, guardrails)
├── readme.md               # 📖 Human guide to the brain
│
├── 0_warehouse-skills/     # 📦 Community-contributed AI skills & automations
├── 1_warehouse-tools/      # 🔧 Community-contributed helper apps & scripts
│
├── 2_working/              # 📝 Day-to-day working sessions & docs
├── 3_learning/             # 🔬 Persistent research & knowledge
├── 4_tasks-and-logs/       # 📋 Task checklists & daily contribution logs
│
└── think_tank/             # 💡 Growth direction & future possibilities
```

### Warehouses vs. Personal Space
- **Warehouses (0, 1)** are **community-growing**. They expand as contributors add new skills and tools. Think of them as shared libraries that get better over time.
- **Personal Folders (2, 3, 4)** are **your project's private memory**. They grow as your project evolves.
- **Think Tank** is the strategic layer for planning your project's future.

---

## 📂 Directory Structure

```
agentic-project-template/
│
├── .agents/
│   └── skills/                      # 🤖 AI agent skill definitions
│       ├── global-context-blueprint/ #    How to write context.md files
│       ├── project-baseline/         #    Mandatory files every project needs
│       ├── project-setup/            #    The setup directive skill
│       └── readme-blueprint/         #    How to write README.md files
│
├── brain/                           # 🧠 The project operating system
│   ├── context.md                   #    Master AI context
│   ├── readme.md                    #    Master human README
│   ├── 0_warehouse-skills/          # 📦 Community skills (growing)
│   ├── 1_warehouse-tools/           # 🔧 Community tools (growing)
│   ├── 2_working/                   # 📝 Working sessions & docs
│   ├── 3_learning/                  # 🔬 Research & knowledge
│   ├── 4_tasks-and-logs/            # 📋 Tasks & daily logs
│   └── think_tank/                  # 💡 Growth & future planning
│
├── project-itself/                  # 🏗️ Your actual codebase
│
├── .gitignore                       #    Git exclusion rules
├── CONTRIBUTING.md                  #    How to contribute skills & tools
├── LICENSE                          #    MIT License
├── README.md                        #    This file
└── setup.md                         #    🤖 AI agent setup directive
```

---

## 🏗️ Project Codebase

This is where your actual project codebase lives.

### Options
You have two ways to organize your code:

#### Option A: Code Inside This Folder
Place your entire codebase here. This keeps a clean separation between your project code and the brain/ operating system.

```
project-itself/
├── src/
├── package.json
├── ...
```

#### Option B: Root as Parent
Use the repository root as your project root. In this case, `brain/` and `.agents/` sit alongside your `src/`, `package.json`, etc.

Your AI agent will ask you which option you prefer during the `setup.md` configuration.

---

## 🤝 Contributing

We actively welcome contributions — especially to the **warehouse folders**!

### What You Can Contribute
- **🤖 New Skills** → Add to `brain/0_warehouse-skills/`
- **🔧 New Tools** → Add to `brain/1_warehouse-tools/`
- **📝 Documentation improvements** → PRs welcome
- **💡 Ideas** → Open an issue or add to `brain/think_tank/`

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines and format standards.

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
