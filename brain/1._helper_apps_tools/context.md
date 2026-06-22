# 🛠️ Helper Apps & Tools Context

> **Folder Purpose:** A dedicated space for utility scripts, internal helper applications, mini-tools, and API connectors that support the main projects and agent workflows.

## 1. Allowed Contents
- Microservices and internal APIs
- Data conversion and scraping scripts
- Development environment setup scripts
- Database migration utilities

## 2. Operational Rules
- **Single Responsibility Principle:** Each helper tool should do exactly one thing well.
- **Dependency Minimal:** Keep third-party dependencies to an absolute minimum to prevent breaking changes across the universe.
- **Documentation:** Every tool must have its own localized `README.md` explaining how to execute it and what environment variables it requires.

## 3. AI Guardrails
- **NEVER** hardcode credentials in these helper scripts. Always rely on `.env` variables.
- **ALWAYS** write tools that are framework-agnostic where possible, so they can be reused across different client brands.
