# Intelligence Agency OS — System Guide
> For AI coding agent. Read fully before writing any code.
> Stack decisions are final. Do not substitute.

---

## Vision

A self-conscious project ecosystem. Every base project serves itself and any calling project simultaneously. The system reads, writes, versions, and logs itself. Built in layers — each layer functional before the next begins.

---

## Layer 1 — UI Stack

### Framework
- **React 18** with Vite
- **TypeScript** strict mode
- **TailwindCSS v3** — utility only, no component libraries

### Typography
- Display: `Syne` (weights 400, 600, 800)
- Mono: `Syne Mono` (weight 400)
- Body: `DM Sans` (weights 300, 400, 500)
- Load via Google Fonts

### Color tokens — define in `tailwind.config.ts`
```
bg:       #070809
surface:  #0e1014
border:   #1a1e26
borderH:  #252c38
amber:    #c8901a
amberDim: #6e4f0e
amberGlow:#c8901a0f
teal:     #1a9a78
tealDim:  #0e5442
tealGlow: #1a9a780a
purple:   #7c64c8
purpleDim:#4a3a7a
red:      #b83c3c
green:    #28945a
text:     #dcd8d2
text2:    #757068
text3:    #32302c
```

### Component library — build these, use nowhere else
```
Button       variants: primary | ghost | danger | teal | purple | sm
Card         variants: default | active | amber | teal
Field        label + input/textarea/select + error
Badge        variants: learn | build | log | pattern | version
ProgressBar  step-based, 3-8 steps
Modal        overlay + container, no position:fixed
Pill         selectable tag, toggle on/off
Alert        variants: warn | success | error
Spinner      14px, border animation
MDPreview    monospace, scrollable, max-height 320px
TreeNode     expandable, shows children, rename inline
```

### Layout
- Sidebar: 210px fixed, sticky, full height
- Main: flex-1, max-width 900px, padding 36px 40px
- Two-column grid: `grid-cols-2 gap-3` for forms
- Responsive breakpoint: collapse sidebar at 768px

---

## Layer 2 — Storage Architecture

### Entity schema — fixed envelope + flexible body
Every stored object follows this exact shape:

```typescript
interface Entity {
  // FIXED ENVELOPE — never changes
  id:         string       // {type}_{ulid}
  type:       EntityType
  status:     'active' | 'archived' | 'draft'
  project_id: string | null
  parent_id:  string | null   // for nested items
  version:    number          // starts at 1
  tags:       string[]
  links:      Link[]
  created_at: number          // Date.now()
  updated_at: number
  created_by: string          // 'user' | agent id

  // FLEXIBLE BODY — varies by type
  body:       Record<string, unknown>
}

interface Link {
  id:   string
  type: 'parent' | 'child' | 'derived_from' | 'related' | 'calls'
}

type EntityType =
  | 'project'       // base project or brand project
  | 'skill'         // from learning sessions
  | 'wiki_page'     // project wiki entry
  | 'skill_file'    // .md skill file
  | 'session'       // work session log
  | 'research'      // research document
  | 'process'       // SOP / process document
  | 'version_log'   // version history entry
  | 'file_node'     // folder or file in file tree
  | 'pattern'       // AI-detected pattern
```

### ID convention
```typescript
// ulid-style: type + timestamp + random
function mkId(type: string): string {
  return `${type}_${Date.now()}_${Math.random().toString(36).slice(2, 8)}`
}
// Examples:
// project_1720000000000_a3f9kx
// skill_file_1720000001000_b8m2pz
// wiki_page_1720000002000_c4n7qr
```

### IndexDB — V1 local
```typescript
// Database name: IOS_V1  version: 1
// Stores and their indexes:

entities:
  keyPath: 'id'
  indexes:
    - 'type'        (unique: false)
    - 'project_id'  (unique: false)
    - 'parent_id'   (unique: false)
    - 'status'      (unique: false)
    - 'created_at'  (unique: false)
    - 'tags'        (multiEntry: true)

settings:
  keyPath: 'key'

patterns:
  keyPath: 'id'
```

