# SLS Backend Guide — AI Coder Agent

> Read the frontend HTML first. Then build this. V1 = local IndexDB (already working). This guide = V2 serverless + remote DB.

---

## What the frontend expects

Two things from your backend:

**1. REST API** — base URL stored in settings → `apiUrl`
**2. MCP server** — URL stored in settings → `mcpUrl`

Frontend switches between local/remote in settings. When remote is active, replace every `dbPut/dbGet/dbGetAll/dbDelete` call with `fetch()` to your API.

---

## Data models

```typescript
// Session — one learning run through all 7 stages
Session {
  id: string           // timestamp string
  domain: string       // what they're learning
  status: 'active' | 'complete' | 'rejected' | 'filed'
  stage: string        // current stage name
  timestamp: number
  gateRule: string
  clarityKnown: string
  clarityGaps: string
  skelProblem: string
  skelMetric: string
  skelBreakdown: string
  operatingChecklist: string  // recurring tasks ordered frequency→consequence
  top20Vocab: string          // minimum viable language
  mandatoryResources: string  // each mapped to a checklist item
  bestPractice: string        // industry baseline standard
  resNotes: string
  principle: string    // compressed paragraph
  theorySecond: string
  practiceA1/A2/A3: string
  measureWorked: string
  measureFailed: string
  measureType: string
  measureVerdict: string
  md: string           // full markdown output
}

// Skill — stored principle file
Skill {
  id: string
  domain: string
  principle: string
  md: string           // full markdown
  verdict: string
  timestamp: number
}
```

---

## API routes — 6 total

```
POST   /sessions          create session
GET    /sessions          get all
PUT    /sessions/:id      update (called on every stage advance)
DELETE /sessions/:id

POST   /skills            save skill file
GET    /skills            get all
GET    /skills/:id        get one
DELETE /skills/:id
```

All return `{ data, error }`. No auth in V2 — add API key header later.

---

## Stack recommendation (serverless)

```
Runtime:    Cloudflare Workers or Vercel Edge Functions
DB:         PlanetScale (MySQL) or Supabase (Postgres)
ORM:        Drizzle (lightweight, edge-compatible)
Files:      R2 or Supabase Storage (for .md exports)
```

Alternatively — pure Supabase. Enable REST auto-generated API, point frontend directly at it. Fastest path to working.

---

## MCP server — what it does

Exposes your skill library to any AI agent (Claude, GPT, local LLM).

```
Tools to expose:
  get_skills()              returns all skill files as markdown
  get_skill(domain)         semantic search by domain name
  add_skill(skill_obj)      agent writes a new skill file
  query_principle(query)    returns matching principles
```

Build with: **FastMCP** (Python) or **@modelcontextprotocol/sdk** (Node).

Point it at the same DB as your API.

The agent reads this MCP, finds the right skill file for the situation, and applies it. That is "train your AI agent to become the next you."

---

## How to connect to frontend

In `settings.js` (inside the HTML), find these two functions and replace:

```javascript
// BEFORE (local)
async function dbPut(store, obj) { ... indexedDB ... }
async function dbGetAll(store) { ... indexedDB ... }

// AFTER (remote) — add alongside, switch on storageMode
async function apiPut(store, obj) {
  const url = await getSetting('apiUrl');
  return fetch(`${url}/${store}/${obj.id}`, {
    method: 'PUT',
    headers: {'Content-Type':'application/json'},
    body: JSON.stringify(obj)
  }).then(r => r.json());
}

async function apiGetAll(store) {
  const url = await getSetting('apiUrl');
  return fetch(`${url}/${store}`).then(r => r.json()).then(r => r.data);
}
```

---

## Trap fixes wired into backend (keep these)

| Trap | Frontend | Backend |
|------|----------|---------|
| Gate bypass | 3 checkboxes + hard rule field | log every gate rejection with reason |
| Self-deception | 2min teach-back timer | store timer_completed boolean |
| Nodding student | challenge generator | store challenge_responses, flag if empty |

Log all three. Surface in a `/stats` endpoint later for self-audit.

---

```
Stage map: gate→0, orient→1, clarity→2, skeleton→3, research→4, compress→5, test→6, measure→7, filed→8
```

- [ ] Pick stack (Supabase fastest)
- [ ] Create sessions + skills tables using models above
- [ ] Deploy 6 API routes
- [ ] Build MCP server with 4 tools
- [ ] Update frontend storage toggle to call API
- [ ] Test: run one full session end-to-end, check DB, export .md

That is the complete V2. Start with Supabase auto-API and you skip writing routes entirely.
