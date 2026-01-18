# The Context Layer: Universal AI Context Pattern 🧠

[![YouTube](https://img.shields.io/badge/Watch_Tutorial-YouTube-red?style=flat&logo=youtube)]([https://www.youtube.com/watch?v=oRclzIO5j_w&list=PLQog6EfhK_pLacZtSXqNp2vuPKMjZoHaF])
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

> **Stop repeating yourself to AI.**
> A standardized file structure to keep LLMs (Cursor, Claude, GPT-4) perfectly synced with your architecture decisions, coding standards, and active tasks.

## ⚡ The Problem
AI coding assistants are powerful, but they are **amnesiacs**.
- They forget your tech stack choices.
- They hallucinate libraries you aren't using.
- They ignore your folder structure conventions.
- You waste tokens and time re-explaining "how we do things here."

## 🛠 The Solution: `.context/`
Instead of relying on a tool's proprietary memory (like `.cursorrules` or Claude Projects), we externalize the context into the repository itself. This makes your context **portable** and **universal**.

### The Structure
Create a `.context/` folder in the root of your project:

```text
📂 .context/
├── 📄 architecture.md    # The "North Star" (Patterns, Stack, Boundaries)
├── 📄 conventions.md     # The "Law" (Naming, Testing, Folder Structure)
├── 📄 current.md         # The "RAM" (Active Sprint, Current Session Goals)
└── 📄 tech-stack.md      # The "Inventory" (Exact Versions, Dependencies)
📂 File Templates
1. architecture.md
Define the high-level decisions that shouldn't change often.

Markdown
# System Architecture

## Core Patterns
- **Frontend:** Next.js 14 (App Router) using Server Components by default.
- **State Management:** URL-based state first, then React Context. No Redux.
- **Database:** Supabase (PostgreSQL) with Row Level Security (RLS).

## Key Boundaries
- API routes must validate all inputs using Zod.
- UI components must be separated from Data Fetching logic.
2. conventions.md
Define the syntax and style rules.

Markdown
# Coding Conventions

## Naming
- Components: PascalCase (e.g., `UserProfile.tsx`)
- Functions: camelCase (e.g., `fetchUserData`)
- Constants: UPPER_SNAKE_CASE

## Testing
- All critical user flows must have an E2E test in Playwright.
- Unit tests co-located with components in `__tests__` folder.

## Rules
- Prefer const over let.
- No `any` types in TypeScript.
3. current.md (The Game Changer)
Update this file at the start of every session. It acts as the "Short Term Memory" for the AI.

Markdown
# Current Session Context
**Date:** 2026-01-18
**Goal:** Refactor the User Dashboard to improve loading performance.

## Active Tasks
- [ ] Move large data fetching to Server Actions.
- [ ] Implement Skeleton loaders for the chart widgets.
- [x] Fix the layout shift on mobile.

## Known Issues
- The `UserMetric` component is re-rendering too often. Focus investigation there.
🚀 Workflow
With Cursor / VS Code
Open your Chat.

Type: "@.context/ Read the context folder and help me implement..."

The AI now knows your architecture, conventions, and exactly what you are working on today.

With Claude (Projects)
Create a Project in Claude.ai.

Upload the .context folder as "Project Knowledge".

Claude will now check these files before every response, preventing hallucinations.

📚 As Seen In "The Architect's Playbook"
This pattern is part of the Context Engineering series on YouTube.

Part 1: The Universal Pattern (This Repo)

Part 2: Automating Skills (Coming Soon)

Part 3: Enterprise Governance (Coming Soon)

🤝 Contributing
Feel free to submit PRs with your own specialized .context templates (e.g., for Python/Django, Go, or Rust).

📄 License
MIT License. Build cool things.
