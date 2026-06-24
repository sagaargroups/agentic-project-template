# 🔌 Plugins (Bundled Skills)

Plugins are **bundles of multiple skills** packaged together for one big workflow or domain. When a single skill isn't enough, a plugin combines several into a cohesive package.

```
plugins/
└── my-plugin/
    ├── plugin.json       # Plugin metadata (name, description, skills list)
    ├── skills/
    │   ├── skill-a/
    │   │   └── SKILL.md
    │   └── skill-b/
    │   │   └── SKILL.md
    └── README.md         # Human guide for the entire plugin
```

**Example use cases:**
- A "Full-Stack Scaffold" plugin bundling frontend + backend + database skills
- A "SEO Suite" plugin bundling keyword research + content optimization + analytics skills
- A "DevOps Pipeline" plugin bundling CI/CD + monitoring + deployment skills
