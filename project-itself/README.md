# 🏗️ Project Codebase

This is where your actual project codebase lives.

## Options
You have two ways to organize your code:

### Option A: Code Inside This Folder
Place your entire codebase here. This keeps a clean separation between your project code and the brain/ operating system.

```
project-itself/
├── src/
├── package.json
├── ...
```

### Option B: Root as Parent
Use the repository root as your project root. In this case, `brain/` and `.agents/` sit alongside your `src/`, `package.json`, etc.

Your AI agent will ask you which option you prefer during the `setup.md` configuration.
