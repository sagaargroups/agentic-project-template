# BFS Backend Guide — AI Coder Agent

> Read bfs_v1.html first. V1 = IndexDB (working). This = V2 serverless + remote DB.

---

## Data models

```typescript
Business {
  id: string
  type: 's1' | 's2'
  name: string
  desc: string
  market: string
  revenue: string
  capital: string
  timeline: string
  kill: string          // REQUIRED — kill condition
  edge: string
  psych?: string        // S2 only
  mcs?: string          // S2 only
  timestamp: number
}

Priority {
  id: string
  bizId: string
  type: 's1' | 's2'
  rank: number          // 1=start now, 2=after #1, 3+=future
  match: 'green' | 'yellow' | 'red'
  params: {             // survival param completion flags
    p1?: boolean
    p2?: boolean
    p3?: boolean
  }
  paramData: Record<string, string>  // all param field values
  step1: {
    knowledge: string
    resources: string
    timeline: string
    gaps: string
    verdict: 'ready' | 'partial' | 'notready'
  }
  step3: {
    version: string
    working: string
    bottleneck: string
    v2: string
    trigger: string
  }
  timestamp: number
}

Assessment {
  id: 'current'         // always single record
  scores: {
    capital: number     // 1-10
    time: number
    skill: number
    risk: number
    network: number
  }
  fields: {
    capital: string     // actual liquid amount
    runway: string
    skills: string
    motivation: string
    constraints: string
    stage: string
    backup: string
    killstate: string
  }
  triggers: {
    monthly: boolean
    quarterly: boolean
    capital: boolean
    newbiz: boolean
    failure: boolean
    custom: boolean
    customDays: number
  }
  timestamp: number
}

ConstitutionYear {
  id: string
  year: string
  bizExecute: string
  whyNow: string
  target: string
  chickenEgg: string
  enables: string
  timestamp: number
}

EcosystemConnection {
  id: string
  name: string
  hypothesis: string
  validation: string
  result: string
  status: 'hypothesis' | 'testing' | 'validated' | 'failed'
  timestamp: number
}
```

---

## API routes — 10 total

```
POST   /businesses           create
GET    /businesses           get all
PUT    /businesses/:id       update
DELETE /businesses/:id

POST   /priorities           create
GET    /priorities           get all
PUT    /priorities/:id       update (called on every param save)

GET    /assessment/current   get latest
PUT    /assessment/current   upsert

POST   /constitution         create year
GET    /constitution         get all
PUT    /constitution/:id
DELETE /constitution/:id

POST   /ecosystem            create connection
GET    /ecosystem            get all
PUT    /ecosystem/:id
DELETE /ecosystem/:id
```

All return `{ data, error }`.

---

## Audit trigger logic (implement server-side)

```typescript
// Run on GET /assessment/current
function checkAuditDue(assessment: Assessment): boolean {
  const { triggers, timestamp } = assessment;
  const now = Date.now();
  
  if (triggers.monthly && now > timestamp + 30 * 86400000) return true;
  if (triggers.quarterly && now > timestamp + 90 * 86400000) return true;
  if (triggers.custom && now > timestamp + triggers.customDays * 86400000) return true;
  
  return false;
}

// Trigger events — call PUT /assessment/current with auditDue: true when:
// - Capital field drops 30%+ vs previous assessment
// - New business added (POST /businesses)
// - Business marked failed (PUT /businesses/:id with status: 'failed')
```

---

## Survival param enforcement (backend mirror)

Frontend enforces locked sequence visually. Backend enforces in data:

```typescript
// PUT /priorities/:id
function validatePriorityUpdate(body: Partial<Priority>) {
  if (body.params?.p2 && !body.params?.p1)
    return { error: 'Cannot complete param 2 without param 1' };
  if (body.params?.p3 && !body.params?.p2)
    return { error: 'Cannot complete param 3 without param 2' };
  if (body.paramData && Object.keys(body.paramData).some(k => parseInt(k.replace('p','')) > 3)) {
    if (!body.params?.p1 || !body.params?.p2 || !body.params?.p3)
      return { error: 'Survival params must be complete before params 4-11' };
  }
  return null;
}
```

---

## Stack recommendation

```
Same as SLS V2:
- Cloudflare Workers or Vercel Edge Functions
- Supabase (fastest — auto REST API, enable it and skip writing routes)
- Drizzle ORM if building custom
```

Supabase fastest path: create 5 tables with schemas above, enable auto REST API, point frontend at it.

---

## MCP server tools

```
get_businesses(type?)          returns all businesses, optional filter by s1/s2
get_priorities()               returns prioritized list with system completion state
get_assessment()               returns current state + audit due status
get_param_data(bizId, param)   returns specific param data for a business
get_ecosystem_validated()      returns only validated connections (not hypothesis)
update_connection_status(id, status)   agent can mark connections as tested
```

Build with FastMCP (Python) or @modelcontextprotocol/sdk (Node).

---

## Frontend connection — replace these two functions

```javascript
// In bfs_v1.html, replace dbPut and dbAll with:
async function apiPut(store, obj) {
  const url = await dbGet('settings', 'apiUrl');
  const method = obj.id ? 'PUT' : 'POST';
  const endpoint = obj.id ? `${url.value}/${store}/${obj.id}` : `${url.value}/${store}`;
  return fetch(endpoint, {
    method,
    headers: {'Content-Type':'application/json'},
    body: JSON.stringify(obj)
  }).then(r => r.json()).then(r => r.data);
}

async function apiAll(store) {
  const url = await dbGet('settings', 'apiUrl');
  return fetch(`${url.value}/${store}`).then(r => r.json()).then(r => r.data);
}
```

Add storage mode check before every db call — if mode=remote, route to api functions.

---

## Hole fixes wired in — backend must preserve

| Hole | Frontend | Backend |
|------|----------|---------|
| Static self-assessment | Trigger checkboxes + event hooks | auditDue flag on GET assessment |
| Flat param weight | Survival params locked (1-3 enforced) | Validate sequence on PUT priorities |
| Assumed ecosystem synergy | Status: hypothesis→testing→validated | Never return unvalidated as confirmed |
| No kill condition | Kill field required to save business | Reject POST /businesses if kill empty |
| No domain depth test | Teach-back timer + verdict field | Reject step2 access if step1 verdict ≠ ready |

---

## V2 checklist

- [ ] Create 5 tables in Supabase
- [ ] Enable auto REST API
- [ ] Add audit trigger logic to assessment endpoint
- [ ] Add survival param validation to priorities endpoint
- [ ] Build MCP server with 6 tools
- [ ] Update 2 frontend functions (dbPut/dbAll)
- [ ] Test full flow: add business → prioritize → complete survival params → save assessment