### Query helpers — implement all of these
```typescript
getById(id: string): Promise<Entity>
getByType(type: EntityType): Promise<Entity[]>
getByProject(projectId: string): Promise<Entity[]>
getByProjectAndType(projectId: string, type: EntityType): Promise<Entity[]>
getChildren(parentId: string): Promise<Entity[]>
getByTag(tag: string): Promise<Entity[]>
putEntity(entity: Entity): Promise<void>
deleteEntity(id: string): Promise<void>
archiveEntity(id: string): Promise<void>  // sets status: 'archived'
```

### File tree — stored as entities
```typescript
// Every folder or file is a file_node entity
// body shape for file_node:
{
  name:      string       // display name
  node_type: 'folder' | 'skill_md' | 'wiki_md' | 'process_md' | 'research_md'
  content:   string       // markdown content (files only)
  path:      string       // computed: parent names joined by '/'
}
// parent_id links to parent folder or project root
// Supports: rename (update body.name), move (update parent_id), delete, create
```

---

## Layer 3 — Feature Modules

### Module 1: Project Manager
Every project is an entity with `type: 'project'`.

```typescript
// body shape for project entity:
{
  name:         string
  category:     'base' | 'brand' | 'research' | 'presence' | 'process'
  description:  string
  kill_condition: string    // required — when to shut this down
  serves:       string[]    // which other projects this base project serves
  status_note:  string      // current state in one line
}
```

Two project categories:
- **Base projects** — serve themselves and any calling project (researcher, documenter, process builder, presence builder)
- **Regular projects** — consume base projects to grow (brand launches, commercial firms, campaigns)

Entry criteria before project is created:
1. Kill condition defined
2. Category selected
3. At least one outcome condition written
4. If consuming base projects — those base projects must exist first

### Module 2: File Tree (per project)
Each project has its own file tree. File nodes are entities with `parent_id` pointing to parent folder.

Operations to implement:
```
CREATE folder      — new file_node with node_type: 'folder'
CREATE file        — new file_node with content
RENAME             — update body.name inline
MOVE               — update parent_id
DELETE             — archive entity + all children
EXPORT single      — download as .md
EXPORT folder      — download as .zip of .md files
IMPORT .md file    — parse and store as file_node
```

File types and their icons (use Tabler):
```
folder        ti-folder
skill_md      ti-brain       (amber)
wiki_md       ti-book        (teal)
process_md    ti-list-check  (purple)
research_md   ti-microscope  (default)
```

### Module 3: Wiki (per project)
Wiki pages are entities with `type: 'wiki_page'` and `project_id`.

Each wiki page:
```typescript
body: {
  title:    string
  content:  string    // markdown
  section:  string    // grouping label
  order:    number    // display order within section
}
```

Wiki operations:
- Create page
- Edit content (full markdown editor — textarea with preview toggle)
- Organize by section
- Link between pages via `[[page title]]` syntax (stored as `related` link)
- Export all wiki as single .md file

### Module 4: Skill Files (per project)
Skill files are the output of learning. They are `file_node` entities with `node_type: 'skill_md'`.

Fixed structure for every skill file .md:
```markdown
# {domain}
> project: {project_name} · version: {n} · date: {date}

---

## Core problem
{what problem this domain solves}

## Metric of truth
{how this domain measures success}

## Breakdown point
{where this lens fails}

---

## Principle
{compressed one-paragraph principle}

## Conditions it works under
{specific contexts}

## Conditions it fails under
{specific contexts}

## Second-order effects
{what happens downstream}

---

## Version history
v1 — {date} — initial
```

### Module 5: Session Logger (per project)
Sessions are entities with `type: 'session'` and `project_id`.

```typescript
body: {
  title:     string
  session_type: 'build' | 'research' | 'review' | 'meeting' | 'planning'
  log:       string    // raw, unfiltered
  worked:    string    // what worked and why structurally
  failed:    string    // what failed and why structurally
  decisions: string
  next:      string
  energy:    number    // 1-10
  hours:     number
}
```

### Module 6: Version System
Every entity that changes creates a `version_log` entity:

```typescript
// version_log body:
{
  entity_id:   string
  entity_type: EntityType
  version_from: number
  version_to:   number
  diff_summary: string    // what changed in plain text
  snapshot:     string    // JSON.stringify of entity at this version
}
```

