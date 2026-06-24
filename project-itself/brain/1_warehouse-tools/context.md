# 🔧 Warehouse: Helper Apps & Tools — AI Context

> **Folder Type:** Community Warehouse (ever-growing)
> **Audience:** AI Agents

## Purpose
The secondary warehouse for standalone utility scripts, helper applications, and bundled tool suites. Grows over time via community contributions.

## Internal Structure
| Subfolder | What It Stores |
|-----------|---------------|
| `tools/` | Individual, single-purpose helper utilities |
| `plugins/` | Bundled multi-tool packages for complete workflows |
| `third-party/` | Tools cloned or adapted from external repos (preserve LICENSE) |

## Contribution Standard
- **Individual Tools** → `tools/my-tool/README.md` + source files + `.env.example`
- **Plugins** → `plugins/my-suite/README.md` + tool subfolders
- **Third-Party** → `third-party/cloned-tool/` with original LICENSE preserved

## AI Guardrails
- **NEVER** hardcode credentials. Always use `.env` variables.
- **NEVER** delete a community-contributed tool without the founder's permission.
- **ALWAYS** include `.env.example` if the tool requires configuration.
- **ALWAYS** preserve original licenses in `third-party/`.
