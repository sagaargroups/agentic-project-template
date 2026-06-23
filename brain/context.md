# 🧠 System Context & Operational Handbook

> **Last Updated:** [DATE]
> **Project:** [PROJECT NAME]

## 1. Industry & Domain
* **Core Industry:** [e.g., FinTech, HealthTech, E-Commerce, Logistics, EdTech, SaaS]
* **Target Audience:** [e.g., B2B Enterprise Admins, B2C Mobile Users, Internal Teams]
* **Mission Critical Focus:** [e.g., Data Privacy (HIPAA/GDPR), Low-Latency, High Accessibility]

## 2. Technology Stack & Ecosystem
* **Core Language/Runtime:** [e.g., TypeScript Node.js v20, Python 3.11, Rust, Go]
* **Primary Frameworks:** [e.g., Next.js v15, FastAPI, Spring Boot, React Native]
* **Data Layer:** [e.g., PostgreSQL via Prisma, MongoDB, Redis, AWS S3]
* **Package Manager / Build Tool:** [e.g., pnpm, npm, poetry, gradle, cargo]

## 3. Architecture & Code Conventions
* **Design Pattern:** [e.g., Clean Architecture, Microservices, DDD, Monolith]
* **Type Safety:** [e.g., Strict TypeScript (no 'any'), Pydantic validation]
* **Naming Conventions:** [e.g., camelCase variables, PascalCase components, snake_case DB columns]
* **File Structure Rule:** [e.g., Feature-based folders, Flat src/ components]

## 4. Local Commands & Core Workflows
* **Install Dependencies:** `[e.g., pnpm install]`
* **Run Local Server:** `[e.g., npm run dev]`
* **Execute Tests:** `[e.g., pytest, npm run test]`
* **Database Migration:** `[e.g., npx prisma migrate dev]`

## 5. AI Guardrails (What NOT to Do)
* **Never Do This:** [e.g., Never hardcode API keys, Never use inline styles]
* **Deprecations:** [e.g., Do not use Axios; use native fetch]
* **Security Constraints:** [e.g., All inputs must pass validation middleware]

## 6. Playbooks (If/Then Scenarios)
*This section dictates how AI agents should react to specific triggers.*

- **If the AI Agent is confused or lacks context:**
  1. PAUSE and ask the human for clarification.
  2. Once clarified, UPDATE this `context.md` so the question never needs to be asked again.

- **If a new feature is being built:**
  1. Check `4_tasks-and-logs/` for the relevant task.
  2. Check `3_learning/` for any prior research on the topic.
  3. Begin implementation inside `project-itself/`.

- **If a reusable pattern is discovered:**
  1. Extract it into a new skill inside `0_warehouse-skills/skills/`.
  2. Document it with a `SKILL.md` following the standard format.