When any entity is updated:
1. Create version_log with snapshot of previous state
2. Increment entity.version
3. Update entity.updated_at

### Module 7: Pattern Engine (cross-project)
Reads all entities across all projects. Calls Claude API.

Prompt structure:
```
Read all entities below across all project types.
Return JSON:
{
  "project_patterns":   string[],   // what's recurring across projects
  "missing_base":       string[],   // base projects that should exist but don't
  "skill_gaps":         string[],   // skills needed but not built
  "cross_connections":  string[],   // connections between projects not yet linked
  "loop_message":       string,     // one sentence — what the system is saying
  "v2_recommendations": string      // markdown — what to change in how the agency operates
}
```

API call:
```typescript
// Model: claude-sonnet-4-20250514
// Max tokens: 1000
// No API key in code — handled by proxy
```

---

## Layer 4 — Navigation Structure

### Sidebar sections
```
AGENCY
  ◈  Dashboard
  ⬡  Projects
  ◎  Pattern engine

BASE PROJECTS
  [dynamically listed — category: 'base']

ACTIVE PROJECTS
  [dynamically listed — category != 'base', status: 'active']

DRAFTS
  [status: 'draft']

OS
  ↓  Export
  ⚙  Settings
```

### Views per route
```
/                     Dashboard
/projects             All projects list
/projects/new         Create project (with entry criteria gate)
/projects/:id         Project home — tabs: Wiki | Files | Sessions | Skills
/projects/:id/wiki    Wiki view + editor
/projects/:id/files   File tree + editor panel
/projects/:id/session Log session
/patterns             Pattern engine
/settings             Settings + API config
```

---

## Layer 5 — Export System

### Single entity export
Any entity can be exported as .md. Format:
```markdown
# {entity name}
> type: {type} · project: {project} · version: {n} · {date}

{body fields as markdown sections}

---
_exported from Intelligence Agency OS_
```

### Project export
Full project export as .zip containing:
```
{project_name}/
  wiki/
    {section}/
      {page_title}.md
  files/
    {folder_structure}/
      {file_name}.md
  skills/
    {domain}_skill.md
  sessions/
    {date}_{title}.md
  project_manifest.json    ← all entity metadata
```

### Full OS export
JSON export of all entities + settings. Import-ready for V2 Supabase.

---

## Layer 6 — V2 Backend (Supabase)

### Tables — mirror IndexDB schema exactly
```sql
-- entities table
CREATE TABLE entities (
  id          TEXT PRIMARY KEY,
  type        TEXT NOT NULL,
  status      TEXT DEFAULT 'active',
  project_id  TEXT,
  parent_id   TEXT,
  version     INTEGER DEFAULT 1,
  tags        TEXT[],
  links       JSONB DEFAULT '[]',
  created_at  BIGINT NOT NULL,
  updated_at  BIGINT NOT NULL,
  created_by  TEXT DEFAULT 'user',
  body        JSONB NOT NULL
);

CREATE INDEX idx_entities_type        ON entities(type);
CREATE INDEX idx_entities_project_id  ON entities(project_id);
CREATE INDEX idx_entities_parent_id   ON entities(parent_id);
CREATE INDEX idx_entities_status      ON entities(status);
CREATE INDEX idx_entities_created_at  ON entities(created_at);
CREATE INDEX idx_entities_tags        ON entities USING gin(tags);

-- patterns table
CREATE TABLE patterns (
  id         TEXT PRIMARY KEY,
  count      INTEGER,
  data       JSONB,
  created_at BIGINT
);

-- settings table
CREATE TABLE settings (
  key   TEXT PRIMARY KEY,
  value JSONB
);
```

### API routes
```
GET    /entities              ?type= &project_id= &status= &tag=
GET    /entities/:id
POST   /entities
PUT    /entities/:id
DELETE /entities/:id

GET    /projects              shortcut — entities?type=project
GET    /projects/:id/tree     all file_nodes for project
GET    /projects/:id/export   full project zip

GET    /patterns/latest
POST   /patterns/run          triggers AI analysis

GET    /settings/:key
PUT    /settings/:key
```

