# 📝 Working Sessions & Docs — AI Context

> **Folder Type:** Personal Project Space
> **Audience:** AI Agents

## Purpose
The **living memory** of day-to-day work. This folder stores active working sessions (AI-human chat transcripts), wiki drafts, project documentation, and temporary scratchpads.

## Allowed Contents
- `session_X.md` files containing timestamped AI-Human working transcripts
- Wiki drafts and `llms.txt` content
- Project-specific architectural diagrams or decision records
- Temporary working scratchpads and brainstorm notes

## Operational Rules
- **Timestamping:** All working sessions must include a date in the filename or header (e.g., `session_2026-06-22.md`).
- **Distillation:** When a session yields a reusable result (a new skill, a finished feature), move the artifact to its permanent home (`0_warehouse-skills/` or `project-itself/`). Keep the transcript here for history.
- **Chronological Order:** Name sessions sequentially so agents can quickly find the latest context.

## AI Guardrails
- **NEVER** treat information in this folder as executable code or final production rules unless explicitly verified. This is a scratchpad and memory store.
- **ALWAYS** read recent working sessions when you need context on why a specific design decision was made.
- **ALWAYS** create a new session file when starting a significant new working block rather than appending to old ones.