### Storage mode switch
```typescript
// In settings: storageMode = 'local' | 'remote'
// Abstract all DB calls through:

interface StorageAdapter {
  get(id: string): Promise<Entity>
  getAll(filters: QueryFilters): Promise<Entity[]>
  put(entity: Entity): Promise<void>
  delete(id: string): Promise<void>
}

// LocalAdapter  — uses IndexDB
// RemoteAdapter — uses fetch to Supabase REST
// Switch in settings. Zero code change in features.
```

---

## Layer 7 — MCP Server

### Tools to expose
```
list_projects()
get_project(id)
get_wiki(project_id)
get_skills(project_id?)
get_sessions(project_id?, limit?)
get_file_tree(project_id)
get_file_content(file_node_id)
create_entity(type, project_id, body)
update_entity(id, body_patch)
log_session(project_id, session_body)
run_patterns()
export_project(id)
```

### Build with
- Python: FastMCP
- Node: @modelcontextprotocol/sdk

Point at same Supabase DB as REST API. Same entity schema.

---

## Layer 8 — Build Order for Agent

Follow this exactly. Do not skip layers.

```
Phase 1 — Foundation
  1. Vite + React + TypeScript + Tailwind setup
  2. Color tokens in tailwind.config.ts
  3. Font imports in index.html
  4. Component library (Button, Card, Field, Badge, Modal, Alert)
  5. IndexDB init with all stores and indexes
  6. Entity factory function (mkEntity)
  7. All query helper functions
  8. StorageAdapter interface + LocalAdapter

Phase 2 — Core views
  9.  Sidebar navigation
  10. Dashboard view (stats + feed)
  11. Projects list view
  12. Create project (with entry criteria gate)
  13. Project home (tabs scaffold)

Phase 3 — File system
  14. File tree component (recursive TreeNode)
  15. File CRUD (create, rename, move, delete)
  16. Markdown editor panel (textarea + preview toggle)
  17. Import .md file
  18. Export single file and folder as .zip (use JSZip from CDN)

Phase 4 — Content modules
  19. Wiki pages (list + editor + sections)
  20. Session logger form + history list
  21. Skill file creator (structured form → .md)
  22. Version log (auto-created on every entity update)

Phase 5 — Intelligence
  23. Pattern engine UI + Claude API call
  24. Cross-project entity feed
  25. Missing base project detector

Phase 6 — Export
  26. Single entity .md export
  27. Full project .zip export
  28. Full OS JSON export

Phase 7 — V2 backend
  29. Supabase tables + indexes
  30. REST API routes
  31. RemoteAdapter (mirrors LocalAdapter interface)
  32. Settings toggle (local ↔ remote)
  33. MCP server

Phase 8 — Polish
  34. Search across all entities
  35. Keyboard shortcuts (N = new, E = export, / = search)
  36. Empty states for every view
  37. Loading states for async ops
  38. Error boundaries
```

---

## Trap warnings for agent

**Trap 1** — Do not build the file tree with HTML `<details>` or CSS-only expand/collapse. Use React state per node with a `Set<string>` of open node IDs.

**Trap 2** — Do not store markdown content directly in textarea value and forget to persist. Every keystroke does NOT save. Save on blur + explicit save button. Show unsaved indicator.

**Trap 3** — JSZip for folder export. Import from CDN: `https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js`. Generate blob, trigger download.

**Trap 4** — The version log must be created BEFORE the entity is updated. Snapshot = previous state. If you create it after, you log the new state as "previous."

**Trap 5** — IndexDB transactions are short-lived. Do not await multiple operations inside one transaction. Use separate transactions per operation.

**Trap 6** — MCP server runs on a separate port from the API. Do not mix them.

**Trap 7** — The StorageAdapter switch must be complete. Every feature must use the adapter, not call IndexDB or fetch directly. This is what enables clean V2 migration.

---

## First project to test in the app

**The Researcher** — a base project that:
- Uses itself to document its own research process
- Wiki: how to research (first principles)
- Skill files: research domain knowledge
- Sessions: research sessions logged
- Process: the research SOP built from sessions
- Serves: any other project that needs R&D

This is the first base project. Build the app. Create this project. Run it. The app will immediately have real data and validate every module.
