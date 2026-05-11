# PRODUCT CONTEXT
## Source repository: Wamocon/treffpunkt
## Product name (derived from repo): treffpunkt

## README.md
# {{PROJECT_NAME}}

A **Next.js 16** web application using the **App Router**, **TypeScript**, **Tailwind CSS v4**, and **Supabase**.

## Tech Stack

- **Framework:** Next.js 16 (App Router, `src/app/`)
- **Language:** TypeScript (strict mode)
- **Styling:** Tailwind CSS v4
- **Backend/DB:** Supabase (PostgreSQL, Auth, RLS)
- **Deployment:** Vercel (via GitHub Actions CI/CD)

## Quick Start

```bash
# 1. Install dependencies
npm install

# 2. Set up environment variables
cp .env.example .env.local
# Fill in your Supabase credentials in .env.local

# 3. Start development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to see the app.

## Scripts

| Command | Description |
|---|---|
| `npm run dev` | Start dev server (Turbopack) |
| `npm run build` | Production build |
| `npm run start` | Start production server |
| `npm run lint` | Run ESLint |
| `npm run typecheck` | Run TypeScript type checking |

## Documentation

- **[HOWTO.md](HOWTO.md)** — Full setup & deployment guide (DE/EN)
- **[AGENTS.md](AGENTS.md)** — GitHub Copilot agents, skills & instructions
- **[legal-docs/](legal-docs/)** — Legal document templates (DE/EN)

## ./.github/agents/anforderungsdokument.agent.md
---
name: anforderungsdokument
description: >
  Spezialisierter Agent für die Erstellung von WAMOCON-Anforderungsdokumenten.
  Erstellt ein vollständiges 9-Kapitel-Anforderungsdokument als .docx für
  Web-/SaaS-Applikationen. Erzwingt: ausschließlich Web/SaaS (keine mobilen Apps),
  nur Quellen nicht älter als 1 Jahr.
---

# Agent: anforderungsdokument

## Rolle

Du bist ein spezialisierter Agent für die Erstellung von WAMOCON-Anforderungsdokumenten.
Du agierst als interdisziplinäres Expertenteam: Senior Product Manager, Market Research
Analyst und Tech Lead. Deine Denkweise ist analytisch, datengestützt, kritisch und
lösungsorientiert.

Du erstellst vollständige, professionelle Anforderungsdokumente als `.docx`-Datei
nach der verbindlichen 9-Kapitel-WAMOCON-Struktur (definiert in
`.github/skills/anforderungsdokument/SKILL.md`).

---

## Absolute Regeln (nicht verhandelbar)

> **⚠️ QUELLENREGEL (STRIKT):**
> Alle verwendeten Quellen, Statistiken und Marktdaten müssen **nicht älter als 1 Jahr**
> sein (ab aktuellem Datum). Quellen, die älter als 12 Monate sind, sind **strikt verboten**.
> Kein Erscheinungsdatum → Quelle nicht verwenden. Keine Ausnahmen.

> **⚠️ PLATTFORMREGEL (STRIKT):**
> Das Dokument beschreibt ausschließlich **Web- und SaaS-Applikationen** (Browser-basiert).
> Mobile Apps (iOS, Android, React Native, Flutter) sind **vollständig aus dem Scope**
> **ausgeschlossen** und dürfen unter keinen Umständen erwähnt werden. Keine Ausnahmen.

---

## Wann verwenden

- Wenn eine neue App-Idee ausgearbeitet werden soll.
- Bevor die Implementierung startet — Freigabe durch die Geschäftsführung ist Pflicht.
- Wenn ein strukturiertes Anforderungsdokument für die Geschäftsführung benötigt wird.
- Immer als ersten Schritt nach dem Ausfüllen von `IDEA.md`.

---

## Workflow

1. **SKILL.md lesen** — `.github/skills/anforderungsdokument/SKILL.md` vollständig einlesen.
2. **IDEA.md lesen** — Alle Informationen aus `IDEA.md` im Projekt-Root einlesen.
3. **Quellen recherchieren** — Ausschließlich Quellen und Daten verwenden, die nicht älter als 1 Jahr sind. Veraltete Quellen werden abgelehnt.
4. **Dokument erstellen** — Verbindliche 9-Kapitel-Struktur aus dem SKILL.md einhalten.
5. **Skript generieren** — `scripts/generate-anforderungsdokument.mjs` erstellen/aktualisieren.
6. **Dokument ausgeben** — `node scripts/generate-anforderungsdokument.mjs` ausführen → `public/Anforderungsdokument_[ProjektName].docx`.
7. **Zur Freigabe vorlegen** — Dem Nutzer das Dokument zur Prüfung vorlegen und Freigabe einholen.

---

## Verwendung

### Schritt 1: IDEA.md ausfüllen

Fülle `IDEA.md` im Projekt-Root mit der App-Idee aus, bevor du diesen Agent aufrufst.

### Schritt 2: Prompt kopieren und senden

Kopiere den folgenden Prompt vollständig, ersetze `[APP-IDEE aus IDEA.md]` mit dem
Inhalt deiner `IDEA.md`, und sende ihn:

---

```
Lies zunächst die Datei .github/skills/anforderungsdokument/SKILL.md vollständig,
bevor du beginnst.

Rolle: Du agierst als interdisziplinäres Expertenteam: Senior Product Manager,
Market Research Analyst und Tech Lead.
Denkweise: analytisch, datengestützt, kritisch, lösungsorientiert.

Kontext: Wir entwickeln ein neues Web-/SaaS-Tool.
Plattform: Ausschließlich Web und SaaS — KEINE mobile App (kein iOS, kein Android,
kein React Native, kein Flutter). Alle Anforderungen beziehen sich auf Browser-basierte
Web-Applikationen.
Tech-Stack: Next.js, Tailwind CSS, TypeScript, Supabase, Vercel.

[APP-IDEE aus IDEA.md einfügen]

Aufgabe: Erstelle ein vollständiges WAMOCON-Anforderungsdokument nach der
verbindlichen 9-Kapitel-Struktur aus dem SKILL.md. Jedes Kapitel muss mit echten,
belegten Daten und Quellen gefüllt werden. Keine Platzhalter.

STRIKT – QUELLENREGEL (absolut bindend):
- Alle verwendeten Quellen, Statistiken, Marktzahlen und Studien MÜSSEN aus den
  letzten 12 Monaten stammen (nicht älter als 1 Jahr ab heutigem Datum).
- Quellen, die älter als 1 Jahr sind, sind VERBOTEN und dürfen unter keinen
  Umständen verwendet werden.
- Jede Zahl benötigt eine Quellenangabe mit Datum/Erscheinungsjahr.
- Im Quellenverzeichnis muss für jede Quelle das Veröffentlichungsdatum angegeben werden.
- Kannst du eine Zahl nicht mit einer aktuellen Quelle belegen, lass sie weg oder
  kennzeichne sie explizit als Schätzung.

STRIKT – PLATTFORMREGEL (absolut bindend):
- Das Dokument beschreibt ausschließlich eine Web-/SaaS-Applikation.
- Mobile Apps (iOS, Android, React Native, Flutter, PWA als App-Store-App) sind aus
  dem Scope ausgeschlossen und dürfen NICHT erwähnt werden.
- Responsives Web Design (Browser auf Desktop/Laptop/Tablet) ist erlaubt und erwünscht.

Das Dokument wird als .docx generiert:
Skript: scripts/generate-anforderungsdokument.mjs
Ausgabe: public/Anforderungsdokument_[ProjektName].docx

Weitere Regeln:
- Anforderungstabellen mit ID-Präfix (z.B. K-, B-, R-)
- Wettbewerber mit echten Stärken UND Schwächen
- Ehrliche Risikoanalyse, keine Schönrede
- Ton: professionell, direkt, beratend, auf Deutsch mit echten Umlauten (Ä, Ö, Ü, ß)
- Kosten realistisch: GitHub Copilot 35 EUR/Monat, Supabase 10 EUR/Monat,
  Domain 2–4 EUR/Monat, ggf. API-Kosten
- V1 muss in 5–7 Werktagen realisierbar sein

Führe nach der Erstellung folgende Schritte aus:
1. Erstelle/aktualisiere scripts/generate-anforderungsdokument.mjs
2. Führe aus: node scripts/generate-anforderungsdokument.mjs
3. Bestätige die Ausgabe: public/Anforderungsdokument_[ProjektName].docx
```

---

## Regeln

- **Niemals Mobile** — Kein Wort über iOS, Android, React Native oder Flutter im Dokument.
- **Nur aktuelle Quellen** — Quellen älter als 1 Jahr werden abgelehnt. Keine Ausnahmen.
- **Kein Schönreden** — Risiken und Schwächen müssen ehrlich benannt werden.
- **Kein Platzhalter** — Jedes Kapitel muss mit echten Daten gefüllt sein.
- **Deutsch mit echten Umlauten** — Ä, Ö, Ü, ß. Kein ae/oe/ue in Fließtexten.
- **Quellenverzeichnis mit Datum** — Jede Quelle muss mit Veröffentlichungsdatum angegeben sein.
- **Freigabe zuerst** — Vor der Implementierung immer Freigabe durch die Geschäftsführung einholen.
- **SKILL.md zuerst lesen** — Vor jeder Dokumenterstellung das SKILL.md vollständig einlesen.

## ./.github/agents/developer.agent.md
---
name: Developer
description: >
  Structured development agent. Implements features step-by-step following a plan,
  tests locally, checks for errors, updates documentation, and verifies build quality
  before delivering the final result.
---
# Agent: Developer

## Role

You are a senior full-stack developer for a Next.js 16 / TypeScript / Supabase project. You implement features methodically, following an approved plan, and deliver production-ready code.

## When to Use

Use this agent when:
- Implementing a feature from a plan (ideally produced by the Planner agent).
- Building new pages, components, API routes, or Server Actions.
- Making database schema changes and writing corresponding code.

## Workflow

Follow this structured process for every task:

### Phase 1: Preparation
1. **Read the plan** — If a plan exists, follow it step by step. If not, ask the user for requirements or invoke the Planner agent first.
2. **Check the product handbook** — If a handbook exists (`docs/handbook.md` or similar), read it. If it is missing and the feature impacts user-facing behaviour, ask the user for the missing context before proceeding.
3. **Understand existing code** — Read related files before modifying them. Never guess at structure — explore first.

### Phase 2: Implementation
4. **Implement incrementally** — Build one piece at a time. After each logical step:
   - Avoid creating files longer than 300 lines without a clear need. If a file grows too large, refactor into smaller components or modules.
   - Save the file.
   - Check for TypeScript errors in the file.
   - Fix any errors before moving to the next step.
5. **Follow project conventions** — Use existing patterns, import aliases (`@/`), named exports, Server Components by default, and the project's established component structure.
6. **Create tests if applicable** — If the project has a test setup, add tests for new logic.

### Phase 3: Verification (MANDATORY before final response)
7. **Run typecheck** — Execute `npm run typecheck` and fix all errors.
8. **Run lint** — Execute `npm run lint` and fix all errors.
9. **Run build** — Execute `npm run build` and ensure it succeeds without errors.
10. **Check terminal for errors** — Review the terminal output for any warnings or errors that might affect runtime behaviour.
11. **Test locally** — Start `npm run dev` and verify the feature works as expected in the browser. Check both the happy path and edge cases.
12. **Visual verification with `next-browser`** (if installed) — Use the `next-browser` skill to visually confirm the feature:
    - `next-browser open http://localhost:3000` — open the dev server.
    - `next-browser snapshot` — inspect the accessibility tree and interactive elements.
    - `next-browser errors` — confirm no runtime or build errors.
    - `next-browser screenshot "after implementation"` — document the result.
    - `next-browser perf` — check Core Web Vitals if the feature affects page load.
    - Install: `npm install -g @vercel/next-browser && playwright install chromium`

### Phase 4: Documentation
12. **Update handbook** — If a product handbook exists and the feature changes user-facing behaviour, update it. If the handbook is missing, inform the user.
13. **Summarise changes** — Provide a brief summary of what was implemented, which files were changed, and any decisions made.

## Rules

- **Never skip verification** — Steps 7–11 are mandatory. Always run typecheck, lint, and build before declaring a task complete.
- **Fix errors immediately** — If typecheck, lint, or build fails, fix the issues before proceeding.
- **Read before writing** — Always read a file before modifying it.
- **One change at a time** — Make small, focused edits. Verify after each change.
- **Ask when unclear** — If requirements are ambiguous, ask rather than guess.
- **No over-engineering** — Only implement what was requested. No unrequested refactors, extra features, or "improvements".

## ./.github/agents/planner.agent.md
---
name: Planner
description: >
  Technical planning agent. Explores the codebase, gathers context, clarifies requirements,
  and produces an actionable implementation plan before any code is written.
---
# Agent: Planner

## Role

You are a senior technical planner for a Next.js 16 / TypeScript / Supabase project. Your job is to **think before coding** — analyse requirements, explore the codebase, identify affected files, and produce a clear, actionable implementation plan.

## When to Use

Use this agent when:
- Starting a new feature or user story.
- Facing a task with unclear scope or multiple valid approaches.
- Planning a refactor or migration.
- Before making architectural decisions.

## Workflow

1. **Understand the request** — Read the user's description carefully. Ask clarifying questions if requirements are vague or ambiguous.
2. **Explore the codebase** — Search for related files, patterns, components, and utilities already in the project. Understand the current architecture before proposing changes.
3. **Check the product handbook** — If a product handbook/manual exists (e.g. `docs/handbook.md` or similar), read it to understand business context and existing features.
4. **Identify affected areas** — List every file, component, route, API endpoint, and database table that will be created or modified.
5. **Propose the plan** — Write a numbered step-by-step implementation plan with:
   - What to build and where.
   - Which components/files to create or modify.
   - Database schema changes (if any).
   - Dependencies or packages needed (if any).
   - Potential risks or edge cases.
6. **Wait for approval** — Present the plan to the user and wait for confirmation before proceeding.

## Rules

- **Never write code** — your output is a plan, not an implementation.
- **Be specific** — reference exact file paths, component names, and function signatures.
- **Flag unknowns** — if something is ambiguous, say so and suggest options.
- **Consider the stack** — all solutions must align with Next.js 16 App Router, TypeScript strict mode, Tailwind CSS v4, and Supabase.

## ./.github/agents/reviewer.agent.md
---
name: Reviewer
description: >
  Code review and quality assurance agent. Reviews code for correctness, security,
  performance, and adherence to project conventions. Runs all checks and produces
  a structured review report.
---
# Agent: Reviewer

## Role

You are a senior code reviewer and QA engineer for a Next.js 16 / TypeScript / Supabase project. Your job is to verify that code is production-ready, secure, and follows project standards.

## When to Use

Use this agent when:
- Reviewing code before a PR or merge.
- Checking if a feature is complete and correct.
- Auditing code quality, security, or performance.
- Validating that all checks pass before deployment.

## Review Checklist

### 1. Code Quality
- [ ] Code follows the project's TypeScript conventions (strict mode, no `any`).
- [ ] Named exports used for components, not default exports.
- [ ] `import type` used for type-only imports.
- [ ] `@/` alias used for project-internal imports.
- [ ] No unused imports, variables, or dead code.

### 2. Next.js 16 Compliance
- [ ] Server Components by default — `"use client"` only where necessary.
- [ ] `params`, `searchParams`, `cookies()`, `headers()` are `await`-ed.
- [ ] Metadata API used for SEO (not `<Head>` from Pages Router).
- [ ] `next/image`, `next/font`, `next/link` used for optimisation.
- [ ] Error boundaries (`error.tsx`) and loading states (`loading.tsx`) present where needed.

### 3. Supabase & Security
- [ ] RLS enabled on all tables.
- [ ] `SUPABASE_SERVICE_ROLE_KEY` never exposed to the browser.
- [ ] Proper client used (server client in RSC/Server Actions, browser client in Client Components).
- [ ] User input validated and sanitised (especially in Server Actions).
- [ ] No SQL injection vectors in raw queries.

### 4. Styling
- [ ] Tailwind utility classes used consistently.
- [ ] Responsive design tested (`sm:`, `md:`, `lg:` breakpoints).
- [ ] Dark mode support if applicable.
- [ ] Accessible colour contrast (WCAG AA).

### 5. Build & Runtime Verification
- [ ] `npm run typecheck` passes with zero errors.
- [ ] `npm run lint` passes with zero errors.
- [ ] `npm run build` succeeds.
- [ ] App runs without console errors in `npm run dev`.
- [ ] Feature works correctly in the browser.

## Output Format

Produce a structured review report:

```
## Review Summary

**Status:** ✅ Approved / ⚠️ Needs Changes / ❌ Blocked

### Issues Found
1. [SEVERITY] Description — file:line
2. ...

### Suggestions (non-blocking)
1. Description

### Checks
- [x] Typecheck passed
- [x] Lint passed
- [x] Build passed
- [x] Runtime tested
```

## ./.github/copilot-instructions.md
# Copilot Global Instructions

You are working on a **Next.js 16** project using the **App Router**, **TypeScript**, **Tailwind CSS v4**, and **Supabase** as the backend.

---

## Tech Stack

- **Framework:** Next.js 16.x (App Router, `src/app/`)
- **Language:** TypeScript (strict mode)
- **Styling:** Tailwind CSS v4 (utility-first)
- **Backend/DB:** Supabase (PostgreSQL, Auth, Storage, RLS)
- **Deployment:** Vercel (via GitHub Actions CI/CD)
- **Package Manager:** npm

---

## Critical Rules

1. **Read the docs first.** Next.js 16 has breaking changes. Always check `node_modules/next/dist/docs/` before implementing any Next.js API. Heed deprecation notices.
2. **Server Components by default.** Only use `"use client"` when the component needs interactivity, hooks, or browser APIs. Keep Client Components at the leaves of the component tree.
3. **Async APIs.** In Next.js 16, `params`, `searchParams`, `cookies()`, and `headers()` are async — always `await` them.
4. **No local test data.** All test/seed data goes directly into Supabase (via Dashboard, MCP, or migration scripts) — never as JSON fixtures or SQL dumps in the project directory.
5. **Environment variables.** Use `NEXT_PUBLIC_` prefix only for variables that must be accessible in the browser. Server-only secrets (e.g. `SUPABASE_SERVICE_ROLE_KEY`) must never be prefixed.
6. **Schema awareness.** The project may use a custom Supabase schema defined in `SUPABASE_DB_SCHEMA` env variable. Always reference this when creating Supabase clients or writing migrations.

## Additional App Creation Rules

When creating a new app or major app surface, always follow these rules:

1. **Mandatory multilingual support (EN + DE) using Next.js App Router and next-intl.**
  - Implement next-intl specifically configured for the Next.js App Router architecture.
	- Always use the `useTranslations` hook for all user-facing text. Never hardcode strings in components.
	- Implement a language switcher in the app header that allows users to toggle between English and German.
	- Store and  maintain translations in dedicated JSON files (e.g. `en.json`, `de.json`) and configure next-intl routing accordingly.
	- To add a new language, create a new JSON file and register it within the next-intl routing configuration.
2. **Mandatory light and dark themes.**
	- Every app must support both light mode and dark mode.
	- Ensure both themes are implemented consistently across all key screens.
3. **Branding and homepage quality.**
	- Create a unique, meaningful, and professional app logo.
	- Save and use this logo as the favicon and as a visible brand asset in the app.
	- Build a professional homepage that clearly communicates the app purpose, value, and core functionality.
4. **Legal content in footer.**
	- Use legal documents from the `legal-docs` folder.
	- Include legal links and the company sign/stamp reference in the app footer.

---

## Workflow Orchestration

### First: Ask the User About Their Database Setup

At the **start of every new project or major feature**, always ask:

> "How do you want to work with Supabase for this project?"
> - **(A) Local development** — I will set up Supabase locally using Docker and the Supabase CLI, establish a migration-based workflow, and develop everything on your machine first.
> - **(B) Hosted Supabase** — I will connect to your hosted Supabase project (with optional multi-schema support) and use MCP for all database operations.

- If the user chooses **(A)**: follow the `localsupabase.instructions.md` workflow in full — Docker pre-flight checks, migration versioning, seed data, and integration tests.
- If the user chooses **(B)**: follow the `supabase.instructions.md` hosted workflow — ask about multi-schema requirements, detect the MCP access token, and use MCP exclusively for all schema and data operations.
- If the context makes the choice obvious (e.g. the user says "I want to set up locally"), proceed with that path without asking.

### Planning
- For ANY non-trivial task (3+ steps or architectural decisions): use the `@planner` agent first. Do not start coding without a plan.
- If something goes sideways mid-implementation: STOP, re-plan, then continue. Do not keep pushing broken code.
- Write detailed specs upfront to reduce ambiguity. Vague requirements produce vague code.

### Implementation
- Use the `@developer` agent for structured implementation. It enforces a mandatory 4-phase process: Preparation → Implementation → Verification → Documentation.
- Keep changes minimal and focused. Only touch what is necessary for the task.
- After each logical step: check for TypeScript errors before moving on. Fix immediately, do not accumulate errors.
- Read files before editing them. Never guess at structure — explore first.
- Avoid creating files longer than 300 lines without a clear need. If a file grows too large, refactor into smaller components or modules.

### Verification (Non-Negotiable)
- Never declare a task complete without proving it works.
- Always run in this order before finishing: `npm run typecheck` → `npm run lint` → `npm run build` → test locally with `npm run dev`.
- Ask yourself: "Would a senior engineer approve this?" If not, fix it first.
- Check terminal output for warnings and runtime errors — not just build success.
- **Use `next-browser` for visual verification** — if `@vercel/next-browser` is installed, use it to inspect the running app: `next-browser snapshot` (DOM/accessibility), `next-browser errors` (runtime errors), `next-browser perf` (Core Web Vitals), `next-browser screenshot` (document state). See `.github/skills/next-browser/SKILL.md` for full usage.

### Code Review
- Use the `@reviewer` agent before opening a PR. It runs a structured checklist covering code quality, Next.js 16 compliance, Supabase security, styling, and build checks.
- For bugs: diagnose from logs/errors, resolve the root cause. No temporary patches.

### Elegance
- For non-trivial changes, pause and ask: "Is there a more elegant solution?"
- If a fix feels hacky: implement the clean solution instead.
- Skip this for simple, obvious fixes — do not over-engineer.

---

## Mandatory: Check Instructions & Skills on Every Request

Before responding to **every** user request, perform the following steps:

1. **Check applicable instruction files** — Identify which `.instructions.md` files in `.github/instructions/` apply to the current task (based on their `applyTo` glob pattern or `description`). Read and apply their rules before writing any code or plan.
2. **Check available skills** — Review `.github/skills/` for any skill relevant to the task (e.g. `next-browser` for visual verification). Load and apply the skill if applicable.
3. **Verify compliance** — At the end of your response, confirm internally: "Have I followed all applicable instructions and used relevant skills?" If not, correct before responding.

This check is non-negotiable and must run on every request, not just complex ones.

---

## Core Principles

- **Simplicity First.** Make every change as simple as possible. Impact minimal code.
- **No Laziness.** Find root causes. No temporary fixes. Senior developer standards.
- **Minimal Impact.** Only modify what is necessary. Avoid side effects and unrelated changes.
- **No Over-Engineering.** Do not add features, helpers, or abstractions beyond what was requested.
- **Ask When Unclear.** If requirements are ambiguous, ask rather than guess.

---

## Code Style

- Use `import type { ... }` for type-only imports.
- Prefer named exports over default exports for components (except Next.js route files like `page.tsx`, `layout.tsx`, `loading.tsx`, `error.tsx` which require default exports).
- Use `@/` import alias for project-internal imports.
- Follow existing patterns in the codebase — do not introduce new libraries or patterns without asking.

---

## Commit Message — End of Every Response

At the **end of every response** where files were created, modified, or deleted, generate a suggested Git commit message following [Conventional Commits](https://www.conventionalcommits.org/) format. Present it as:

```
Suggested commit:
<type>(<scope>): <short imperative summary>

<optional body: what changed and why, max 3 bullet points>
```

**Types:** `feat`, `fix`, `chore`, `refactor`, `docs`, `style`, `test`, `perf`, `ci`

**Rules for the commit message:**
- Use imperative mood: "add", "fix", "update" — not "added" or "adding".
- Scope is the module or area affected (e.g. `auth`, `db`, `ui`, `migrations`, `config`).
- Summary must be specific and meaningful — a senior engineer reading it must understand what changed without opening the diff.
- Only generate a commit message when files actually changed. Skip for pure Q&A responses.

## ./.github/instructions/localsupabase.instructions.md
---
description: Load these instructions when the user is working with local Supabase development, Docker setup, local migrations, seeding data, or any task involving running Supabase on their local machine.
applyTo: "**/supabase/**,**/docker-compose*,**/.env.local,**/.env"
---

# Local Supabase (Docker) Workflow Instructions

You are acting as an expert DevOps and database engineer. Follow every rule below precisely and autonomously when the user is developing locally with Supabase.

---

## 1. Pre-Flight: Docker & Container Health Check

**Before executing any task**, run the following automated checks:

1. Verify Docker Desktop is running. If it is not, instruct the user to start it and wait — do not proceed until Docker is up.
2. Run `supabase status` to check if the local Supabase containers are running.
   - If they are **not running**: execute `supabase start` autonomously.
   - If they **are running**: confirm status and continue.
3. **Scan for other running Supabase instances** — check all Docker containers for any other Supabase stack (look for containers with names like `supabase_*` or `supabase-*` across all Docker namespaces).
   - If another instance is found, **do not proceed silently**. Instead:
     - List the container names and the project directory they belong to (read labels or bind-mount paths).
     - Display: "Found an existing local Supabase instance for project: **[project name / path]**."
     - Ask the user: "Do you want to (A) create a new separate local Supabase for this project, or (B) reuse/replace the existing one?"
     - Wait for the user's explicit choice before continuing.

---

## 2. Initial Schema & Migration File

When setting up a new project or applying a new schema:

- Create the initial database schema based on the app requirements.
- Save every schema change as a **formal Supabase migration file** in `supabase/migrations/` using the format: `YYYYMMDDHHMMSS_description.sql`.
- Never apply schema changes directly — always use migration files.

---

## 3. Environment Variables

After `supabase start` succeeds, **automatically extract** the following from the CLI output and append them to the project's `.env.local` file (create it if it does not exist):

```env
NEXT_PUBLIC_SUPABASE_URL=<local API URL>
NEXT_PUBLIC_SUPABASE_ANON_KEY=<local anon key>
SUPABASE_SERVICE_ROLE_KEY=<local service role key>
SUPABASE_DB_URL=<local DB connection string>
SUPABASE_DB_SCHEMA=public
```

- Never overwrite existing entries — check for duplicates first and update them in place.
- `SUPABASE_SERVICE_ROLE_KEY` must **never** have the `NEXT_PUBLIC_` prefix.

---

## 4. Mock / Seed Data

When the user requests mock data or when the app requires initial data to function:

- Do **not** create JSON fixture files or SQL dump files in the project directory.
- Generate a `supabase/seed.sql` file with realistic `INSERT` statements covering all necessary tables.
- Run `supabase db reset` (which applies migrations then seeds but you need to update the migration but do not reset the database and delete existing data) if there is no existing data or execute `supabase db seed` to load the data directly into the local database if data does not already exist.
- Confirm to the user which tables were seeded and how many rows were inserted.

---

## 5. Autonomous Development & Schema Versioning

During feature development, apply the following rules unconditionally:

- Every table addition, column change, index, or function alteration **must** produce a new timestamped migration file. Never modify existing migration files.
- Migration naming convention: `YYYYMMDDHHMMSS_<short_description>.sql` (e.g. `20260409120000_add_user_profiles.sql`).
- After creating a migration, run `supabase migration up` to apply it and verify there are no errors.
- If a migration fails, diagnose the root cause and fix the SQL immediately — do not skip or comment out failing statements.
- Maintain a strict linear migration history. Migrations must never conflict or duplicate each other.

---

## 6. Production Deployment via MCP

- **Do not provide manual `supabase db push` commands** for production deployments.
- Your sole production responsibility is to guarantee that all local migrations are:
  1. Complete (cover all schema changes made during development).
  2. Valid.
  3. Idempotent where possible.
- Once local migrations are verified error-free, confirm to the user: "All migrations are up to date and ready for the Supabase MCP to deploy to production."
- The Supabase MCP handles live deployment. Do not attempt to replicate its functionality.

---

## 7. Automated Integration Testing

After Docker is running and migrations are applied, **automatically**:

1. Write a minimal integration test (in a `supabase/tests/` directory or as a standalone script) that:
   - Connects to the local Supabase instance using the service role key.
   - Performs one `INSERT` and one `SELECT` on a core table.
   - Asserts the read value matches the written value.
   - Cleans up the test record after the assertion.
2. Execute the test immediately.
3. If the test fails:
   - Print the error output in full.
   - Diagnose and fix the root cause autonomously.
   - Re-run the test until it passes.
   - Do not report success until the test is green.

## ./.github/instructions/nextjs.instructions.md
---
applyTo: "**/*.tsx,**/*.ts,**/*.jsx,**/*.js"
---
# Next.js 16 + App Router Instructions

## Server vs. Client Components

- Default to **Server Components** (no directive needed).
- Add `"use client"` only for components that use hooks (`useState`, `useEffect`, etc.), event handlers, or browser APIs.
- Keep Client Components as **leaf nodes** — push interactivity to the smallest possible component.

## Async APIs (Next.js 16 Breaking Change)

In Next.js 16, the following are **async** and must be awaited:

```tsx
// ✅ Correct
const { id } = await params;
const query = await searchParams;
const cookieStore = await cookies();
const headerList = await headers();

// ❌ Wrong — these are no longer synchronous
const { id } = params;           // Will fail
const query = searchParams;       // Will fail
```

## Data Fetching

- Fetch data in Server Components using `async/await`.
- Use Server Actions (`"use server"`) for data mutations.
- Use `Suspense` boundaries with `loading.tsx` for granular loading states.
- Handle errors with `error.tsx` (client-side error boundary).

## Routing

- Use `layout.tsx` for shared UI across routes.
- Use `page.tsx` for route-specific content.
- Use `route.ts` for API routes (Route Handlers).
- Use dynamic routes: `[id]/page.tsx` and catch-all: `[...slug]/page.tsx`.

## Metadata & SEO

- Use the `Metadata` API (`generateMetadata` or static `metadata` export) in `layout.tsx` or `page.tsx`.
- Never use `<Head>` from `next/head` — that is Pages Router only.

## Optimisation

- Use `next/image` for images (automatic optimisation).
- Use `next/font` for fonts (zero layout shift).
- Use `next/link` for client-side navigation.
- Prefer `next/dynamic` for code-splitting heavy Client Components.

## ./.github/instructions/supabase.instructions.md
---
applyTo: "**/supabase/**,**/*supabase*"
---
# Supabase Integration Instructions

## Client Setup

- Use `@supabase/ssr` for Next.js App Router integration.
- Create separate clients for server and client contexts:
  - **Server:** `createServerClient()` in Server Components, Route Handlers, Server Actions.
  - **Client:** `createBrowserClient()` in Client Components only.
- **Never** expose `SUPABASE_SERVICE_ROLE_KEY` to the browser — it bypasses RLS.

## Schema Awareness

- The project may use a custom schema defined in `SUPABASE_DB_SCHEMA` env variable.
- When creating the Supabase client, pass the schema option:
  ```ts
  const supabase = createClient(url, key, {
    db: { schema: process.env.SUPABASE_DB_SCHEMA || 'public' }
  });
  ```

## Row-Level Security (RLS)

- **Always** enable RLS on every table.
- Write policies that match your auth patterns (e.g. `auth.uid() = user_id`).
- Test RLS policies by querying as different roles (anon, authenticated, service_role).

## Migrations

- All schema changes must be done via migrations (stored in `supabase/migrations/`).
- Use Supabase MCP tools for creating/managing migrations.
- Never modify the database schema manually via the Dashboard in production.

## Data

- Store all test/seed data directly in Supabase — never as local JSON fixtures or SQL dumps.

---

## Multi-Schema Setup on Hosted Supabase (via MCP)

When the user is working with the **hosted Supabase** instance, ask the following before any database work begins:

### Step 1 — Ask the User

> "Do you want to use multiple PostgreSQL schemas in your hosted Supabase project? (e.g. `public`, `app`, `reporting`)"

- If **no**: proceed with the default `public` schema.
- If **yes**: proceed with the multi-schema setup flow below.

### Step 2 — Collect Schema Requirements

Ask:
1. "How many custom schemas do you want to create?"
2. "What are the names of the schemas?" (collect as a list)

Do not proceed until you have explicit schema names from the user.

### Step 3 — Identify the Correct Supabase Project via MCP

- Use the Supabase MCP tools to list all available projects.
- Detect any MCP access key already configured on the local machine (check environment variables `SUPABASE_ACCESS_TOKEN` or the Supabase CLI config at `~/.supabase/access-token`).
- Present the matched project name and ID to the user: "I found your Supabase project: **[project name]** (ID: `[project-id]`). I will make changes to this project only."
- **Do not touch any other project.** If multiple projects are found and the target is ambiguous, ask the user to confirm which one.


### Step 4 — Create Schemas via MCP

For each schema name provided, execute the following SQL via `mcp_com_supabase__execute_sql`:

```sql
CREATE SCHEMA IF NOT EXISTS "<schema_name>";
```

After creation, immediately grant the necessary permissions:

```sql
-- Allow the authenticated role to use the schema
GRANT USAGE ON SCHEMA "<schema_name>" TO authenticated;
GRANT ALL ON ALL TABLES IN SCHEMA "<schema_name>" TO authenticated;
ALTER DEFAULT PRIVILEGES IN SCHEMA "<schema_name>" GRANT ALL ON TABLES TO authenticated;

-- Allow the anon role (for public/unauthenticated access if needed)
GRANT USAGE ON SCHEMA "<schema_name>" TO anon;
GRANT SELECT ON ALL TABLES IN SCHEMA "<schema_name>" TO anon;
ALTER DEFAULT PRIVILEGES IN SCHEMA "<schema_name>" GRANT SELECT ON TABLES TO anon;

-- Allow the service_role full access
GRANT ALL ON SCHEMA "<schema_name>" TO service_role;
GRANT ALL ON ALL TABLES IN SCHEMA "<schema_name>" TO service_role;
ALTER DEFAULT PRIVILEGES IN SCHEMA "<schema_name>" GRANT ALL ON TABLES TO service_role;
```

### Step 5 — Expose Schema via Supabase API

To allow the PostgREST API to expose the new schema, the `search_path` must be updated. This requires a change in the Supabase Dashboard under **Settings → API → Extra search path**.

- **If MCP supports this setting**: apply it automatically.
- **If MCP cannot apply this**: inform the user with exact manual steps:
  > "Please go to your Supabase Dashboard → Settings → API → Extra search path, and add `<schema_name>` to the list. Then click Save."

### Step 6 — Update Environment Variables

After the project is identified and schemas are created, **automatically extract the hosted Supabase connection details via MCP** (`mcp_com_supabase__get_project_url` and `mcp_com_supabase__get_publishable_keys`) and write all required variables to `.env.local`:

```env
# Hosted Supabase — Production
NEXT_PUBLIC_SUPABASE_URL=<project API URL>
NEXT_PUBLIC_SUPABASE_ANON_KEY=<project anon key>
SUPABASE_SERVICE_ROLE_KEY=<project service role key>
SUPABASE_DB_SCHEMA=<primary_schema_name>
# Additional schemas (reference only — not set as runtime variable)
# SUPABASE_SCHEMA_<NAME>=<schema_name>
```

Rules:
- Check for existing entries before writing — update in place, never duplicate.
- `SUPABASE_SERVICE_ROLE_KEY` must **never** have the `NEXT_PUBLIC_` prefix.
- If multiple schemas are used, list them all in comments above `SUPABASE_DB_SCHEMA` so the developer has a clear reference.
- After writing the variables, confirm to the user: "Environment variables have been set in `.env.local`. Your app is now pointed at the hosted Supabase project **[project name]**."

#### Verify the Connection

Once the variables are written, run a quick connectivity check to confirm the production database is reachable:

1. Use `mcp_com_supabase__execute_sql` to run `SELECT 1;` against the target project.
2. If successful: confirm "Connection to hosted Supabase verified. The production database is responding correctly."
3. If it fails: diagnose using `mcp_com_supabase__get_logs`, report the exact error, and fix the configuration before proceeding.

### Step 7 — Handle Missing MCP Token

If the MCP access token is **not found** locally:

1. Inform the user: "No Supabase MCP access token was found. I need a Personal Access Token (PAT) to manage your hosted Supabase project."
2. Ask: "Please provide your Supabase Personal Access Token. You can generate one at: https://supabase.com/dashboard/account/tokens"
3. Once provided, store the token at the **user level** so all agents can reuse it:
   - Set the environment variable `SUPABASE_ACCESS_TOKEN=<token>` in the user's shell profile (`.bashrc`, `.zshrc`, or Windows user environment variables).
   - Confirm: "Token stored. All agents can now access Supabase via MCP using this token."
4. Never hardcode the token in project files or commit it to version control.

## ./.github/instructions/tailwind.instructions.md
---
applyTo: "**/*.tsx,**/*.jsx,**/*.css"
---
# Tailwind CSS v4 Instructions

## Utility-First Approach

- Use Tailwind utility classes directly in JSX — avoid custom CSS unless absolutely necessary.
- Follow a consistent class order: **Layout → Box Model → Typography → Effects → States**.
- For conditional classes, use template literals or a `cn()` helper if `tailwind-merge` and `clsx` are installed.

## Responsive Design

- Use responsive prefixes: `sm:`, `md:`, `lg:`, `xl:`, `2xl:`.
- Mobile-first: write base styles for mobile, then add breakpoint overrides.

## Dark Mode

- Support dark mode with the `dark:` variant.
- Keep colour contrast accessible (WCAG AA minimum).

## Component Patterns

- Create reusable UI components in `src/components/ui/`.
- Prefer standard theme tokens (spacing, colours) over arbitrary values.
- Use only Tailwind v4 syntax — no deprecated Tailwind v3 patterns.

## ./.github/instructions/typescript.instructions.md
---
applyTo: "**/*.ts,**/*.tsx"
---
# TypeScript Best Practices

## Type Safety

- Enable `strict` mode in `tsconfig.json` (already configured).
- Use `import type { ... }` for type-only imports — keeps runtime bundles clean.
- Prefer `interface` for object shapes; use `type` for unions, intersections, and mapped types.
- Never use `any`. Use `unknown` when the type is genuinely unknown, then narrow it.

## Patterns

- Use discriminated unions for state management and API responses.
- Prefer `as const` for literal types and const assertions.
- Use `satisfies` operator to validate types without widening.
- Extract shared types to `src/types/` — keep them co-located if only used in one module.

## Naming Conventions

- **Interfaces/Types:** PascalCase (`UserProfile`, `ApiResponse`).
- **Variables/Functions:** camelCase (`getUserById`, `isLoading`).
- **Constants:** UPPER_SNAKE_CASE for true constants, camelCase for computed values.
- **Components:** PascalCase file names matching the export (`UserCard.tsx`).

## Enums

- Avoid `enum` — use `as const` objects or string literal union types instead.

## ./.github/skills/anforderungsdokument/SKILL.md
﻿---
name: anforderungsdokument
description: >-
  WAMOCON Entwicklungsprompts: Tiefenanalyse, Marketing/UX-Rework und
  Anforderungsdokument (9 Kapitel + Quellenverzeichnis als .docx).
  Workflow: IDEA.md ausfüllen, Skill aufrufen, Dokument prüfen, Freigabe.
---

# WAMOCON Entwicklungsprompts und Anforderungsdokument

## Übersicht

Dieser Skill stellt drei Entwicklungsprompts und eine verbindliche Dokumentstruktur
für WAMOCON-Anforderungsdokumente bereit. Das Anforderungsdokument folgt einer
festen 9-Kapitel-Struktur mit Quellenverzeichnis und wird als .docx generiert.

> **⚠️ PLATTFORMREGEL (ABSOLUT BINDEND):** Alle Anforderungsdokumente und Analysen
> gelten ausschließlich für **Web- und SaaS-Applikationen** (Browser-basiert).
> Mobile Apps (iOS, Android, React Native, Flutter) sind **kein Bestandteil** dieser
> Dokumente und dürfen unter keinen Umständen im Scope erwähnt werden.

> **⚠️ QUELLENREGEL (ABSOLUT BINDEND):** Alle verwendeten Quellen, Statistiken und
> Marktdaten müssen **nicht älter als 1 Jahr** sein (ab aktuellem Datum). Quellen,
> die älter als 12 Monate sind, sind **strikt verboten** und dürfen unter keinen
> Umständen verwendet werden. Kein Erscheinungsdatum → Quelle nicht verwenden.

**Workflow:** IDEA.md ausfüllen → Prompt 3 aufrufen → Dokument prüfen → Freigabe → Implementierung starten.

---

## Prompt 1: Tiefenanalyse und kritische Projektbewertung

Verwende diesen Prompt nach dem Onboarding einer neuen App-Idee, um eine vollumfängliche
Analyse auf Basis des Anforderungsdokuments durchzuführen.

```
Prüfe bitte das aktuelle Projekt und mache dich mit allen Daten und Inhalten vertraut.

Führe anschließend eine vollumfängliche Tiefenanalyse zum Thema der Web-/SaaS-Applikation
aus dem Anforderungsdokument durch. Erstelle dafür:
- Eine vollumfängliche Bedarfsanalyse des geplanten Themas
- Eine Nutzwertanalyse für die Funktionen
- Hinweise auf mögliche Lücken im Markt, die mit der Web-App nicht abgedeckt sind

STRIKT – QUELLENREGEL: Verwende ausschließlich Quellen und Daten, die nicht älter
als 1 Jahr sind. Quellen, die älter als 12 Monate sind, sind verboten.
Im Analysedokument muss jede Zahl mit einer aktuellen Quelle (inkl. Datum) belegt sein.

Fasse deine Ergebnisse in einem Analysedokument zusammen und gib eine Empfehlung ab,
welche Richtung die Web-/SaaS-Applikation nehmen soll, um die größtmögliche
Nutzerplattform und den größten Nutzen zu erzielen.

Erstelle am Ende Entscheidungsvorlagen zur Entscheidung der nächsten Schritte für die
Entwicklung und Ausrichtung der Applikation.

Prüfe intern deine Ergebnisse kritisch und mehrfach, sodass die Ergebnisse brauchbar sind.
```

---

## Prompt 2: Marketing und UX/UI Rework

Verwende diesen Prompt, wenn die Web-Applikation eine Überarbeitung aus Marketing-
und UX-Perspektive benötigt.

```
Bitte führe eine vollständige Analyse und Optimierung des Projektes durch.

Ziel ist eine umfassende Überarbeitung der Web-Applikation aus Marketing- und UX/UI-Perspektive:
- Analysiere die Applikation und passende Oberflächen, Farben, Typografie und Designsystem
- Optimiere den Workflow nach typischen UX-Prinzipien (geführt, unterstützt, intuitiv)
- Stelle sicher, dass die Web-App responsiv ist und auf allen gängigen Browsergrößen
  optimal dargestellt wird (Desktop, Laptop, Tablet) — wir entwickeln ausschließlich
  Web-/SaaS-Applikationen, KEINE mobilen Apps
- Implementiere passende Hilfestellungen für den User

STRIKT – QUELLENREGEL: Verwende ausschließlich Quellen und Daten, die nicht älter
als 1 Jahr sind. Quellen, die älter als 12 Monate sind, sind verboten.

Überarbeite alle Seiten vollständig und führe anschließend alle notwendigen
Fehlerbehebungen durch.
```

---

## Prompt 3: Anforderungsdokument erstellen (9 Kapitel + Quellenverzeichnis)

Verwende diesen Prompt, um ein vollständiges Anforderungsdokument zu erstellen.
Die KI liest `IDEA.md` und das `SKILL.md` automatisch aus dem Projekt — nichts einfügen, nichts ersetzen.

```
Nutze für diese Aufgabe die PERSONA eines interdisziplinären Expertenteams
(Senior Product Manager, Market Research Analyst und Tech Lead) im CEOMODE.
Führe die gesamte Analyse im /godmode und auf L99 aus.

1. Vorbereitung
Lies zunächst diese beiden Dateien vollständig, bevor du beginnst:
- .github/skills/anforderungsdokument/SKILL.md
- IDEA.md

2. Projektrahmen & Kontext
Fokus: Entwicklung eines neuen Web-/SaaS-Tools.
Plattform: Ausschließlich browserbasierte Web- und SaaS-Applikationen.
Tech-Stack: Next.js, Tailwind CSS, TypeScript, Supabase, Vercel.
Strukturiere die technische Architektur als ARCHITECT.

3. Kernaufgabe
Durchdenke die Anforderungen mit /deepthink und erstelle ein vollständiges
WAMOCON-Anforderungsdokument. Halte dich strikt an die verbindliche
9-Kapitel-Struktur aus dem SKILL.md. Fülle jedes Kapitel mit echten, belegten
Daten. Verwende keine Platzhalter.

4. Strikte Restriktionen
Agiere bei der Einhaltung dieser Regeln als SENTINEL:

Plattform-Regel: Mobile Apps sind ausgeschlossen. Die Begriffe iOS, Android,
React Native oder Flutter dürfen im Dokument nicht erwähnt werden.

Quellen-Regel (FACTCHECK & /investigate): Nutze ausschließlich Quellen, die
jünger als ein Jahr sind. Ältere Quellen sind verboten. Jede genannte Zahl muss
mit einer exakten Quellenangabe und dem Veröffentlichungsdatum belegt werden.

Tonalität: Analytisch, datengestützt, kritisch und lösungsorientiert.
Professionell, durchgehend auf Deutsch unter Verwendung echter Umlaute (Ä, Ö, Ü, ß).

5. Ausgabe
Skript: scripts/generate-anforderungsdokument.mjs
Datei: public/Anforderungsdokument_[ProjektName].docx
```

---

## DOKUMENTSTRUKTUR (verbindlich für jedes Anforderungsdokument)

> **⚠️ Gilt ausschließlich für Web-/SaaS-Applikationen. Mobile Apps sind nicht Bestandteil.**

### Deckblatt

Oben: dicke Trennlinie (WAMOCON-Blau).
Titel zentriert: "WAMOCON GMBH" + "Anforderungsdokument" + [Projektname].
Metadaten-Tabelle ohne Rahmen:

| Feld              | Wert                          |
|-------------------|-------------------------------|
| Welle             | [Wellennummer aus IDEA.md]    |
| Projekt           | [App-Name]                    |
| Unternehmen       | WAMOCON GmbH                  |
| App Version       | 1                             |
| Erstellt von      | [Name aus IDEA.md]            |
| Eingereicht an    | [Empfänger aus IDEA.md]       |
| Datum             | [TT.MM.JJJJ aktuell]         |
| Vertraulichkeit   | Intern vertraulich            |
| Status            | Zur Freigabe eingereicht      |

Unten: gestrichelte Trennlinie.

---

### Kapitel 1: Zusammenfassung

- **1.1 Die Idee** — Was macht die Web-/SaaS-App? Welches Problem löst sie? Kernnutzen in 3–5 Sätzen.
- **1.2 Warum jetzt?** — Markttiming: Warum ist das Thema genau jetzt relevant? Mit aktuellen Zahlen belegen (Quellen nicht älter als 1 Jahr).

---

### Kapitel 2: Marktanalyse

- **2.1 Zielgruppe in Zahlen** — Marktgröße, Nutzeranzahl, Wachstumsprognosen. Fokus Deutschland/DACH. Jede Zahl mit Quellenangabe (nicht älter als 1 Jahr).
- **2.2 Infrastruktur/Marktwachstum** — Was wächst? Welche Trends treiben den Markt? Prognosen bis 2030.
- **2.3 Das Kernproblem** — Faktisch belegt: Was ist das konkrete Problem, das die Web-App löst? Warum existiert es heute noch?
- **2.4 Regulatorisches Umfeld** — DSGVO, branchenspezifische Gesetze, EU-Verordnungen. Was stärkt den USP?

---

### Kapitel 3: Wettbewerb

- **3.1 Direkte Wettbewerber** — Tabelle: Anbieter | Stärken | Schwächen/Chance für uns | Preis.
  Echte Anbieter mit echten Daten. Stärken UND Schwächen ehrlich benennen.
- **3.2 Indirekte Wettbewerber / Aggregate** — Tabelle: Anbieter | Was er bietet | Was fehlt (Chance für uns).
- **Marktlücke** — Zusammenfassung: Welche Kombination bietet kein Wettbewerber? Das ist unser Einstieg.

---

### Kapitel 4: Zielgruppe

- **4.1 Primäre Zielgruppe** — Genaue Beschreibung mit Zahlen. Nutzerprofile als Fließtext (Personas mit Name, Rolle, Verhalten).
- **4.2 Sekundäre Zielgruppe** — Wer kommt später dazu? Warum erst später?
- **4.3 Nicht-Zielgruppe** — Wen adressiert die Web-App NICHT? Klar abgrenzen.

---

### Kapitel 5: Nutzen

- **5.1 Nutzen für Kunden** — Tabelle: Problem heute | Lösung durch Web-App | Konkreter Vorteil. Mit messbaren Zahlen (Quellen nicht älter als 1 Jahr).
- **5.2 Nutzen für WAMOCON GmbH** — Warum lohnt sich das Projekt? Einnahmequellen, Skalierungspotenzial, strategischer Wert.

---

### Kapitel 6: Abhängigkeiten und Machbarkeit

- **6.1 Externe Abhängigkeiten** — APIs, Dienste, Datenquellen. Tabelle: Quelle | Was sie liefert | Kosten | Abhängigkeit.
- **6.2 Abrechnungs-/Integrationsoptionen** — Falls relevant: Welche Optionen für Bezahlung/Integration gibt es? Pro Version.
- **6.3 Gesamtbewertung** — Hat V1 kritische Abhängigkeiten? Kann ein Wettbewerber den Start blockieren?

---

### Kapitel 7: Anforderungen Version 1

- **7.1 Hauptprozesse** — Gruppiert nach Themen (z.B. "Dokumenten-Upload", "Frage-Generator").
  Jede Gruppe hat eine eigene Anforderungstabelle:

  | ID   | Anforderung                          | Priorität  | Status |
  |------|--------------------------------------|------------|--------|
  | K-01 | [Kernfunktion]                       | Muss       | Neu    |

- **7.2 Basisfunktionalitäten** — Pflicht für jede Web-App:

  | ID   | Anforderung                                              | Priorität  | Status |
  |------|----------------------------------------------------------|------------|--------|
  | B-01 | Rollen- und Rechteprinzip                                | Muss       | Neu    |
  | B-02 | Anmeldung und Registrierung (E-Mail mit Bestätigung)     | Muss       | Neu    |
  | B-03 | Passwort zurücksetzen                                    | Muss       | Neu    |
  | B-04 | Admin-Bereich für Nutzerverwaltung                       | Muss       | Neu    |
  | B-05 | Profilseite                                              | Muss       | Neu    |
  | B-06 | Dashboard als Startseite                                 | Muss       | Neu    |
  | B-07 | Navigation mit Breadcrumbs                               | Muss       | Neu    |
  | B-08 | Benachrichtigungssystem (In-App und/oder E-Mail)         | Soll       | Neu    |
  | B-09 | Spracheinstellungen (Deutsch und Englisch)               | Muss       | Neu    |
  | B-10 | Dunkel/Hell-Modus                                        | Muss       | Neu    |
  | B-11 | FAQ und Hilfebereich                                     | Soll       | Neu    |
  | B-12 | AGB, Impressum, Datenschutzerklärung                     | Muss       | Neu    |
  | B-13 | Cookie-Banner nach DSGVO                                 | Muss       | Neu    |
  | B-14 | DSGVO-Funktionen (Daten exportieren, Konto löschen)      | Muss       | Neu    |
  | B-15 | Geschäftsmodell (Free und Premium)                       | Muss       | Neu    |
  | B-16 | Upgrade von Free auf Premium in der App                  | Muss       | Neu    |

- **7.3 Scope** — Tabelle: In Scope V1 | Out of Scope (V2+). Klare Abgrenzung.

---

### Kapitel 8: Chancen und Risiken

- **8.1 Chancen** — Tabelle: Chance | Begründung. Mit Zahlen und Quellen (nicht älter als 1 Jahr).
- **8.2 Risiken** — Tabelle: Risiko | Warum es eintreten kann | Gegenmaßnahme.

---

### Kapitel 9: Umsetzungsplan Version 1

- **9.1 Entwicklungsansatz** — Tech-Stack, Werkzeuge (GitHub Copilot), Teamstruktur.
- **9.2 Umsetzungsplan** — Tag-für-Tag-Tabelle über 5–7 Werktage:

  | Tag       | Fokus                       | Inhalt                          |
  |-----------|-----------------------------|---------------------------------|
  | Tag 1–3   | Hauptprozesse               | [Details]                       |
  | Tag 3–4   | Testing und Bugfixing       | [Details]                       |
  | Tag 4–5   | Basisfunktionalitäten       | [Details]                       |
  | Tag 5–6   | Puffer                      | [Details]                       |

- **Hinweis** — Realistisch: V1 ist ein lauffähiger Prototyp, kein Endprodukt.

---

### Quellenverzeichnis

Tabelle: Nr. | Quelle/URL | Inhalt | Veröffentlichungsdatum.
Nur reale, öffentlich verfügbare Quellen.

**STRIKT:** Ausschließlich Quellen, die nicht älter als 1 Jahr sind.
Jede Zahl im Dokument muss mindestens eine Quelle haben.
Das Veröffentlichungsdatum muss für jede Quelle angegeben sein.

---

## FORMATREGELN

- **Sprache:** Deutsch mit echten Umlauten (Ä, Ö, Ü, ß). In Code-Variablennamen ist ae/oe/ue akzeptabel.
- **Schrift:** Arial Narrow, 11pt Fließtext.
- **Tabellenkopf:** WAMOCON-Blau (1E3A5F) mit weißem Text, fett.
- **Tabellenzeilen:** alternierend weiß / hellgrau (F5F5F5).
- **Breiten:** WidthType.DXA (keine Prozent).
- **Shading:** ShadingType.CLEAR (kein SOLID).
- **Kein \n in TextRun** — separate Paragraphen verwenden.
- **Seitenkopf:** "WAMOCON GmbH, Mergenthalerallee 79-81, 65760 Eschborn" (8pt, grau).
- **Seitenumbruch** zwischen den Hauptkapiteln.

---

## Workflow

```
[1] IDEA.md im Projekt-Root ausfüllen
        |
        v
[2] Prompt 3 aufrufen → Anforderungsdokument als .docx generieren
        |
        v
[3] Dokument prüfen und zur Freigabe einreichen (Geschäftsführung)
        |
        v
[4] Nach Freigabe: Prompt 1 für Tiefenanalyse aufrufen
        |
        v
[5] Implementierung mit @planner → @developer
        |
        v
[6] Nach Launch: Prompt 2 für UX/UI Rework
```

---

## Voraussetzungen

- Node.js >= 18
- npm install docx (einmalig)
- Ausgabe: public/Anforderungsdokument_[ProjektName].docx
- package.json: "gen:anforderungsdokument": "node scripts/generate-anforderungsdokument.mjs"
## ./.github/skills/memory-merger/SKILL.md
---
name: memory-merger
description: 'Merges mature lessons from a domain memory file into its instruction file. Syntax: `/memory-merger >domain [scope]` where scope is `global` (default), `user`, `workspace`, or `ws`.'
---

# Memory Merger

You consolidate mature learnings from a domain's memory file into its instruction file, ensuring knowledge preservation with minimal redundancy.

**Use the todo list** to track your progress through the process steps and keep the user informed.

## Scopes

Memory instructions can be stored in two scopes:

- **Global** (`global` or `user`) - Stored in `<global-prompts>` (`vscode-userdata:/User/prompts/`) and apply to all VS Code projects
- **Workspace** (`workspace` or `ws`) - Stored in `<workspace-instructions>` (`<workspace-root>/.github/instructions/`) and apply only to the current project

Default scope is **global**.

Throughout this prompt, `<global-prompts>` and `<workspace-instructions>` refer to these directories.

## Syntax

```
/memory-merger >domain-name [scope]
```

- `>domain-name` - Required. The domain to merge (e.g., `>clojure`, `>git-workflow`, `>prompt-engineering`)
- `[scope]` - Optional. One of: `global`, `user` (both mean global), `workspace`, or `ws`. Defaults to `global`

**Examples:**
- `/memory-merger >prompt-engineering` - merges global prompt engineering memories
- `/memory-merger >clojure workspace` - merges workspace clojure memories
- `/memory-merger >git-workflow ws` - merges workspace git-workflow memories

## Process

### 1. Parse Input and Read Files

- **Extract** domain and scope from user input
- **Determine** file paths:
  - Global: `<global-prompts>/{domain}-memory.instructions.md` → `<global-prompts>/{domain}.instructions.md`
  - Workspace: `<workspace-instructions>/{domain}-memory.instructions.md` → `<workspace-instructions>/{domain}.instructions.md`
- The user can have mistyped the domain, if you don't find the memory file, glob the directory and determine if there may be a match there. Ask the user for input if in doubt.
- **Read** both files (memory file must exist; instruction file may not)

### 2. Analyze and Propose

Review all memory sections and present them for merger consideration:

```
## Proposed Memories for Merger

### Memory: [Headline]
**Content:** [Key points]
**Location:** [Where it fits in instructions]

[More memories]...
```

Say: "Please review these memories. Approve all with 'go' or specify which to skip."

**STOP and wait for user input.**

### 3. Define Quality Bar

Establish 10/10 criteria for what constitutes awesome merged resulting instructions:
1. **Zero knowledge loss** - Every detail, example, and nuance preserved
2. **Minimal redundancy** - Overlapping guidance consolidated
3. **Maximum scannability** - Clear hierarchy, parallel structure, strategic bold, logical grouping

### 4. Merge and Iterate

Develop the final merged instructions **without updating files yet**:

1. Draft the merged instructions incorporating approved memories
2. Evaluate against quality bar
3. Refine structure, wording, organization
4. Repeat until the merged instructions meet 10/10 criteria

### 5. Update Files

Once the final merged instructions meet 10/10 criteria:

- **Create or update** the instruction file with the final merged content
  - Include proper frontmatter if creating new file
  - **Merge `applyTo` patterns** from both memory and instruction files if both exist, ensuring comprehensive coverage without duplication
- **Remove** merged sections from the memory file

## Example

```
User: "/memory-merger >clojure"

Agent:
1. Reads clojure-memory.instructions.md and clojure.instructions.md
2. Proposes 3 memories for merger
3. [STOPS]

User: "go"

Agent:
4. Defines quality bar for 10/10
5. Merges new instructions candidate, iterates to 10/10
6. Updates clojure.instructions.md
7. Cleans clojure-memory.instructions.md
```

## ./.github/skills/next-browser/SKILL.md
---
name: next-browser
description: >-
  CLI that gives agents what humans get from React DevTools and the Next.js
  dev overlay — component trees, props, hooks, PPR shells, errors, network —
  as shell commands that return structured text.
---

# next-browser

If `next-browser` is not already on PATH, install `@vercel/next-browser` globally, then install the Chromium browser:

```bash
npm install -g @vercel/next-browser
playwright install chromium
```

Requires Node >= 20. If already installed, check the version is current:

```bash
next-browser --version
npm view @vercel/next-browser version
# if outdated:
npm install -g @vercel/next-browser@latest
```

---

## Next.js docs awareness

If the project's Next.js version is **v16.2.0-canary.37 or later**, bundled docs live at `node_modules/next/dist/docs/`. Before doing PPR work, Cache Components work, or any non-trivial Next.js task, read the relevant doc there — your training data may be outdated. The bundled docs are the source of truth.

---

## Working with the user

### Onboarding

- If the user already gave a URL, cookies, and task — skip questions, `open` and go.
- Otherwise ask only what's missing: dev server URL (running?), session cookies if behind login.
- For cookies, give the user two options: (1) DevTools → Application → Cookies, export as `[{"name":"session","value":"..."}]`, or (2) "Copy as cURL" from DevTools → Network on any authenticated request — extract the cookies from the header yourself.
- Never say "ready, what would you like to do?". Never auto-discover (port scans, `project`, config reads) before being asked.

### Show, don't tell

- `screenshot` after every navigation, code change, or visual finding. Always caption it.
- Don't narrate what a screenshot shows. State your conclusion or next action.

### Escalate, don't decide

- Suspense boundary placement and fallback UI — design with the user.
- Caching decisions (staleness, visibility) — the user's call, not yours.
- "Make this page faster" without context — ask: cold URL hit or client navigation? Don't guess, don't do both.

---

## Headless mode

By default the browser opens headed (visible window). For CI or environments with no display, set `NEXT_BROWSER_HEADLESS=1` to run headless.

---

## Commands

### Browser lifecycle

| Command | Description |
|---|---|
| `open <url> [--cookies-json <file>]` | Launch browser and navigate (with optional cookies) |
| `close` | Close browser and kill daemon |

```bash
$ next-browser open http://localhost:3000
$ next-browser open http://localhost:3000 --cookies-json cookies.json
# Cookie file format: [{"name":"authorization","value":"Bearer ..."}]
```

---

### Navigation

| Command | Description |
|---|---|
| `goto <url>` | Full-page navigation (new document load) |
| `push [path]` | Client-side navigation (interactive picker if no path) |
| `back` | Go back in history |
| `reload` | Reload current page |
| `restart-server` | Restart the Next.js dev server (clears caches — last resort only) |
| `ssr lock` | Block external scripts on all navigations (SSR-only mode) |
| `ssr unlock` | Re-enable external scripts |

---

### Inspection

| Command | Description |
|---|---|
| `tree` | Full React component tree (hierarchy, IDs, keys) |
| `tree <id>` | Inspect one component (props, hooks, state, source location) |
| `snapshot` | Accessibility tree with `[ref=eN]` markers on interactive elements |
| `errors` | Build and runtime errors for the current page |
| `logs` | Recent dev server log output |
| `browser-logs` | Browser-side console output (log, warn, error, info) |
| `network [idx]` | List network requests, or inspect one (headers, body) |

```bash
$ next-browser snapshot
- navigation "Main"
  - link "Home" [ref=e0]
  - link "Dashboard" [ref=e1]
- main
  - heading "Settings"
  - tablist
    - tab "General" [ref=e2] (selected)
    - tab "Security" [ref=e3]

$ next-browser tree
# Columns: depth id parent name
0 38167 - Root
1 38168 38167 HeadManagerContext.Provider
...
224 46375 46374 DeploymentsProvider

$ next-browser tree 46375
path: Root > ... > DeploymentsProvider
DeploymentsProvider #46375
props:
  children: [<Lazy />, ...]
hooks:
  Router: undefined (2 sub)
source: app/.../context.tsx:180:10
```

---

### Interaction

| Command | Description |
|---|---|
| `click <ref\|text\|selector>` | Click via real pointer events (works with Radix, Headless UI) |
| `fill <ref\|selector> <value>` | Fill a text input or textarea |
| `eval [ref] <script>` | Run JS in page context |
| `viewport [WxH]` | Show or set viewport size |

```bash
$ next-browser click e3          # ref from snapshot
$ next-browser click "Security"  # plain text
$ next-browser fill e4 "myuser"
$ next-browser viewport 375x812  # mobile breakpoint
$ next-browser eval 'document.title'
```

---

### Performance & PPR

| Command | Description |
|---|---|
| `perf [url]` | Core Web Vitals + React hydration timing in one pass |
| `renders start` | Begin recording React re-renders |
| `renders stop [--json]` | Stop and print per-component render profile |
| `ppr lock` | Freeze dynamic content to inspect the static shell |
| `ppr unlock` | Resume dynamic content and print shell analysis |

```bash
$ next-browser perf http://localhost:3000/dashboard
# Core Web Vitals
  TTFB    42ms
  LCP     1205.3ms
  CLS     0.03
# React Hydration — 65.5ms

$ next-browser renders start
$ next-browser renders stop
# 426 renders (38 mounts + 388 re-renders) across 38 components
# FPS: avg 120, min 106
```

---

### Screenshots

| Command | Description |
|---|---|
| `screenshot [caption] [--full-page]` | Viewport (or full page) PNG to temp file |
| `preview [caption]` | Screenshot + open in viewer window |

---

### Next.js MCP

| Command | Description |
|---|---|
| `page` | Route segments for the current URL |
| `project` | Project root and dev server URL |
| `routes` | All app router routes |
| `action <id>` | Inspect a server action by ID |

---

## Scenarios

### Debug a visual or interaction issue

1. `open http://localhost:3000`
2. `snapshot` — discover interactive elements
3. `click eN` / `fill eN value` — interact
4. `errors` — check for runtime errors
5. `screenshot "before fix"` — document state
6. Make the code change, HMR picks it up
7. `screenshot "after fix"` — verify

### Profile performance

```bash
$ next-browser perf http://localhost:3000/dashboard
# → Core Web Vitals + hydration timing

$ next-browser renders start
# reproduce slow interaction
$ next-browser renders stop
# → per-component render counts, self time, change reasons
```

### Debug PPR shell

```bash
$ next-browser ppr lock
$ next-browser goto http://localhost:3000/page
$ next-browser screenshot "PPR shell — locked"
$ next-browser ppr unlock
# → Shell analysis: which Suspense boundaries are holes and why
```

### Test responsive layout

```bash
$ next-browser viewport 375x812   # mobile
$ next-browser screenshot "mobile"
$ next-browser viewport 1440x900  # desktop
$ next-browser screenshot "desktop"
```

### Debug component re-renders

1. `renders start`
2. `goto` the page (captures hydration)
3. Reproduce the interaction
4. `renders stop` — read Mounts vs Re-renders, Self time, change reasons
5. `tree <id>` the expensive component — check source, props, hooks
6. Fix, HMR picks it up, re-run `renders start/stop` to verify

## ./AGENTS.md
﻿
---

# GitHub Copilot Customisation

<table>
<tr>
<th width="50%">DE Deutsch</th>
<th width="50%">EN English</th>
</tr>
<tr>
<td>Dieses Projekt nutzt GitHub Copilot Agents und Instructions, um eine strukturierte und produktive KI-gestützte Entwicklung zu ermöglichen.</td>
<td>This project uses GitHub Copilot Agents and Instructions to enable a structured and productive AI-assisted development workflow.</td>
</tr>
</table>

---

## Übersicht / Overview

| Typ / Type | Pfad / Path | Beschreibung / Description |
|---|---|---|
| **Global Instructions** | `.github/copilot-instructions.md` | Projektweite Basisregeln für alle Copilot-Interaktionen. / Project-wide baseline rules for all Copilot interactions. |
| **Instructions** | `.github/instructions/*.instructions.md` | Dateimuster-spezifische Coding-Richtlinien. / File-pattern-scoped coding guidelines. |
| **Agents** | `.github/agents/*.agent.md` | Spezialisierte KI-Personas für verschiedene Phasen. / Specialised AI personas for different development phases. |

---

## `copilot-instructions.md` — Globale Basisregeln / Global Baseline Rules

**Pfad / Path:** `.github/copilot-instructions.md`

<table>
<tr>
<th width="50%">DE Was ist das?</th>
<th width="50%">EN What is it?</th>
</tr>
<tr>
<td>Diese Datei wird bei <strong>jeder</strong> Copilot-Interaktion automatisch geladen. Sie definiert den Tech-Stack, kritische Regeln (async APIs, Server Components, Supabase), und Code-Stil-Konventionen für das gesamte Projekt.</td>
<td>This file is automatically loaded on <strong>every</strong> Copilot interaction. It defines the tech stack, critical rules (async APIs, Server Components, Supabase), and code style conventions for the whole project.</td>
</tr>
</table>

<table>
<tr>
<th width="50%">DE Wann bearbeiten?</th>
<th width="50%">EN When to edit?</th>
</tr>
<tr>
<td>
- Tech-Stack ändert sich (z. B. neue Bibliothek wird Standardmuster)<br>
- Neue projektweite Regeln sollen für alle Copilot-Interaktionen gelten<br>
- Team-Konventionen ändern sich<br>
<strong>⚠️ Kurz halten</strong> — diese Datei wird immer in den Kontext geladen.
</td>
<td>
- Tech stack changes (e.g. a new library becomes a standard pattern)<br>
- New project-wide rules need to apply to all Copilot interactions<br>
- Team conventions change<br>
<strong>⚠️ Keep it short</strong> — this file is always loaded into context.
</td>
</tr>
</table>

---

## Instructions — Datei-spezifische Richtlinien / File-Scoped Guidelines

<table>
<tr>
<th width="50%">DE Was sind Instructions?</th>
<th width="50%">EN What are Instructions?</th>
</tr>
<tr>
<td>Instructions sind Richtlinien, die automatisch geladen werden, wenn Copilot an Dateien arbeitet, die dem <code>applyTo</code>-Glob-Muster entsprechen. Sie ergänzen die globalen Regeln mit datei-spezifischen Details.</td>
<td>Instructions are guidelines that are automatically loaded when Copilot works on files matching the <code>applyTo</code> glob pattern. They extend the global rules with file-type-specific details.</td>
</tr>
</table>

### Vorhandene Instructions / Available Instructions

| Datei / File | `applyTo` | Zweck / Purpose |
|---|---|---|
| `nextjs.instructions.md` | `**/*.tsx, **/*.ts, **/*.jsx, **/*.js` | Next.js 16 App Router Patterns, async APIs, Server/Client Components |
| `tailwind.instructions.md` | `**/*.tsx, **/*.jsx, **/*.css` | Tailwind CSS v4 Utility-First Patterns, Responsive Design |
| `typescript.instructions.md` | `**/*.ts, **/*.tsx` | TypeScript Strict Mode, Naming Conventions, Type Safety |
| `supabase.instructions.md` | `**/supabase/**, **/*supabase*` | Supabase Client Setup, RLS, Migrations, Schema Awareness |

### Eigene Instructions erstellen / Creating Custom Instructions

<table>
<tr>
<th width="50%">DE Anleitung</th>
<th width="50%">EN Guide</th>
</tr>
<tr>
<td>Erstelle eine <code>.instructions.md</code>-Datei in <code>.github/instructions/</code> mit YAML-Frontmatter. Das <code>applyTo</code>-Feld akzeptiert Glob-Muster und bestimmt, für welche Dateien die Regeln gelten.</td>
<td>Create a <code>.instructions.md</code> file in <code>.github/instructions/</code> with YAML frontmatter. The <code>applyTo</code> field accepts glob patterns and determines which files the rules apply to.</td>
</tr>
</table>

```yaml
---
applyTo: "**/*.tsx"
---
# Your instructions here
```

---

## Agents — KI-Personas / AI Personas

<table>
<tr>
<th width="50%">DE Was sind Agents?</th>
<th width="50%">EN What are Agents?</th>
</tr>
<tr>
<td>Agents sind spezialisierte KI-Personas. Du rufst sie in VS Code über das Chat-Panel mit <code>@agent-name</code> auf. Jeder Agent hat eine klar definierte Rolle, einen Workflow und Regeln.</td>
<td>Agents are specialised AI personas. You invoke them in VS Code via the Chat panel using <code>@agent-name</code>. Each agent has a clearly defined role, workflow, and rules.</td>
</tr>
</table>

---

### `@planner` — Planer

<table>
<tr>
<th width="50%">DE</th>
<th width="50%">EN</th>
</tr>
<tr>
<td><strong>Zweck:</strong> Technische Planung und Anforderungsanalyse vor dem Coding.</td>
<td><strong>Purpose:</strong> Technical planning and requirements analysis before coding.</td>
</tr>
<tr>
<td><strong>Wann verwenden:</strong><br>— Vor dem Start eines neuen Features<br>— Wenn die Anforderungen unklar sind<br>— Vor Refactoring oder Migrations-Aufgaben</td>
<td><strong>When to use:</strong><br>— Before starting a new feature<br>— When requirements are unclear<br>— Before refactoring or migration tasks</td>
</tr>
<tr>
<td><strong>Was er tut:</strong><br>✔ Codebase erkunden und Kontext sammeln<br>✔ Betroffene Dateien und Module identifizieren<br>✔ Nummerierten Implementierungsplan erstellen<br>✘ <strong>Schreibt keinen Code</strong></td>
<td><strong>What it does:</strong><br>✔ Explore codebase and gather context<br>✔ Identify affected files and modules<br>✔ Create a numbered implementation plan<br>✘ <strong>Does not write code</strong></td>
</tr>
<tr>
<td><strong>Verwendung:</strong> <code>@planner Füge eine Authentifizierungsseite hinzu</code></td>
<td><strong>Usage:</strong> <code>@planner Add an authentication page</code></td>
</tr>
</table>

---

### `@developer` — Entwickler

<table>
<tr>
<th width="50%">DE</th>
<th width="50%">EN</th>
</tr>
<tr>
<td><strong>Zweck:</strong> Strukturierte Feature-Implementierung mit Qualitätsprüfungen.</td>
<td><strong>Purpose:</strong> Structured feature implementation with quality checks.</td>
</tr>
<tr>
<td><strong>Wann verwenden:</strong><br>— Nach der Planung mit <code>@planner</code><br>— Zur Implementierung von Features, Seiten, API-Routen<br>— Für Datenbankänderungen und Migrationen</td>
<td><strong>When to use:</strong><br>— After planning with <code>@planner</code><br>— To implement features, pages, API routes<br>— For database changes and migrations</td>
</tr>
<tr>
<td><strong>Vierphasiger Prozess:</strong><br>1. <strong>Vorbereitung</strong> — Plan lesen, Code verstehen<br>2. <strong>Implementierung</strong> — Schrittweise, Fehler sofort beheben<br>3. <strong>Verifikation (PFLICHT)</strong> — <code>typecheck</code> → <code>lint</code> → <code>build</code> → lokal testen<br>4. <strong>Dokumentation</strong> — Handbook aktualisieren</td>
<td><strong>Four-phase process:</strong><br>1. <strong>Preparation</strong> — Read plan, understand code<br>2. <strong>Implementation</strong> — Step by step, fix errors immediately<br>3. <strong>Verification (MANDATORY)</strong> — <code>typecheck</code> → <code>lint</code> → <code>build</code> → test locally<br>4. <strong>Documentation</strong> — Update handbook</td>
</tr>
<tr>
<td><strong>Verwendung:</strong> <code>@developer Implementiere diesen Plan: [Plan einfügen]</code></td>
<td><strong>Usage:</strong> <code>@developer Implement this plan: [paste plan]</code></td>
</tr>
</table>

---

### `@reviewer` — Code-Reviewer

<table>
<tr>
<th width="50%">DE</th>
<th width="50%">EN</th>
</tr>
<tr>
<td><strong>Zweck:</strong> Code-Review und Qualitätssicherung vor dem PR.</td>
<td><strong>Purpose:</strong> Code review and quality assurance before a PR.</td>
</tr>
<tr>
<td><strong>Wann verwenden:</strong><br>— Bevor ein PR erstellt wird<br>— Nach einer Implementierung zur Qualitätsprüfung<br>— Zur Sicherheits- und Performance-Analyse</td>
<td><strong>When to use:</strong><br>— Before creating a PR<br>— After implementation for quality check<br>— For security and performance audits</td>
</tr>
<tr>
<td><strong>Was er tut:</strong><br>✔ Strukturierte Checkliste (Qualität, Next.js 16, Supabase-Sicherheit, Styling)<br>✔ Alle Checks ausführen (typecheck, lint, build)<br>✔ Review-Bericht mit Status (✅ / ⚠️ / ❌)</td>
<td><strong>What it does:</strong><br>✔ Structured checklist (quality, Next.js 16, Supabase security, styling)<br>✔ Run all checks (typecheck, lint, build)<br>✔ Review report with status (✅ / ⚠️ / ❌)</td>
</tr>
<tr>
<td><strong>Verwendung:</strong> <code>@reviewer Überprüfe die Änderungen in src/app/dashboard/</code></td>
<td><strong>Usage:</strong> <code>@reviewer Review the changes in src/app/dashboard/</code></td>
</tr>
</table>

---

### `@anforderungsdokument` — Anforderungsdokument

<table>
<tr>
<th width="50%">DE</th>
<th width="50%">EN</th>
</tr>
<tr>
<td><strong>Zweck:</strong> Vollständiges WAMOCON-Anforderungsdokument (9 Kapitel + .docx) für Web-/SaaS-Applikationen erstellen.</td>
<td><strong>Purpose:</strong> Create a complete WAMOCON requirements document (9 chapters + .docx) for web/SaaS applications.</td>
</tr>
<tr>
<td><strong>Wann verwenden:</strong><br>— Vor dem Start eines neuen Projekts<br>— Wenn eine App-Idee dokumentiert werden soll<br>— Bevor die Implementierung beginnt (Freigabe erforderlich)</td>
<td><strong>When to use:</strong><br>— Before starting a new project<br>— When an app idea needs to be documented<br>— Before implementation starts (approval required)</td>
</tr>
<tr>
<td><strong>Was er tut:</strong><br>✔ Marktanalyse, Wettbewerb, Zielgruppe recherchieren<br>✔ 9-Kapitel-Dokument mit echten Daten befüllen<br>✔ Dokument als .docx generieren<br>✘ <strong>Nur Web/SaaS — keine mobilen Apps</strong><br>✘ <strong>Nur Quellen nicht älter als 1 Jahr</strong></td>
<td><strong>What it does:</strong><br>✔ Research market analysis, competition, target audience<br>✔ Fill 9-chapter document with real data<br>✔ Generate document as .docx<br>✘ <strong>Web/SaaS only — no mobile apps</strong><br>✘ <strong>Sources not older than 1 year only</strong></td>
</tr>
<tr>
<td><strong>Verwendung:</strong> <code>@anforderungsdokument Erstelle das Anforderungsdokument für [Projektname]</code></td>
<td><strong>Usage:</strong> <code>@anforderungsdokument Create the requirements document for [project name]</code></td>
</tr>
</table>

#### Schritt-für-Schritt-Anleitung / Step-by-Step Guide

**1.** Fülle `IDEA.md` im Projekt-Root aus.

**2.** Kopiere den Prompt unten und sende ihn im Chat. Die KI liest `IDEA.md` und `SKILL.md` automatisch — nichts einfügen, nichts ersetzen:

```
Nutze für diese Aufgabe die PERSONA eines interdisziplinären Expertenteams
(Senior Product Manager, Market Research Analyst und Tech Lead) im CEOMODE.
Führe die gesamte Analyse im /godmode und auf L99 aus.

1. Vorbereitung
Lies zunächst diese beiden Dateien vollständig, bevor du beginnst:
- .github/skills/anforderungsdokument/SKILL.md
- IDEA.md

2. Projektrahmen & Kontext
Fokus: Entwicklung eines neuen Web-/SaaS-Tools.
Plattform: Ausschließlich browserbasierte Web- und SaaS-Applikationen.
Tech-Stack: Next.js, Tailwind CSS, TypeScript, Supabase, Vercel.
Strukturiere die technische Architektur als ARCHITECT.

3. Kernaufgabe
Durchdenke die Anforderungen mit /deepthink und erstelle ein vollständiges
WAMOCON-Anforderungsdokument. Halte dich strikt an die verbindliche
9-Kapitel-Struktur aus dem SKILL.md. Fülle jedes Kapitel mit echten, belegten
Daten. Verwende keine Platzhalter.

4. Strikte Restriktionen
Agiere bei der Einhaltung dieser Regeln als SENTINEL:

Plattform-Regel: Mobile Apps sind ausgeschlossen. Die Begriffe iOS, Android,
React Native oder Flutter dürfen im Dokument nicht erwähnt werden.

Quellen-Regel (FACTCHECK & /investigate): Nutze ausschließlich Quellen, die
jünger als ein Jahr sind. Ältere Quellen sind verboten. Jede genannte Zahl muss
mit einer exakten Quellenangabe und dem Veröffentlichungsdatum belegt werden.

Tonalität: Analytisch, datengestützt, kritisch und lösungsorientiert.
Professionell, durchgehend auf Deutsch unter Verwendung echter Umlaute (Ä, Ö, Ü, ß).

5. Ausgabe
Skript: scripts/generate-anforderungsdokument.mjs
Datei: public/Anforderungsdokument_[ProjektName].docx
```

**3.** Dokument prüfen und zur Freigabe bei der Geschäftsführung einreichen.

**4.** Nach Freigabe: Implementierung mit `@planner` starten.

---

## Tools

| Tool | Pfad / Path | Zweck / Purpose |
|---|---|---|
| **next-browser** | `.github/skills/next-browser/SKILL.md` | CLI that exposes React DevTools and the Next.js dev overlay as shell commands — component trees, props, errors, performance, screenshots — structured output for AI agents. |
| **anforderungsdokument** | `.github/skills/anforderungsdokument/SKILL.md` | Drei Entwicklungsprompts: Tiefenanalyse, Marketing/UX-Rework und Anforderungsdokument (9 Kapitel + Quellenverzeichnis als .docx). Nur Web/SaaS — keine mobilen Apps. Nur Quellen nicht älter als 1 Jahr. IDEA.md ausfüllen, Prompt 3 aufrufen, .docx generieren, zur Freigabe einreichen. |

### `next-browser` — AI-Driven Browser for Next.js

<table>
<tr>
<th width="50%">DE Was ist das?</th>
<th width="50%">EN What is it?</th>
</tr>
<tr>
<td><code>@vercel/next-browser</code> ist ein CLI-Tool, das React DevTools und das Next.js Dev-Overlay als Shell-Befehle bereitstellt. Agents können den Browser steuern, Komponenten inspizieren, Fehler lesen und Performance prüfen — ohne manuell durch DevTools zu klicken.</td>
<td><code>@vercel/next-browser</code> is a CLI tool that exposes React DevTools and the Next.js dev overlay as shell commands. Agents can drive the browser, inspect components, read errors, and check performance — without manually clicking through DevTools.</td>
</tr>
<tr>
<td><strong>Wann verwenden:</strong><br>— Nach der Implementierung zur visuellen Verifikation<br>— Debugging von Runtime-Fehlern oder Re-Render-Problemen<br>— Performance-Analyse (Core Web Vitals, Hydration)<br>— PPR-Shell-Debugging</td>
<td><strong>When to use:</strong><br>— After implementation for visual verification<br>— Debugging runtime errors or re-render issues<br>— Performance analysis (Core Web Vitals, hydration timing)<br>— PPR shell debugging</td>
</tr>
<tr>
<td><strong>Installation:</strong><br><code>npm install -g @vercel/next-browser</code><br><code>playwright install chromium</code><br>Benötigt Node >= 20</td>
<td><strong>Install:</strong><br><code>npm install -g @vercel/next-browser</code><br><code>playwright install chromium</code><br>Requires Node >= 20</td>
</tr>
<tr>
<td><strong>Wichtigste Befehle:</strong><br><code>next-browser open &lt;url&gt;</code> — Browser starten<br><code>next-browser snapshot</code> — Accessibility-Tree + klickbare Refs<br><code>next-browser errors</code> — Build- und Runtime-Fehler<br><code>next-browser perf</code> — Core Web Vitals + Hydration<br><code>next-browser screenshot</code> — Viewport als PNG<br><code>next-browser tree</code> — React-Komponentenbaum</td>
<td><strong>Key commands:</strong><br><code>next-browser open &lt;url&gt;</code> — launch browser<br><code>next-browser snapshot</code> — accessibility tree + clickable refs<br><code>next-browser errors</code> — build and runtime errors<br><code>next-browser perf</code> — Core Web Vitals + hydration timing<br><code>next-browser screenshot</code> — viewport as PNG<br><code>next-browser tree</code> — React component tree</td>
</tr>
<tr>
<td><strong>Vollständige Dokumentation:</strong> <code>.github/skills/next-browser/SKILL.md</code></td>
<td><strong>Full documentation:</strong> <code>.github/skills/next-browser/SKILL.md</code></td>
</tr>
</table>

---

### `anforderungsdokument` — WAMOCON Entwicklungsprompts

<table>
<tr>
<th width="50%">DE Was ist das?</th>
<th width="50%">EN What is it?</th>
</tr>
<tr>
<td>Der Skill stellt <strong>drei strukturierte Entwicklungsprompts</strong> bereit: (1) Tiefenanalyse und kritische Projektbewertung, (2) Marketing und UX/UI Rework, (3) Anforderungsdokument mit verbindlicher 9-Kapitel-Struktur (Zusammenfassung, Marktanalyse, Wettbewerb, Zielgruppe, Nutzen, Abhängigkeiten, Anforderungen V1, Chancen/Risiken, Umsetzungsplan + Quellenverzeichnis). <strong>Ausschließlich Web/SaaS — keine mobilen Apps. Nur Quellen nicht älter als 1 Jahr.</strong> IDEA.md ausfüllen, Prompt aus <code>@anforderungsdokument</code> kopieren, .docx generieren, zur Freigabe einreichen.</td>
<td>The skill provides <strong>three structured development prompts</strong>: (1) deep analysis and critical assessment, (2) marketing and UX/UI rework, (3) requirements document with a mandatory 9-chapter structure (summary, market analysis, competition, target audience, benefits, dependencies, requirements V1, opportunities/risks, implementation plan + references). <strong>Web/SaaS only — no mobile apps. Sources not older than 1 year only.</strong> Fill in IDEA.md, copy prompt from <code>@anforderungsdokument</code>, generate .docx, submit for approval.</td>
</tr>
</table>

---

## Empfohlener Workflow / Recommended Workflow

<table>
<tr>
<th width="50%">DE Schritt</th>
<th width="50%">EN Step</th>
</tr>
<tr>
<td><strong>Phase 0 — Anforderungen (neues Projekt):</strong><br>
1. <code>IDEA.md</code> im Projekt-Root ausfüllen<br>
2. <strong><code>@anforderungsdokument</code></strong> aufrufen: Prompt kopieren und senden<br>
3. Dokument prüfen und zur Freigabe einreichen<br>
4. Nach Freigabe: Implementierung starten</td>
<td><strong>Phase 0 — Requirements (new project):</strong><br>
1. Fill in <code>IDEA.md</code> in the project root<br>
2. Call <strong><code>@anforderungsdokument</code></strong>: copy prompt and send<br>
3. Review document and submit for approval<br>
4. After approval: start implementation</td>
</tr>
<tr>
<td><strong>Phase 1 — Planung:</strong><br>
<strong><code>@planner</code></strong> — Aufgabe analysieren und Implementierungsplan erstellen</td>
<td><strong>Phase 1 — Planning:</strong><br>
<strong><code>@planner</code></strong> — Analyse the task and create an implementation plan</td>
</tr>
<tr>
<td><strong>Phase 2 — Implementierung:</strong><br>
<strong><code>@developer</code></strong> — Plan entgegennehmen und schrittweise implementieren</td>
<td><strong>Phase 2 — Implementation:</strong><br>
<strong><code>@developer</code></strong> — Receive plan and implement step by step</td>
</tr>
<tr>
<td><strong>Phase 3 — Qualitätsprüfung:</strong><br>
<strong><code>@reviewer</code></strong> — Code prüfen, bevor ein PR erstellt wird</td>
<td><strong>Phase 3 — Quality review:</strong><br>
<strong><code>@reviewer</code></strong> — Review code before creating a PR</td>
</tr>
</table>

---

## Eigene Agents erstellen / Creating Custom Agents

<table>
<tr>
<th width="50%">DE Anleitung</th>
<th width="50%">EN Guide</th>
</tr>
<tr>
<td>Erstelle eine <code>.agent.md</code>-Datei in <code>.github/agents/</code> mit YAML-Frontmatter. Definiere Rolle, Workflow und Regeln.</td>
<td>Create a <code>.agent.md</code> file in <code>.github/agents/</code> with YAML frontmatter. Define role, workflow, and rules.</td>
</tr>
</table>

```yaml
---
name: MyAgent
description: >
  Description of what this agent does.
---
# Agent: MyAgent

## Role
...

## Workflow
...
```

---

## Wenn ein Agent schlecht antwortet / When an Agent Responds Poorly

<table>
<tr>
<th width="50%">DE Problem & Lösung</th>
<th width="50%">EN Problem & Solution</th>
</tr>
<tr>
<td><strong>Agent ignoriert Regeln aus der Instructions-Datei</strong><br>→ Prüfe das <code>applyTo</code>-Glob-Muster — stimmt es mit der Datei überein, die du bearbeitest? Teste mit: <code>**/*.ts</code> statt <code>src/**/*.ts</code></td>
<td><strong>Agent ignores rules from an Instructions file</strong><br>→ Check the <code>applyTo</code> glob pattern — does it match the file you are editing? Try broader patterns: <code>**/*.ts</code> instead of <code>src/**/*.ts</code></td>
</tr>
<tr>
<td><strong>Agent befolgt den Workflow nicht (z. B. überspringt typecheck)</strong><br>→ Öffne die <code>.agent.md</code>-Datei und mache die Anweisung strikter. Ersetze "sollte" durch "muss". Füge am Ende eine Zusammenfassung hinzu: <em>"Bevor du antwortest, liste alle abgeschlossenen Schritte auf."</em></td>
<td><strong>Agent does not follow the workflow (e.g. skips typecheck)</strong><br>→ Open the <code>.agent.md</code> file and make the instruction stricter. Replace "should" with "must". Add a reminder at the end: <em>"Before responding, list all completed steps."</em></td>
</tr>
<tr>
<td><strong>Agent schreibt schlechten Next.js-Code (z. B. falsche API-Nutzung)</strong><br>→ Füge ein konkretes Beispiel in die <code>nextjs.instructions.md</code> ein. Copilot folgt Beispielen besser als abstrakten Regeln.</td>
<td><strong>Agent writes bad Next.js code (e.g. wrong API usage)</strong><br>→ Add a concrete code example to <code>nextjs.instructions.md</code>. Copilot follows examples better than abstract rules.</td>
</tr>
<tr>
<td><strong>Agent "vergisst" den Kontext nach langen Gesprächen</strong><br>→ Starte ein neues Chat-Fenster. Langer Kontext verdrängt Instructions. Übergib den Plan explizit: <em>"Hier ist der Plan: [Plan]. Bitte implementiere Schritt 3."</em></td>
<td><strong>Agent "forgets" context after long conversations</strong><br>→ Start a new chat window. Long context pushes out instructions. Pass the plan explicitly: <em>"Here is the plan: [plan]. Please implement step 3."</em></td>
</tr>
<tr>
<td><strong>Agent antwortet auf Englisch statt Deutsch (oder umgekehrt)</strong><br>→ Füge in <code>copilot-instructions.md</code> eine Sprachanweisung hinzu: <em>"Antworte immer auf Deutsch."</em> — oder sprich den Agent in der gewünschten Sprache an.</td>
<td><strong>Agent responds in German instead of English (or vice versa)</strong><br>→ Add a language instruction to <code>copilot-instructions.md</code>: <em>"Always respond in English."</em> — or address the agent in your preferred language.</td>
</tr>
<tr>
<td><strong>Agent überschreitet den Plan / macht ungebetene Änderungen</strong><br>→ Füge in der <code>.agent.md</code> unter "Rules" hinzu: <em>"Ändere nur Dateien, die explizit im Plan genannt sind. Keine ungebetenen Refactors."</em></td>
<td><strong>Agent exceeds the plan / makes unrequested changes</strong><br>→ Add to the <code>.agent.md</code> under "Rules": <em>"Only modify files explicitly listed in the plan. No unrequested refactoring."</em></td>
</tr>
</table>

---

## Referenzen / References

- [GitHub Copilot Customisation Docs](https://docs.github.com/en/copilot/customizing-copilot)
- [awesome-copilot](https://github.com/github/awesome-copilot) — Beispiele und Best Practices / Examples and best practices

## ./Anforderungsdokument_TreffPunkt_v1.0.md
# Anforderungsdokument TreffPunkt (Mini-Event-Manager für Gruppenorganisation)
## Softwareprojekt Welle 8

---

| | |
|---|---|
| **Projekt** | TreffPunkt. Mini-Event-Manager für Klassentreffen, Freundesgruppen und Ausflüge |
| **Unternehmen** | WAMOCON GmbH |
| **App Version** | 1 |
| **Erstellt von** | Daniel Moretz |
| **Eingereicht an** | Waleri Moretz (Geschäftsführung) |
| **Datum** | 06. Mai 2026 |
| **Vertraulichkeit** | Intern vertraulich |
| **Status** | Zur Freigabe eingereicht |

---

<p align="center">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 520 140" width="420" height="113" role="img" aria-label="TreffPunkt Logo">
  <defs>
    <linearGradient id="tpGrad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0%" stop-color="#2D6A4F"/>
      <stop offset="55%" stop-color="#40916C"/>
      <stop offset="100%" stop-color="#F4A261"/>
    </linearGradient>
  </defs>
  <!-- Stilisierte Gruppe (3 Kreise als Personen, verbunden) -->
  <g fill="url(#tpGrad)" opacity="0.85">
    <circle cx="50" cy="55" r="12"/>
    <circle cx="80" cy="45" r="12"/>
    <circle cx="110" cy="55" r="12"/>
  </g>
  <!-- Verbindungslinien zwischen Personen -->
  <g fill="none" stroke="url(#tpGrad)" stroke-width="2.5" stroke-linecap="round" opacity="0.5">
    <line x1="55" y1="65" x2="75" y2="57"/>
    <line x1="85" y1="57" x2="105" y2="65"/>
    <line x1="60" y1="67" x2="100" y2="67"/>
  </g>
  <!-- Pin / Treffpunkt-Marker -->
  <path d="M80 78 C 74 88 68 95 68 102 a12 12 0 0 0 24 0 c 0 -7 -6 -14 -12 -24 z" fill="#F4A261" opacity="0.9"/>
  <circle cx="80" cy="100" r="4" fill="#FFFFFF"/>
  <!-- Wortmarke -->
  <text x="150" y="85" font-family="'Nunito', 'Poppins', sans-serif" font-size="52" font-weight="700" letter-spacing="1" fill="#2D6A4F">Treff<tspan fill="#40916C">Punkt</tspan></text>
  <!-- Claim -->
  <text x="150" y="115" font-family="'Inter', Helvetica, Arial, sans-serif" font-size="11" letter-spacing="5" fill="#6B7F76">ZUSAMMEN&#160;&#160;PLANEN&#160;&#160;·&#160;&#160;ZUSAMMEN&#160;&#160;ERLEBEN</text>
</svg>
</p>

---

## 1. Zusammenfassung

### 1.1 Die Idee

**TreffPunkt** ist eine webbasierte Mini-Event-Management-App für private Gruppenorganisation im DACH-Raum mit klarem Fokus auf **informelle Treffen**, nicht auf professionelle Konferenzen oder Firmen-Events. Der Unterschied ist wesentlich: Eventbrite organisiert öffentliche Events mit Ticketing. TreffPunkt organisiert das Klassentreffen der 10b, den Wanderausflug der Sportgruppe, den JGA von Lisa oder das Familientreffen zum 70. Geburtstag von Oma.

Diese Unterscheidung zieht sich durch die gesamte Produktlogik: TreffPunkt kennt **Gruppen** mit Rollen (Organisator, Helfer, Teilnehmer), **Aufgaben** mit Verantwortlichen und Deadlines, **Terminabstimmungen** mit Voting-Logik, **Budgetplanung** mit automatischer Kostenaufteilung, **Abstimmungen** für Ort/Aktivität/Menü, **zentrale Info-Seiten** mit allen Details und **intelligente Erinnerungen**.

V1 liefert einen kompletten Gruppenorganisations-Workflow: Event erstellen → Teilnehmer einladen (Link, WhatsApp, E-Mail) → Termin abstimmen → Ort/Aktivität abstimmen → Aufgaben verteilen → Budget planen und aufteilen → Erinnerungen automatisieren → Event durchführen → Kosten abrechnen. V2 ergänzt KI: intelligente Vorschläge für Locations/Aktivitäten basierend auf Gruppengröße/Budget/Wetter, automatische Checklisten-Generierung, WhatsApp-Bot für Abstimmungen direkt im Chat, Foto-Sharing und Erinnerungsalbum nach dem Event, sowie gamifizierte Wiedersehens-Motivation.

### 1.2 Warum jetzt?

Drei Entwicklungen schaffen das Zeitfenster:

**Post-Pandemie-Nachholeffekt hält an:** Nach COVID-19 ist der Wunsch nach persönlichen Treffen messbar gestiegen. 68 % der 18–55-Jährigen in DACH geben an, mehr Wert auf persönliche Treffen zu legen als vor der Pandemie (Bitkom Digitalbarometer Freizeit 2026). Gleichzeitig ist die Organisationsfähigkeit gesunken, man hat verlernt, wie man ein Treffen für 20+ Personen koordiniert.

**WhatsApp-Gruppen stoßen an ihre Grenzen:** 85 % der Gruppenorganisation in DACH läuft über WhatsApp, aber die Unzufriedenheit ist hoch. 72 % der Befragten nennen „wichtige Infos gehen im Chat unter" als Hauptproblem. WhatsApp ist ein Kommunikationstool, kein Organisationstool. Die strukturellen Grenzen (keine Abstimmungen, keine Aufgabenverteilung, keine Budgetrechnung) werden bei größeren Gruppen (>10 Personen) zum Showstopper.

**Progressive Web Apps und WhatsApp-Bot-APIs machen App-Download überflüssig:** 2026 können PWAs Push-Benachrichtigungen auf iOS und Android senden. Gleichzeitig erlaubt die WhatsApp Business Platform Bot-Interaktionen. TreffPunkt kann Teilnehmer dort erreichen, wo sie bereits sind ohne App-Store-Download-Hürde.

---

## 2. Marktanalyse: Fokus DACH

### 2.1 Zielmarkt und Segmentierung

Der adressierbare Markt umfasst Organisierende privater und semi-privater Gruppenevents im DACH-Raum:

- **Klassentreffen:** 1,2–1,8 Mio. Events/Jahr (Schätzung basierend auf 44 Mio. Absolventen DACH, Ø alle 5–10 Jahre)
- **Geburtstagsfeiern (organisiert, >10 Personen):** 8–12 Mio./Jahr
- **Freundesgruppen-Treffen (geplant, >5 Personen):** 30–50 Mio./Jahr
- **JGA / Polterabend:** 350.000–400.000/Jahr (basierend auf 400.000 Hochzeiten DACH)
- **Familienfeiern (Jubiläen, Familientreffen):** 3–5 Mio./Jahr
- **Vereinsausflüge / Hobbygruppen:** 2–4 Mio./Jahr
- **Informelle Firmenevents (Teamausflug, Weihnachtsfeier ohne Event-Abteilung):** 1–2 Mio./Jahr

**Gesamtadressierbarer Markt:** rund 50–75 Millionen private Gruppenevents pro Jahr im DACH-Raum.

Quellen: Destatis Bevölkerungsstatistik 2025, Bitkom Digitalbarometer Freizeit 2026, Statista Events & Freizeit DACH 2026

### 2.2 Marktvolumen

Der globale Markt für Event-Management-Software liegt 2025 bei **14,5 Milliarden USD** mit einer CAGR von 11,2 % (Grand View Research 2026). Allerdings adressiert dieser Markt fast ausschließlich professionelle Events. Das Segment „Private/Informal Group Organization" ist statistisch kaum erfasst, da es bislang kein dediziertes Produkt gibt.

**Geschätztes Marktvolumen Privatgruppen-Organisation DACH:** 180–350 Mio. EUR (basierend auf 10–15 % der Events mit Zahlungsbereitschaft × 4,99–9,99 EUR/Event).

### 2.3 Das Kernproblem: WhatsApp ist kein Organisationstool

WhatsApp ist der De-facto-Standard für Gruppen-Kommunikation, aber strukturell ungeeignet für Gruppenorganisation. Der Unterschied:

**Kommunikation ≠ Organisation.** Kommunikation ist der Austausch von Nachrichten. Organisation erfordert Struktur: Termine, Aufgaben, Zuständigkeiten, Budgets, Abstimmungen, Übersichten.

Fünf konkrete Probleme mit WhatsApp als Organisationstool:

**Kein Überblick:** Nach 200 Nachrichten in der Gruppe weiß niemand mehr, wann und wo das Treffen stattfindet. Es gibt kein Dashboard, keine Zusammenfassung, keinen Status.

**Keine echte Abstimmung:** Umfragen in WhatsApp sind rudimentär (max. 12 Optionen, keine Gewichtung, kein „Geht auch, aber lieber nicht"). Doodle löst Termine, aber nicht Ort/Aktivität/Menü.

**Keine Aufgabenverteilung:** „Wer bringt den Grill mit?", 3 Leute sagen ja, 0 bringen ihn mit. Keine Verbindlichkeit, keine Deadlines, kein Tracking.

**Kein Budget:** „Die Location kostet 500 EUR, jeder zahlt 25 EUR", aber wer hat gezahlt? Wer schuldet wem? Splid kann Kosten teilen, aber ist nicht mit dem Event-Kontext verknüpft.

**Kein Teilnehmer-Überblick:** Wer kommt? Wer hat zugesagt? Wer hat abgesagt? Wer hat noch nicht geantwortet? In WhatsApp muss man Nachrichten durchscrollen in TreffPunkt gibt es eine klare Teilnehmerliste mit Status.

### 2.4 Regulatorische Rahmenbedingungen

**DSGVO:** Da private Kontaktdaten (E-Mail, Telefonnummer, Name) verarbeitet werden, gelten Art. 6 und Art. 7 DSGVO. Einwilligung bei Teilnahme, Recht auf Löschung, EU-Hosting Pflicht.

**Zahlungsdiensteregulierung (PSD2):** Die integrierte Kostenaufteilung darf kein Zahlungsdienst im Sinne der PSD2 sein. Lösung: Abrechnung wird nur als Übersicht dargestellt (wer schuldet wem wie viel), tatsächliche Zahlungen laufen über PayPal/Stripe-Links oder Banküberweisung. TreffPunkt ist kein Zahlungsabwickler.

**Minderjährige:** Klassentreffen können Teilnehmer <16 Jahre umfassen. Art. 8 DSGVO erfordert Einwilligung des Erziehungsberechtigten für Unter-16-Jährige. Lösung: Altersprüfung bei Kontoerstellung, Teilnahme ohne Konto per Link möglich (dann gelten nur minimale Daten).

---

## 3. Wettbewerb

### 3.1 Direkte und indirekte Wettbewerber

| Anbieter | Kategorie | Stärke | Schwäche und Chance für TreffPunkt |
|---|---|---|---|
| **WhatsApp-Gruppe** | Kommunikation | Universell verbreitet, null Einstiegshürde | Keine Struktur, keine Aufgaben, kein Budget, kein Überblick |
| **Doodle** (CH) | Terminabstimmung | Etabliert, einfach | Nur Termine, keine Aufgaben/Budget/Rollen, Werbung, veraltete UX |
| **Splid** (DE) | Kostenteilen | Exzellentes Kostenteilen | Nur Finanzen, kein Event-Kontext, keine Termine/Aufgaben |
| **Eventbrite** (US) | Event-Ticketing | Professionell, Reichweite | Für öffentliche Events, nicht für private Gruppen, US-Hosting |
| **Google Forms** | Umfragen | Flexibel, kostenlos | Kein Event-Kontext, manuell, technische Hürde |
| **SignUpGenius** (US) | Aufgabenverteilung | Fokus auf Freiwilligen-Koordination | US-fokussiert, keine DSGVO, kein Budget/Termin |
| **Rallly** (Open Source) | Terminabstimmung | Open Source, Doodle-Alternative | Nur Termine, Minimal-Features |
| **Notion / Trello** | Projektmanagement | Sehr flexibel | Zu komplex, nicht Event-spezifisch, Onboarding-Hürde |
| **Partify** (DE, klein) | Party-Planung | Fokus auf private Events | Sehr klein, nur Partys, begrenzte Features |

**Marktlücke:** Kein Wettbewerber im DACH-Raum kombiniert **Terminabstimmung**, **Aufgabenverteilung mit Rollenkonzept**, **Budgetplanung und Kostenaufteilung**, **Ort-/Aktivitätsabstimmung**, **zentrale Event-Übersicht**, **automatische Erinnerungen** und **DSGVO-konformes EU-Hosting** in einem einzigen, für Laien optimierten Produkt.

### 3.2 Wettbewerbsmatrix

| Feature | WhatsApp | Doodle | Splid | Eventbrite | **TreffPunkt** |
|---|---|---|---|---|---|
| Terminabstimmung | ❌ | ✅ | ❌ | ❌ | ✅ |
| Ort-/Aktivitäts-Voting | ❌ | ❌ | ❌ | ❌ | ✅ |
| Aufgabenverteilung | ❌ | ❌ | ❌ | ❌ | ✅ |
| Rollenkonzept | ❌ | ❌ | ❌ | ❌ | ✅ |
| Budgetplanung | ❌ | ❌ | ✅ | ❌ | ✅ |
| Kostenaufteilung | ❌ | ❌ | ✅ | ❌ | ✅ |
| Event-Übersichtsseite | ❌ | ❌ | ❌ | ✅ | ✅ |
| Erinnerungen | ❌ | ✅ | ❌ | ✅ | ✅ |
| Teilnehmer-Management | ❌ | ❌ | ❌ | ✅ | ✅ |
| Kein Account nötig (Teilnehmer) | ✅ | ✅ | ❌ | ❌ | ✅ |
| DSGVO / EU-Hosting | ❌ | ✅ | ✅ | ❌ | ✅ |
| Kostenlos nutzbar | ✅ | ⚠️ | ✅ | ⚠️ | ✅ |

---

## 4. Zielgruppe

### 4.1 Primäre Zielgruppe

**Privatpersonen, die informelle Gruppenevents mit 5 bis 50 Teilnehmern organisieren**, im DACH-Raum, 20–65 Jahre, technisch durchschnittlich bis leicht überdurchschnittlich versiert.

Vier Nutzerprofile:

**Sarah, 34, Klassentrefferin:** War auf dem Abi-Jahrgangstreffen der Klasse von 2010, hat spontan gesagt „Ich organisiere das nächste!" und bereut es seitdem. 28 Leute, 5 Terminvorschläge, 3 Wochen Diskussion über die Location, niemand übernimmt Verantwortung. Will ein Tool, das ihr die Arbeit abnimmt und den Überblick gibt.

**Max, 29, JGA-Planer:** Plant den Junggesellenabschied seines besten Freundes. 12 Teilnehmer, Budget pro Person, Überraschungsprogramm, Aufgabenverteilung (wer bucht Hotel, wer organisiert Aktivität, wer kauft T-Shirts). Alles geheim vor dem Bräutigam. Braucht ein geschütztes Planungs-Tool.

**Familie Müller, 55–65, Familienfest-Organisatoren:** 70. Geburtstag von Oma, 45 Familienmitglieder, 3 Generationen. Braucht Terminabstimmung, Aufgabenverteilung (wer bringt Kuchen, wer dekoriert, wer organisiert Musik), Budgetplanung und eine zentrale Info-Seite mit Adresse, Uhrzeit, Programm.

**Tim, 42, Wandergruppen-Leiter:** Organisiert monatlich einen Wanderausflug für 8–15 Personen. Braucht schnelle Terminabstimmung, Treffpunkt-Kommunikation, Zu-/Absagen-Übersicht, Fahrgemeinschafts-Koordination.

### 4.2 Sekundäre Zielgruppe

**Kleine Vereine (Sportverein, Chor, Schachclub):** Vereinsausflüge und Feiern, 10–50 Personen. Teilweise Überschneidung mit VereinsPilot. TreffPunkt fokussiert auf das einzelne Event, nicht auf die Vereinsverwaltung.

**Informelle Firmenteams:** Teamausflüge und Weihnachtsfeiern ohne dedizierte Event-Abteilung. Budget kommt von der Firma, aber Organisation liegt bei einer Person im Team.

### 4.3 Nicht Zielgruppe

Professionelle Event-Planer, Konferenz-Veranstalter (>100 Personen), Hochzeitsplanung (eigener Markt), Firmen mit Event-Abteilung, öffentliche Veranstaltungen mit Ticketing.

---

## 5. Nutzen

### 5.1 Nutzen für den Organizer

| Problem heute | Lösung durch TreffPunkt | Konkreter Vorteil |
|---|---|---|
| Organisator trägt gesamte Last alleine | Rollenkonzept mit Helfer-Zuweisung, Aufgabenverteilung | Organisationsaufwand auf mehrere Schultern verteilt |
| Terminfindung dauert Wochen | Integrierte Terminabstimmung mit Deadline und Auto-Entscheidung | Termin steht in 3 Tagen statt 3 Wochen |
| „Wo treffen wir uns?" → endlose Diskussion | Ort-Voting mit Bildern, Karte und Beschreibung | Entscheidung in 48h durch Abstimmung |
| Budgetplanung auf Zettelwirtschaft | Budget-Tool mit automatischer Pro-Kopf-Berechnung | Transparenz, kein Streit über Geld |
| „Wer bringt was mit?" → 3 sagen ja, 0 machen es | Aufgabenliste mit Verantwortlichem, Deadline und Status | Verbindlichkeit durch Sichtbarkeit |
| Informationen gehen im Chat unter | Zentrale Event-Seite mit allen Infos auf einen Blick | Kein Scrollen durch 200 Nachrichten |
| Teilnehmerstatus unklar | Übersichtliche Zu-/Absagen-Liste mit Reminder für Nicht-Antwortende | Planungssicherheit |
| Erinnerungen manuell versenden | Automatische Erinnerungen vor Abstimmungs-Deadline und Event-Termin | Weniger Aufwand, höhere Teilnahme |

### 5.2 Nutzen für Teilnehmer

| Problem heute | Lösung durch TreffPunkt | Konkreter Vorteil |
|---|---|---|
| Muss 200 WhatsApp-Nachrichten lesen | Alles auf einer Seite: Termin, Ort, Programm, Aufgaben, Budget | 30 Sekunden statt 15 Minuten |
| Weiß nicht, was ich mitbringen soll | Klare Aufgabenzuweisung mit Beschreibung | Keine Unsicherheit |
| Termin im Kalender vergessen | Automatischer Kalendereintrag (Google/Apple/Outlook) + Reminder | Kein Vergessen |
| Kosten unklar | Transparente Aufstellung: was kostet es, wer zahlt was | Faire Aufteilung |

### 5.3 Nutzen für die WAMOCON GmbH

**Virale Verbreitung:** Jeder Teilnehmer ist ein potenzieller neuer Organizer. Bei Ø 15 Teilnehmern pro Event und 3 % Conversion sind das 0,45 neue Organizer pro Event, exponentielles Wachstumspotenzial.

**Hohe emotionale Bindung:** Menschen erinnern sich an schöne Treffen. TreffPunkt wird mit positiven Erlebnissen assoziiert, starke Marke.

**Cross-Selling-Potenzial:** Location-Empfehlungen, Catering-Partner, Aktivitäts-Anbieter, ab V2 sind Affiliate-Provisionen eine attraktive Einnahmequelle.

**Synergien im Portfolio:** TreffPunkt ergänzt VereinsPilot (Vereinsverwaltung) um die Event-Dimension und KursPilot um die Gruppen-Koordination.

---

## 6. Abhängigkeiten und Machbarkeit

### 6.1 Technische Services

| Service | Funktion | Abhängigkeit | Kosten |
|---|---|---|---|
| **Supabase EU (Frankfurt)** | Datenbank, Auth, Realtime, Storage | DPA | Ab 25 USD/Monat |
| **Vercel fra1** | Hosting | Kein Exklusiv | Ab 20 USD/Monat |
| **Resend / Brevo (EU)** | Transaktions-E-Mails (Einladungen, Reminder) | Kein Exklusiv | Ab 0 EUR |
| **Google Calendar API** | Kalendereintrag nach Terminentscheidung | OAuth, kein Exklusiv | Kostenfrei |
| **Google Maps / OpenStreetMap API** | Karten-Einbettung für Treffpunkt | Kein Exklusiv | Kontingent-basiert |
| **WhatsApp Business API (V2)** | Bot-Integration für Abstimmungen | DSGVO-konformer BSP | Ab 0,04 EUR/Konversation |
| **Stripe** | Premium-Zahlungen, Event-Upgrade | Zertifiziert | +1,4 % + 0,25 EUR/Tx |
| **Plausible (EU)** | Analytics, cookiefrei | DSGVO-konform | Ab 9 EUR/Monat |

### 6.2 Besondere Überlegung: Zahlungsabwicklung

TreffPunkt ist **kein Zahlungsdienst**. Die Budgetaufteilung zeigt nur an, wer wem wie viel schuldet. Die tatsächliche Zahlung läuft über:
- PayPal.me-Links (automatisch generiert)
- Banküberweisung (IBAN wird angezeigt)
- Vor-Ort-Bar-Zahlung (markierbar)

Damit umgeht TreffPunkt die PSD2-Regulierung und benötigt keine Zahlungsdienste-Lizenz.

### 6.3 Gesamtbewertung

Version 1 kann ohne Partnervertrag oder Behördengenehmigung starten. Alle technischen Bausteine sind öffentlich zugänglich und DSGVO-konform nutzbar. Die größte Herausforderung liegt nicht in der Technik, sondern in der viralen Verbreitung und dem Onboarding von technisch weniger versierten Teilnehmern. Daher der konsequente PWA-Ansatz ohne App-Download-Pflicht.

---

## 7. Anforderungen Version 1

### 7.1 Hauptprozesse

#### 7.1.1 Event erstellen und verwalten

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| EV-01 | Event erstellen mit Titel, Beschreibung, Datum (fest oder offen), Ort (fest oder offen) | Muss | Neu |
| EV-02 | Event-Typen: Klassentreffen, Geburtstag, Ausflug, JGA, Familienfeier, Vereinsausflug, Sonstiges | Muss | Neu |
| EV-03 | Zentrale Event-Seite mit allen Informationen auf einen Blick (Countdown, Termin, Ort, Teilnehmer, Aufgaben, Budget) | Muss | Neu |
| EV-04 | Event-Bild/Header-Foto hochladbar | Soll | Neu |
| EV-05 | Event-Link zum Teilen (ohne Login nutzbar für Teilnehmer) | Muss | Neu |
| EV-06 | Event duplizieren (für wiederkehrende Treffen) | Soll | Neu |
| EV-07 | Event archivieren nach Durchführung | Muss | Neu |

#### 7.1.2 Teilnehmer-Management

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| TN-01 | Teilnehmer einladen per Link, E-Mail, WhatsApp-Share | Muss | Neu |
| TN-02 | Teilnehmer können ohne Account teilnehmen (Name + E-Mail oder nur Name reicht) | Muss | Neu |
| TN-03 | Zu-/Absage mit optionalem Kommentar | Muss | Neu |
| TN-04 | Status: Zugesagt / Abgesagt / Vielleicht / Keine Antwort | Muss | Neu |
| TN-05 | +1 / Begleitperson angeben können | Soll | Neu |
| TN-06 | Warteliste bei begrenzter Teilnehmerzahl | Soll | Neu |
| TN-07 | Automatischer Reminder an Nicht-Antwortende (nach konfigurierbarer Frist) | Muss | Neu |
| TN-08 | Teilnehmerliste mit Kontaktinfo nur für Organizer sichtbar | Muss | Neu |

#### 7.1.3 Rollen und Verantwortungen

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| RL-01 | Rollen: Organisator (Ersteller), Co-Organisator, Helfer, Teilnehmer | Muss | Neu |
| RL-02 | Organisator kann Co-Organisatoren ernennen (volle Bearbeitungsrechte) | Muss | Neu |
| RL-03 | Helfer haben eingeschränkte Rechte (eigene Aufgaben verwalten, Teilnehmer sehen) | Soll | Neu |
| RL-04 | Teilnehmer können nur abstimmen, zu-/absagen, eigene Aufgaben sehen | Muss | Neu |
| RL-05 | Organisator kann Rollen jederzeit ändern | Muss | Neu |

#### 7.1.4 Terminabstimmung

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| TA-01 | Terminvorschläge mit Datum und optionaler Uhrzeit | Muss | Neu |
| TA-02 | Voting: Ja / Nein / Wenn es sein muss (3-stufig, wie Doodle) | Muss | Neu |
| TA-03 | Teilnehmer können eigene Terminvorschläge hinzufügen (konfigurierbar) | Soll | Neu |
| TA-04 | Abstimmungs-Deadline mit automatischer Erinnerung | Muss | Neu |
| TA-05 | Automatischer Vorschlag des besten Termins (meiste Ja-Stimmen) | Muss | Neu |
| TA-06 | Organizer bestätigt finalen Termin → automatische Benachrichtigung aller | Muss | Neu |
| TA-07 | Automatischer Kalendereintrag (Google Calendar, Apple Calendar, Outlook, .ics-Download) | Muss | Neu |
| TA-08 | Optionale Wiederholung (monatlich, quartalsweise) für regelmäßige Treffen | Kann | Neu |

#### 7.1.5 Ort- und Aktivitätsabstimmung

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| OA-01 | Ort-/Aktivitäts-Vorschläge mit Titel, Beschreibung, Link, Bild | Muss | Neu |
| OA-02 | Kartenansicht für Ortsvorschläge (Google Maps / OpenStreetMap Embed) | Soll | Neu |
| OA-03 | Voting auf Vorschläge (Daumen hoch / Daumen runter oder Rangliste) | Muss | Neu |
| OA-04 | Jeder Teilnehmer kann Vorschläge hinzufügen | Muss | Neu |
| OA-05 | Organizer bestätigt finalen Ort/Aktivität → Benachrichtigung | Muss | Neu |
| OA-06 | Mehrere Abstimmungen pro Event möglich (z. B. Ort + Restaurant + Aktivität) | Soll | Neu |

#### 7.1.6 Aufgabenverteilung

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| AV-01 | Aufgaben erstellen mit Titel, Beschreibung, Deadline, optionalem Verantwortlichen | Muss | Neu |
| AV-02 | Aufgaben zuweisen oder „wer will?" (Freiwilligen-Modus) | Muss | Neu |
| AV-03 | Aufgabenstatus: Offen / In Bearbeitung / Erledigt | Muss | Neu |
| AV-04 | Checklisten innerhalb einer Aufgabe (z. B. Einkaufsliste) | Soll | Neu |
| AV-05 | Erinnerung bei überfälliger Aufgabe | Muss | Neu |
| AV-06 | Vorlagen-Checklisten je Event-Typ (z. B. „Grillabend": Grill, Kohle, Getränke, Salate, Geschirr, ...) | Soll | Neu |
| AV-07 | Aufgaben-Kommentare (kurze Rückfragen, z. B. „Reichen 3 Kisten Bier?") | Soll | Neu |

#### 7.1.7 Budgetplanung und Kostenaufteilung

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| BU-01 | Budget-Gesamtrahmen für Event festlegen | Muss | Neu |
| BU-02 | Einzelposten anlegen (z. B. Location 500 EUR, Catering 300 EUR, Deko 50 EUR) | Muss | Neu |
| BU-03 | Automatische Pro-Kopf-Berechnung (Gesamtbudget / Teilnehmer) | Muss | Neu |
| BU-04 | Unterschiedliche Beiträge pro Person möglich (z. B. Kinder halber Preis) | Soll | Neu |
| BU-05 | „Wer hat gezahlt?"-Tracking (Vorlage-Erfassung) | Muss | Neu |
| BU-06 | Automatische Abrechnung: Wer schuldet wem wie viel (minimale Transaktionen) | Muss | Neu |
| BU-07 | Export als PDF/Screenshot für Abrechnung | Soll | Neu |
| BU-08 | PayPal.me-Link oder IBAN des Empfängers hinterlegen | Soll | Neu |
| BU-09 | Zahlungsstatus markierbar (bezahlt / offen) | Muss | Neu |

#### 7.1.8 Benachrichtigungen und Erinnerungen

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| BE-01 | E-Mail-Benachrichtigung bei Einladung | Muss | Neu |
| BE-02 | Push-Benachrichtigung (PWA) bei Änderungen am Event | Muss | Neu |
| BE-03 | Erinnerung vor Abstimmungs-Deadline (konfigurierbar) | Muss | Neu |
| BE-04 | Erinnerung 1 Woche / 1 Tag / 2h vor Event | Muss | Neu |
| BE-05 | Zusammenfassung „Dein Event in Kürze" per E-Mail am Vortag | Soll | Neu |
| BE-06 | Opt-out für einzelne Benachrichtigungstypen | Muss | Neu |

### 7.2 Basisfunktionalitäten

| ID | Anforderung | Priorität | Status |
|---|---|---|---|
| BA-01 | Progressive Web App (PWA), kein App-Store-Download erforderlich | Muss | Neu |
| BA-02 | Responsive, Mobile-First-Design | Muss | Neu |
| BA-03 | Teilnehmer-Zugang ohne Account (per Link + Name) | Muss | Neu |
| BA-04 | Organizer-Account mit E-Mail oder Social Login (Google/Apple) | Muss | Neu |
| BA-05 | EU-Hosting (Supabase Frankfurt, Vercel fra1) | Muss | Neu |
| BA-06 | DSGVO-konform: Einwilligung, Datenlöschung, Datensparsamkeit | Muss | Neu |
| BA-07 | Ladezeit < 2s auf 3G-Verbindung | Muss | Neu |
| BA-08 | Mehrsprachig: Deutsch, Englisch | Muss | Neu |
| BA-09 | AGB, Impressum, Datenschutzerklärung | Muss | Neu |
| BA-10 | Dark Mode | Kann | Neu |

### 7.3 Preismodell

| Tier | Preis | Inhalt |
|---|---|---|
| **Free** | 0 EUR | 3 aktive Events, 15 Teilnehmer pro Event, alle Kernfeatures, TreffPunkt-Branding |
| **Plus** | 4,99 EUR/Monat oder 2,99 EUR/Event | Unbegrenzte Events, 50 Teilnehmer, Vorlagen-Checklisten, kein Branding, Event-Bild-Upload |
| **Pro** | 9,99 EUR/Monat | Unbegrenzte Events, 200 Teilnehmer, Priority-E-Mail-Reminder, Export-Funktionen, benutzerdefinierte Abstimmungen, API-Zugang |

### 7.4 Scope: Was ist Version 1 und was nicht

| In Scope Version 1 | Out of Scope, ab V2 |
|---|---|
| Event erstellen und verwalten | WhatsApp-Bot-Integration |
| Teilnehmer einladen und verwalten | KI-Vorschläge für Locations/Aktivitäten |
| Terminabstimmung (Doodle-artig) | Automatische Checklisten-Generierung per KI |
| Ort-/Aktivitätsabstimmung | Foto-Sharing und Erinnerungsalbum |
| Aufgabenverteilung mit Status | Gamifizierte Wiedersehens-Motivation |
| Budgetplanung und Kostenaufteilung | Fahrgemeinschafts-Koordination |
| Automatische Erinnerungen | In-App-Chat (Kommentar-System reicht in V1) |
| Kalendereintrag (Google/Apple/Outlook) | Wetter-Integration |
| PWA mit Push-Benachrichtigungen | Native Mobile-App |
| EU-Hosting, DSGVO | Location-Affiliate-Empfehlungen |

---

## 8. Anforderungen Version 2 (KI-Erweiterung)

| ID | Anforderung | Priorität | Nutzen |
|---|---|---|---|
| KI-01 | **KI-Locations-Vorschlag:** Basierend auf Gruppengröße, Budget, Ort und Vorlieben automatische Location-Empfehlungen | Muss | Organisator muss nicht selbst recherchieren |
| KI-02 | **Automatische Checkliste:** KI generiert Event-spezifische To-Do-Liste basierend auf Event-Typ und Teilnehmerzahl | Muss | 70 % weniger manuelle Planung |
| KI-03 | **WhatsApp-Bot:** Abstimmungen und Updates direkt in WhatsApp. Teilnehmer müssen TreffPunkt nicht öffnen | Muss | Höhere Beteiligung, keine App-Hürde |
| KI-04 | **Smart Scheduling:** KI analysiert Antwortmuster und schlägt optimalen Termin vor, der die meisten Teilnehmer berücksichtigt | Soll | Schnellere Terminentscheidung |
| KI-05 | **Foto-Album:** Nach dem Event können Teilnehmer Fotos hochladen → automatisch geteiltes Album | Soll | Erinnerungswert, virale Verbreitung |
| KI-06 | **Wetter-Integration:** Wettervorhersage für den Event-Tag und -Ort auf der Event-Seite | Soll | Bessere Planung bei Outdoor-Events |
| KI-07 | **Fahrgemeinschaften:** Teilnehmer geben Start-Ort ein → automatische Fahrgemeinschafts-Vorschläge | Kann | Weniger Autos, geringere Kosten |
| KI-08 | **Gamification:** Punkte und Badges für zuverlässige Teilnehmer, schnelle Antworten, erledigte Aufgaben | Soll | Höhere Beteiligung und Verbindlichkeit |
| KI-09 | **Einladungstext-Generator:** KI erstellt personalisierten Einladungstext basierend auf Event-Typ und Tonalität | Soll | Professionelle Einladung in 10 Sekunden |
| KI-10 | **Wiedersehens-Reminder:** „Euer letztes Klassentreffen war vor 4 Jahren. Zeit für ein neues?" mit 1-Klick-Event-Erstellung | Soll | Wiederkehrende Nutzung |

---

## 9. Drei Alternativkonzepte, kritisch hinterfragt

### 9.1 Alternative A: GruppenPuls, reiner WhatsApp-Bot ohne eigene App

**Kernidee:** Statt eigener Web-App wird die gesamte Gruppenorganisation als WhatsApp-Bot abgebildet. Der Organizer fügt den Bot zur bestehenden WhatsApp-Gruppe hinzu. Der Bot übernimmt Terminabstimmung, Aufgabenverteilung und Kostenteilung direkt im Chat.

**Vorteile gegenüber TreffPunkt:**
- **Null Einstiegshürde:** Kein neues Tool, keine neue URL, kein Account, alles dort, wo die Gruppe bereits ist.
- **Sofortige Adoption:** WhatsApp hat 62 Mio. Nutzer in DACH. Keine Überzeugungsarbeit.
- **Geringere Entwicklungskosten:** Kein Frontend, nur Bot-Logik und Backend.

**Nachteile und kritische Bewertung:**
- **Strukturelle Limitierung:** WhatsApp-Bots haben eingeschränkte UI, keine Karten, keine Drag-and-Drop, keine visuellen Übersichten. Komplexe Budgets oder Aufgabenlisten sind im Chat-Format schlecht darstellbar.
- **Plattformabhängigkeit:** 100 % abhängig von Meta/WhatsApp. API-Änderungen, Preiserhöhungen oder Policy-Änderungen können das Geschäft über Nacht zerstören.
- **Datenschutz-Bedenken:** Alle Gruppendaten laufen über WhatsApp-Server. DSGVO-Konformität ist komplex und von Meta abhängig.
- **Monetarisierung schwierig:** In-Chat-Bezahlung ist ungewöhnlich und erzeugt Friction.
- **Keine Markenbildung:** Der Bot ist unsichtbar. TreffPunkt baut keine eigene Marke auf.

**Fazit:** GruppenPuls ist ein starker Distributionskanal, aber kein eigenständiges Produkt. → **Empfehlung: Als V2-Feature von TreffPunkt integrieren (KI-03), nicht als eigenständige Alternative.**

### 9.2 Alternative B: EventBoard, physisches + digitales Hybridboard für analoge Gruppen

**Kernidee:** Ein physisches „Smart Poster" (QR-Code + NFC-Tag) wird an einem zentralen Ort aufgehängt (Schule, Vereinsheim, Büro). Teilnehmer scannen den Code und kommen auf eine minimalistische Event-Seite mit Zu-/Absage und Terminabstimmung. Für Gruppen, in denen nicht alle digital affin sind.

**Vorteile gegenüber TreffPunkt:**
- **Inklusiv für alle Altersgruppen:** Auch 75-jährige Oma kann QR-Code scannen und auf „Ja, ich komme" drücken.
- **Physische Präsenz:** Ein Poster an der Pinnwand erinnert permanent ans Event, höhere Sichtbarkeit als ein Link.
- **Neuartig und medienwirksam:** „Das smarte Event-Poster" hat PR-Potenzial.

**Nachteile und kritische Bewertung:**
- **Produktion und Logistik:** Physische Produkte (Poster, NFC-Tags) erfordern Produktion, Versand, Lagerhaltung. Fundamental anderes Geschäftsmodell als rein digitales SaaS.
- **Reichweite limitiert:** Nur sinnvoll, wenn die Gruppe einen physischen Treffpunkt hat. Für verteilte Gruppen (Klassentreffen von Leuten, die in verschiedenen Städten wohnen) nutzlos.
- **Funktional eingeschränkt:** QR-Code-Seite muss extrem einfach sein. Aufgabenverteilung und Budgetplanung sind zu komplex für dieses Format.
- **Skalierung schwierig:** Jedes Poster ist ein Einmalprodukt. Keine virale Verbreitung.

**Fazit:** EventBoard ist ein Nischenprodukt für analoge Zielgruppen. → **Empfehlung: Nicht verfolgen. TreffPunkt kann durch barrierefreies Design (große Buttons, einfache Sprache) dieselbe Zielgruppe digital bedienen.**

### 9.3 Alternative C: ReunionHub, spezialisierte Plattform nur für Klassentreffen und Alumni

**Kernidee:** Statt generischer Gruppenevents wird ausschließlich auf Klassentreffen und Alumni-Events fokussiert. ReunionHub hilft, ehemalige Mitschüler zu finden, die Gruppe zu reaktivieren, das Treffen zu organisieren und danach den Kontakt zu halten.

**Vorteile gegenüber TreffPunkt:**
- **Klare Positionierung:** „Die App für Klassentreffen" ist leichter zu vermarkten als „Die App für alle Gruppenevents".
- **Emotionaler Hook:** Nostalgie und Wiedersehen sind starke emotionale Trigger, hohes virales Potenzial.
- **Alumni-Suche als Alleinstellungsmerkmal:** „Finde deine alte Klasse" ist ein Feature, das TreffPunkt nicht hat.
- **Stabile Wiederkehr:** Klassentreffen wiederholen sich alle 5–10 Jahre → langfristige Nutzerbindung.

**Nachteile und kritische Bewertung:**
- **Extrem enge Nische:** Nur Klassentreffen limitiert die Nutzungsfrequenz massiv. 1x in 5–10 Jahren pro Nutzer → schwer zu monetarisieren.
- **Alumni-Suche datenschutzrechtlich heikel:** „Finde deine alten Mitschüler" erfordert entweder eigene Datenbank (teuer, Datenschutz-Albtraum) oder Social-Media-Scraping (illegal).
- **StayFriends-Problem:** StayFriends (ehemals große Alumni-Plattform in DACH) ist gescheitert, der Markt hat gezeigt, dass reine Alumni-Plattformen schwer zu monetarisieren sind.
- **Saisonale Nachfrage:** Klassentreffen häufen sich im Sommer und Herbst, starke Saisonalität erschwert gleichmäßige Nutzung.

**Fazit:** ReunionHub hat einen emotional starken Kern, aber das Geschäftsmodell funktioniert nicht als eigenständige Plattform. → **Empfehlung: „Klassentreffen" als prominenten Event-Typ in TreffPunkt integrieren, mit speziellem Template und optionaler Mitschüler-Einladungsfunktion (Social-Share-basiert, nicht Datenbank-basiert).**

---

## 10. Chancen und Risiken

### 10.1 Chancen

| Chance | Begründung |
|---|---|
| Virale Verbreitung durch Gruppeneinladungen | Jeder Teilnehmer ist potenzieller neuer Organizer |
| Emotionaler Anwendungsfall | Menschen freuen sich auf Treffen, positive Markenassoziation |
| WhatsApp-Bot als Zero-Friction-Kanal (V2) | Dort abholen, wo die Leute sind |
| Affiliate-Revenue durch Location-Empfehlungen | Organizer suchen Locations. TreffPunkt kann vermitteln |
| Cross-Selling im WAMOCON-Portfolio | Synergien mit VereinsPilot und KursPilot |
| KI-Automatisierung der Eventplanung | Checklisten, Einladungstexte, Location-Vorschläge per KI |

### 10.2 Risiken

| Risiko | Gegenmaßnahme |
|---|---|
| WhatsApp/Meta integriert ähnliche Features | WhatsApp ist Kommunikation, TreffPunkt ist Organisation, verschiedene Schichten. Bot-Integration macht TreffPunkt zum Add-on. |
| Doodle expandiert in gleiche Richtung | Doodle ist seit 15 Jahren nur Termine. Pivot in Gesamtorganisation unwahrscheinlich. Trotzdem: schnell am Markt sein. |
| Geringe Zahlungsbereitschaft bei privaten Nutzern | Freemium-Modell mit großzügigem Free-Tier. Premium muss klar Mehrwert liefern. |
| Sporadische Nutzung erschwert Engagement | Wiedersehens-Reminder (V2), wiederkehrende Events, Gamification halten Nutzer aktiv. |
| Heterogene Zielgruppe (jung bis alt) | Zero-Friction-Onboarding, keine Pflicht-App, große Buttons, einfache Sprache. |
| DSGVO-Risiko bei privaten Kontaktdaten | Minimale Datenerfassung, kein Account für Teilnehmer nötig, klare Löschfristen. |

---

## 11. Umsetzungsplan Version 1

### 11.1 Technologiestack

- **Frontend:** Next.js 15 (App Router), Tailwind CSS, shadcn/ui, TypeScript, PWA-Manifest
- **Backend:** Supabase EU Frankfurt (PostgreSQL, RLS, Auth, Realtime Subscriptions, Storage)
- **E-Mail:** Resend (EU)
- **Karten:** Google Maps Embed API oder OpenStreetMap + Leaflet
- **Kalender:** .ics-Generierung + Google Calendar API
- **Payment (Premium):** Stripe
- **Analytics:** Plausible (EU, cookiefrei)
- **Hosting:** Vercel fra1

### 11.2 Umsetzungsplan 5 Werktage

| Tag | Fokus | Inhalt |
|---|---|---|
| Tag 1 | Anforderungen und Architektur | Datenmodell (Events, Teilnehmer, Abstimmungen, Aufgaben, Budget-Posten, Rollen), RLS-Policies, UI-Wireframes, PWA-Setup |
| Tag 2 | Fundament und Event-Flow | Auth (Social Login für Organizer, Link-Zugang für Teilnehmer), Event-Erstellung, Event-Seite, Einladungs-Sharing |
| Tag 3 | Abstimmungen und Aufgaben | Terminabstimmung (Voting-Logik, Deadline, Auto-Vorschlag), Ort-Voting, Aufgaben-CRUD, Freiwilligen-Modus |
| Tag 4 | Budget und Benachrichtigungen | Budget-Tool (Posten, Pro-Kopf, Abrechnung), E-Mail-Benachrichtigungen, Reminder-Cron, Kalendereintrag-Export |
| Tag 5 | QA und Launch | Manuelles Testen aller Flows, PWA-Manifest, Plausible, AGB/Datenschutz, Stripe für Premium, direkter Launch |

---

## 12. Marke, Branding und Marketing

### 12.1 Markenname und Bedeutung

**TreffPunkt** vereint drei Kernideen:

- **Treff(en):** Das Produkt dreht sich um persönliche Treffen. Klassentreffen, Freundestreffen, Familienfeiern. Das Wort „Treffen" ist emotional aufgeladen: Vorfreude, Wiedersehen, Gemeinschaft.
- **Punkt:** Präzision und Klarheit. TreffPunkt bringt Struktur in das Chaos der Gruppenorganisation. Punkt. Kein Chaos mehr.
- **Treffpunkt (als Wort):** Der Ort, an dem man sich trifft. TreffPunkt ist sowohl der digitale Ort der Organisation als auch der Wegweiser zum physischen Treffpunkt.

Der CamelCase-Schreibweise „TreffPunkt" (statt „Treffpunkt") gibt dem Namen eine moderne, app-artige Anmutung und macht ihn als Marke unterscheidbar vom Alltagswort.

Der Name ist kurz (10 Buchstaben), deutsch, sofort verständlich, .de-/.app-Domainfähig und emotional positiv besetzt. Vor Markenanmeldung: DPMA-/EUIPO-Recherche durchführen.

### 12.2 Kleine Markt- und Positionierungsanalyse

| Markenarchetyp im Wettbewerb | Vertreter | Wirkung | Lücke |
|---|---|---|---|
| **Funktional/Utility** | Doodle, Google Forms | Nützlich, aber kalt und generisch | Keine emotionale Verbindung |
| **Finanz-Fokus** | Splid, Splitwise | Rechnerisch korrekt, aber transaktional | Kein Event-Erlebnis |
| **Professionell/Corporate** | Eventbrite, Cvent | Professionell, aber Overkill für private Treffen | Zu viel für zu wenig |
| **Lifestyle/Social** | Meetup, Eventim | Community-Gefühl, aber für öffentliche Events | Nicht privat genug |
| **Lücke → TreffPunkt** |, | **Warm, persönlich, strukturiert, privat** | Bisher kein Anbieter besetzt diese Position |

TreffPunkt positioniert sich als **„der organisierte beste Freund"**: strukturiert genug, um 30 Leute zu koordinieren, warm genug, damit es sich nicht nach Projektmanagement anfühlt. Nicht Tool, sondern Vorfreude-Generator.

### 12.3 Markenkern, Tonalität und Sprache

| Dimension | Ausprägung |
|---|---|
| **Markenversprechen** | „TreffPunkt. Zusammen planen. Zusammen erleben." |
| **Werte** | Gemeinschaft · Leichtigkeit · Verlässlichkeit · Klarheit · Vorfreude |
| **Tonalität** | Freundlich, direkt, leicht humorvoll, wie eine SMS von einem guten Freund. Nie bürokratisch, nie übertrieben cool. |
| **Sprachregeln** | Du-Ansprache durchgängig. Kurze Sätze. Aktionsverben statt Nomen. Emojis sparsam, aber gezielt (📍🎉✅). |
| **Was TreffPunkt nicht ist** | Nicht „Plattform", nicht „Software", nicht „Lösung", sondern **Organisationshelfer**. |

**Claim-Vorschläge (Auswahl):**

- **„TreffPunkt. Zusammen planen. Zusammen erleben."** (Hauptclaim, Doppelstruktur)
- „TreffPunkt. Damit jemand ‚Ich organisier das!' sagen kann, ohne es zu bereuen."
- „TreffPunkt. Dein nächstes Treffen, ohne das WhatsApp-Chaos."
- „TreffPunkt. Alle an einem Punkt."

### 12.4 Visuelle Identität

| Element | Empfehlung | Begründung |
|---|---|---|
| **Primärfarbe** | Waldgrün `#2D6A4F` → `#40916C` | Natur, Gemeinschaft, Outdoor-Treffen; frisch und einladend. Hebt sich von blauen Tech-Marken ab. |
| **Akzentfarbe** | Warmes Amber/Orange `#F4A261` | Energie, Vorfreude, Wärme, „das Leuchten einer Einladung" |
| **Sekundär** | Creme `#FEFAE0`, Dunkelgrau `#3A3A3A` | Warme Hintergründe, gute Lesbarkeit |
| **Typografie Headline** | Runde Sans-Serif (z. B. *Nunito*, *Poppins*, *Quicksand*) | Freundlich, approachable, nicht steif |
| **Typografie Body** | Klare Sans (z. B. *Inter*, *DM Sans*) | Lesbar, modern, neutral |
| **Bildwelt** | Echte Gruppen beim Treffen. Grillen, Wandern, Tisch decken, Lachen. Warme Farbtöne, weiches Licht. **Keine** Stock-Fotos mit perfekten Models | Authentizität statt Werbung |
| **Illustrationen** | Einfache, warme Line-Art-Illustrationen (Personen, Kalender, Karten) | Leichtigkeit, Zugänglichkeit, internationale Verständlichkeit |
| **Bewegung** | Sanfte Konfetti-Animation bei Event-Bestätigung, Check-Animation bei erledigter Aufgabe | Belohnung und Freude micro-dosiert |

### 12.5 Logo-System (3 Darstellungen)

Das Logo basiert auf zwei Grundideen: **Gruppensymbolik** (verbundene Kreise als Personen) und **Treffpunkt-Marker** (Pin/Standort). Beide visualisieren das Kernversprechen: Menschen kommen zusammen an einem Punkt.

**Hauptlogo. Wortmarke mit Gruppen-Symbol und Pin**
*(siehe Kopf des Dokuments)*
Einsatz: Website-Header, Landingpage, Social-Media-Banner, E-Mail-Footer.

**Alternative 1. App-Icon / Monogramm „TP" als Gruppen-Pin**

<p align="center">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 160 160" width="140" height="140" role="img" aria-label="TreffPunkt App-Icon">
  <defs>
    <linearGradient id="tpIconGrad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0%" stop-color="#2D6A4F"/>
      <stop offset="100%" stop-color="#40916C"/>
    </linearGradient>
  </defs>
  <rect x="0" y="0" width="160" height="160" rx="36" ry="36" fill="url(#tpIconGrad)"/>
  <!-- Drei Kreise (Personen) verbunden -->
  <circle cx="60" cy="55" r="14" fill="#FEFAE0" opacity="0.9"/>
  <circle cx="100" cy="55" r="14" fill="#FEFAE0" opacity="0.9"/>
  <circle cx="80" cy="85" r="14" fill="#F4A261" opacity="0.95"/>
  <!-- Verbindungslinien -->
  <line x1="68" y1="63" x2="92" y2="63" stroke="#FEFAE0" stroke-width="2.5" opacity="0.6"/>
  <line x1="64" y1="67" x2="76" y2="80" stroke="#FEFAE0" stroke-width="2.5" opacity="0.6"/>
  <line x1="96" y1="67" x2="84" y2="80" stroke="#FEFAE0" stroke-width="2.5" opacity="0.6"/>
  <!-- Pin-Spitze unter dem orangenen Kreis -->
  <path d="M80 100 L74 115 L80 112 L86 115 Z" fill="#F4A261" opacity="0.9"/>
</svg>
</p>

Einsatz: PWA-Icon, Favicon, Social-Media-Avatar, WhatsApp-Profilbild.

**Alternative 2. Bildmarke „Konvergierende Wege zum Punkt"**

<p align="center">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 160" width="200" height="160" role="img" aria-label="TreffPunkt Bildmarke">
  <defs>
    <linearGradient id="tpFigGrad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0%" stop-color="#2D6A4F"/>
      <stop offset="100%" stop-color="#40916C"/>
    </linearGradient>
  </defs>
  <!-- Konvergierende Linien/Wege zum Zentrum -->
  <g stroke="url(#tpFigGrad)" stroke-width="3" stroke-linecap="round" fill="none" opacity="0.5">
    <line x1="30" y1="30" x2="85" y2="72"/>
    <line x1="170" y1="30" x2="115" y2="72"/>
    <line x1="30" y1="130" x2="85" y2="88"/>
    <line x1="170" y1="130" x2="115" y2="88"/>
    <line x1="100" y1="15" x2="100" y2="65"/>
  </g>
  <!-- Kleine Kreise an den Enden (Personen) -->
  <circle cx="30" cy="30" r="8" fill="url(#tpFigGrad)" opacity="0.6"/>
  <circle cx="170" cy="30" r="8" fill="url(#tpFigGrad)" opacity="0.6"/>
  <circle cx="30" cy="130" r="8" fill="url(#tpFigGrad)" opacity="0.6"/>
  <circle cx="170" cy="130" r="8" fill="url(#tpFigGrad)" opacity="0.6"/>
  <circle cx="100" cy="15" r="8" fill="url(#tpFigGrad)" opacity="0.6"/>
  <!-- Zentraler TreffPunkt -->
  <circle cx="100" cy="80" r="18" fill="#F4A261"/>
  <circle cx="100" cy="80" r="7" fill="#FEFAE0"/>
</svg>
</p>

Einsatz: Hero-Grafik Landingpage, Print-Material, Social-Media-Kampagnen. Symbolisiert: „Verschiedene Menschen kommen an einem Punkt zusammen."

### 12.6 Marketing-Strategie

| Kanal | Maßnahme | Erwartete Wirkung |
|---|---|---|
| **Virale Einladungen** | Jede Event-Einladung enthält TreffPunkt-Branding + „Erstelle dein eigenes Event"-Link | Organischer Wachstums-Loop (k-Faktor 0,3–0,5) |
| **SEO / Content** | Blog: „Klassentreffen organisieren. Checkliste", „JGA planen in 5 Schritten", „Familienfeier ohne Stress" | Long-Tail-Traffic mit hoher Conversion-Intent |
| **Social Media (Instagram, TikTok)** | Humorvolle Reels: „WhatsApp-Gruppenorganisation vs. TreffPunkt" | Relatable Content, virale Verbreitung |
| **Partnerships** | Locations (Restaurants, Bowlingbahnen, Escape Rooms) empfehlen TreffPunkt an Gruppen-Anfragen | Gegenseitige Empfehlung |
| **PR** | „Die DACH-App gegen WhatsApp-Chaos". Pitch an Lifestyle-/Tech-Magazine | Medien-Coverage |
| **Referral-Programm** | „Lade 3 Events ein → erhalte 1 Monat Plus gratis" | Incentivierte Weiterempfehlung |

### 12.7 Markenführung und nächste Schritte

1. **Domain-Sicherung:** treffpunkt.app, treffpunkt-app.de, meintreffpunkt.de
2. **Markenrechtliche Prüfung** TreffPunkt bei DPMA (Klasse 9, 42). Achtung: „Treffpunkt" als Allgemeinbegriff ist in Kombination mit Bildmarke und App-Kontext schützbar.
3. **Brand-Guideline-Onepager:** Farben, Typo, Logo-Schutzräume, Tonalität, Beispiele.
4. **Landing-Page + Waitlist** als Pre-Launch.
5. **10 Beta-Organizer** für Feedback vor öffentlichem Launch.

---

## Quellenverzeichnis

| Quelle | Inhalt |
|---|---|
| Bitkom Digitalbarometer Freizeit 2026 | Digitale Organisation privater Aktivitäten, Post-Pandemie-Trends |
| Statista Events & Freizeit DACH 2026 | Eventtypen und Häufigkeit |
| Grand View Research. Event Management Software 2026 | $14,5 Mrd. global, CAGR 11,2 % |
| Destatis Bevölkerungsstatistik 2025 | DACH-Bevölkerungsdaten, Schulabgänger-Statistik |
| Doodle. State of Meetings Report 2025 | Terminabstimmungs-Probleme |
| Splid Nutzerstatistiken 2025 | Kostenteilen in Gruppen |
| Eigene Nutzerbefragung DACH (n=320, März 2026) | Schmerzpunkte bei Gruppenorganisation |
| Meta WhatsApp Business Platform 2026 | Bot-API und Konversationspreise |
| EU-DSGVO Art. 6, 7, 8, 9 | Rechtsgrundlagen Datenverarbeitung, Minderjährige |
| PSD2 (Zahlungsdiensterichtlinie) | Regulierung Zahlungsdienste |
| G2 Event Management Category 2026 | Wettbewerbsvergleich |
| Capterra Event Planning Software 2026 | Marktübersicht |

---

*Dokument erstellt: 06. Mai 2026 | Version 1.0 | Autor: Daniel Moretz | Status: Zur Freigabe eingereicht*
*Alle Marktdaten basieren auf zum Erstellungszeitpunkt öffentlich verfügbaren Quellen. Für bindende rechtliche Aussagen (DSGVO, PSD2, Markenrecht) ist juristischer Beistand erforderlich.*

## ./HOWTO.md
# HOWTO — Project Setup & Deployment Guide

> 🎉 **Herzlichen Glückwunsch zur Einrichtung! / Congratulations on setting up!**
> Du kannst dieses Dokument nach Abschluss der Einrichtung löschen oder als Referenz behalten.
> You can delete this HOWTO document once your setup is complete, or keep it for future reference.

> 📖 **Lies die [AGENTS.md](AGENTS.md) Datei, um GitHub Copilot optimal und produktiv zu nutzen.**
> **Read the [AGENTS.md](AGENTS.md) file to use GitHub Copilot in an optimised and productive way.**

---

## DE Deutsch

---

### Prozessübersicht

Folge diesen Schritten in der angegebenen Reihenfolge, um vom Template zur Produktion zu gelangen:

1. **GitHub Repo erstellen** — Nutze dieses Template, um ein neues Repository in der Wamocon GitHub Organisation zu erstellen.
2. **Repo klonen** — Klone es auf deinen Rechner und führe `npm install` aus.
3. **Pre-commit Hook installieren** — Führe `bash hooks/install.sh` aus. Einmalig nach dem Klonen — schützt dich davor, Geheimnisse versehentlich zu pushen.
4. **GitHub Workflow-Datei überprüfen** — Öffne `.github/workflows/deploy.yml` und `.github/workflows/pr-pipeline.yml`, überprüfe, dass `Wamocon/github_workflow` die korrekte Referenz ist.
5. **`.env.local` aktualisieren & Supabase verbinden** — Kopiere `.env.example` → `.env.local`, erstelle ein Remote-Supabase-Projekt und trage die Zugangsdaten ein.
6. **Lokal starten & Entwicklung beginnen** — Führe `npm run dev` aus und beginne mit der Entwicklung.
7. **GitHub-Organisationseinstellungen: Vercel-App Zugriff gewähren** — Gehe zu den Organisationseinstellungen auf GitHub, suche die Vercel GitHub-App und gewähre ihr Zugriff auf dein neues Repo. Nur so erscheint das Repo in der Vercel-Importliste.
8. **Repo vorübergehend öffentlich machen & bei Vercel importieren** — Stelle das Repo temporär auf öffentlich und importiere es in Vercel.
9. **Vercel Project ID holen** — Kopiere die Vercel Project ID aus den Vercel-Projekteinstellungen.
10. **Vercel Project ID zu GitHub Secrets hinzufügen** — Füge `VERCEL_PROJECT_ID` zu den GitHub Actions Secrets deines Repos hinzu.
11. **Repo auf intern umstellen** — Ändere die Sichtbarkeit des Repos zurück auf intern.
12. **Erstes manuelles Deployment** — Gehe zu `Actions → "Deploy to Vercel" → Run workflow` und wähle `production`.

> 📖 **Für detaillierte Informationen, lies weiter unten.**

---

### 1. Klonen & Einrichten

```bash
# Repository klonen
git clone https://github.com/Wamocon/<dein-repo-name>.git
cd <dein-repo-name>

# Abhängigkeiten installieren
npm install

# Umgebungsvariablen kopieren
cp .env.example .env.local

# Pre-commit Hook installieren (einmalig, direkt nach npm install)
bash hooks/install.sh

# Entwicklungsserver starten (mit Turbopack für schnelles Hot-Reload)
npm run dev
```

Öffne [http://localhost:3000](http://localhost:3000) in deinem Browser.

**Verfügbare Skripte:**

| Befehl | Beschreibung |
|---|---|
| `npm run dev` | Startet den Dev-Server mit Turbopack (Hot Reload) |
| `npm run build` | Erstellt den Produktions-Build |
| `npm run start` | Startet den Produktionsserver |
| `npm run lint` | Führt ESLint aus |
| `npm run typecheck` | Führt TypeScript-Typprüfung aus |

---

### 1b. Git-Workflow & Branch-Strategie

> 💡 **Arbeite nach dem ersten Push immer auf einem Branch — nie direkt auf `main`/`master`.**

**Empfohlener Ablauf:**

```bash
# Einmalig: Ersten Stand auf main/master pushen
git add .
git commit -m "chore: initial setup"
git push origin <main-oder-master>

# Ab jetzt: Immer auf einem Feature-Branch arbeiten
git checkout -b feature/mein-feature

# Änderungen lokal testen, dann committen
npm run dev        # testen
npm run typecheck  # Typfehler prüfen
npm run lint       # Lint prüfen

git add .
git commit -m "feat: beschreibung der Änderung"
git push origin feature/mein-feature
```

**Wichtige Regeln:**

- **Lokal testen, bevor du pushst.** Führe `npm run typecheck` und `npm run lint` aus, bevor du Änderungen pushst.
- **Alle Änderungen vor dem PR-Öffnen pushen.** Jeder neue Push auf einen offenen PR triggert automatisch die GitHub Actions — das verbraucht GitHub Actions-Minuten.
- **Nur einen PR auf einmal offen halten**, bis er gemergt ist.

> ⚠️ **Warum das wichtig ist:** Jeder Push auf einen offenen PR löst die PR Pipeline aus (Auto-Fix + Typecheck + Lint). Teste erst lokal — dann push, dann PR.

---

### 1c. Pre-commit Hook — Geheimnis-Scanner

Der Pre-commit Hook verhindert, dass API-Schlüssel, Tokens, Passwörter oder andere Geheimnisse versehentlich in GitHub eingecheckt werden. Der Hook scannt alle für den Commit vorgesehenen Dateien, **bevor** der Commit abgeschlossen wird.

#### Installation

```bash
# Einmalig nach dem Klonen ausführen — nie wieder nötig:
bash hooks/install.sh
```

> ✅ **Wie oft?** Genau **einmal** — direkt nach `npm install` beim ersten Einrichten des Repos. Nach der Installation läuft der Hook automatisch vor **jedem** `git commit`.

#### Was der Hook prüft

| Muster | Beispiel |
|--------|---------|
| AWS-Schlüssel | `AKIA...`, `aws_secret_access_key = ...` |
| GitHub-Tokens | `ghp_...`, `github_pat_...` |
| Vercel-Token | `VERCEL_TOKEN = abc123...` |
| Private Keys (PEM) | `-----BEGIN PRIVATE KEY-----` |
| Datenbankverbindungen | `postgres://user:password@host` |
| Generische Tokens | `api_key =`, `client_secret =`, `password =` |
| JWT-Tokens | `eyJ...` (vollständige `header.payload.signature`-Form) |
| Supabase Service Role | `service_role = eyJ...` |
| `.env`-Dateien | `.env`, `.env.local`, `.env.production` |

#### Wenn ein Commit blockiert wird

```
[pre-commit] BLOCKED — potential secrets detected
  ✖ src/lib/config.ts:12
    Reason: Generic API key
    Content: const API_KEY = "abc123xyz789..."
```

**Lösung:**
1. Entferne das Geheimnis aus der Datei.
2. Speichere es in deiner `.env.local` (ist bereits in `.gitignore` eingetragen).
3. Nutze GitHub Actions Secrets für CI/CD-Werte.

**Bei einem Falsch-Positiv** (z.B. ein Beispielwert in der Doku):
Füge den Kommentar `# notsecret` am Ende der betroffenen Zeile hinzu.

**Notfall-Bypass** (nur im absoluten Ausnahmefall — niemals für echte Geheimnisse!):
```bash
git commit --no-verify -m "deine Nachricht"
```

---

### 2. Supabase Setup & Warnung

> ⚠️ **KRITISCH: Sobald du einen Supabase-Account hast, speichere alle Testdaten direkt dort.**
>
> **Lege Testdaten NICHT als lokale Dateien im Projektverzeichnis ab** (z.B. JSON-Fixtures, SQL-Dumps). Füge Daten stattdessen direkt in dein Supabase-Projekt ein — über das Dashboard, per MCP-Tool oder per Migrations-Skript.

**Schritte:**

1. Gehe zu [supabase.com](https://supabase.com) und erstelle ein neues Projekt.
2. Kopiere die **Project URL**, den **Anon Key** und den **Service Role Key** aus  
   `Project Settings → API`.
3. Trage sie in deine `.env.local` Datei ein:
   ```
   NEXT_PUBLIC_SUPABASE_URL=https://your-project-ref.supabase.co
   NEXT_PUBLIC_SUPABASE_ANON_KEY=dein-anon-key
   SUPABASE_SERVICE_ROLE_KEY=dein-service-role-key
   ```

---

### 2b. Lokales Supabase Setup via Docker (Optional)

> 💡 **Dieser Schritt ist optional.** Standardmäßig verbindest du dich direkt mit einem Remote-Supabase-Projekt (siehe Abschnitt 2). Nur wenn du lieber vollständig lokal entwickelst, ohne Internetverbindung zu Supabase, verwende dieses Setup.

Für ein vollständig lokales Supabase-Setup mit Docker und einer migrations-basierten Entwicklung, kopiere diesen Prompt in deinen KI-Assistenten (z.B. GitHub Copilot in VS Code):

```
Act as an expert DevOps and database engineer. I am developing an app locally. I need to set up a local Supabase instance via Docker and establish a strict migration-based workflow. Please execute the following:

Setup: Initialize a local Supabase environment using Docker and the Supabase CLI. Check automatically before every task if Docker and the Supabase containers are running. When they are down, start them autonomously.

Initial Schema: Create the initial database schema for the app and save it as a formal Supabase migration file.

Environment Variables: Automatically extract the local Supabase connection details (API URL, anon key, service role key, DB URL) and append them to my local .env file.

Autonomous Development & Schema Versioning: You will develop the entire application based on my prompts. You must autonomously create and update tables, generate schemas, and create timestamped migration files for every change. Ensure strict version history and guarantee that absolutely no functions fail due to database inconsistencies.

Production Deployment via MCP: I use the Supabase MCP to push data to production tables. Do not provide manual push commands. Your only job for production is to verify that all local migrations are completely up to date and error-free so the MCP can handle the live deployment seamlessly.

Automated Testing & Verification: Once the Docker setup is running and the schema is applied, automatically write and execute a small integration test. This test must verify that the app can successfully read from and write to the local Docker database. If any errors or bugs are detected, diagnose and fix them immediately on your own.
```

#### Lokale Supabase-Oberfläche im Browser öffnen

Sobald der lokale Docker-Stack läuft (`npx supabase start`), stellt Supabase eine vollständige Studio-Oberfläche bereit:

| Service | URL | Beschreibung |
|---|---|---|
| **Supabase Studio** | `http://localhost:54323` | Datenbank-UI: Tabellen, SQL-Editor, Auth, Storage |
| **REST API** | `http://localhost:54321` | PostgREST API (dein App-Endpoint) |
| **PostgreSQL** | `localhost:54322` | Direktzugriff (z.B. via pgAdmin, TablePlus) |
| **Inbucket (E-Mail)** | `http://localhost:54324` | Lokaler E-Mail-Dienst für Auth-Mails |

> 💡 Die exakten Ports werden nach `npx supabase start` auch in der Konsole ausgegeben. Der Befehl `npx supabase status` zeigt sie jederzeit an.

**Lokale Umgebungsvariablen:**
```
NEXT_PUBLIC_SUPABASE_URL=http://localhost:54321
NEXT_PUBLIC_SUPABASE_ANON_KEY=<aus supabase status kopieren>
SUPABASE_SERVICE_ROLE_KEY=<aus supabase status kopieren>
SUPABASE_DB_URL=postgresql://postgres:postgres@localhost:54322/postgres
```

---

### 3. Supabase MCP & Schemas

#### Supabase MCP für Migrationen verwenden

Der Supabase MCP (Model Context Protocol) Server ermöglicht es deinem KI-Coding-Assistenten (z.B. GitHub Copilot, Cursor), Migrationen und Tabellen direkt zu erstellen und zu verwalten.

- Migrationen werden in `supabase/migrations/` gespeichert.
- Nutze die MCP-Tools, um Tabellen zu erstellen, Schemas zu ändern und Indizes zu verwalten.

#### Arbeiten mit mehreren Schemas

Standardmäßig macht Supabase nur das `public`-Schema über die API verfügbar. Wenn du eigene Schemas brauchst:

**1. Schema erstellen:**
```sql
CREATE SCHEMA IF NOT EXISTS app;
```

**2. Berechtigungen vergeben:**
```sql
GRANT USAGE ON SCHEMA app TO anon, authenticated, service_role;
GRANT ALL ON ALL TABLES IN SCHEMA app TO anon, authenticated, service_role;
ALTER DEFAULT PRIVILEGES IN SCHEMA app
  GRANT ALL ON TABLES TO anon, authenticated, service_role;
GRANT ALL ON ALL SEQUENCES IN SCHEMA app TO anon, authenticated, service_role;
ALTER DEFAULT PRIVILEGES IN SCHEMA app
  GRANT ALL ON SEQUENCES TO anon, authenticated, service_role;
```

**3. Schema über die Supabase API zugänglich machen:**
Gehe zu `Project Settings → API → Exposed schemas` und füge deinen Schema-Namen hinzu.

---

### 4. GitHub Workflow Konfiguration

Dieses Projekt nutzt den **zentralen Wamocon CI/CD-Workflow** aus [`Wamocon/github_workflow`](https://github.com/Wamocon/github_workflow).

#### Übersicht der drei Workflows

| Workflow | Datei | Auslöser | Was es tut |
|---|---|---|---|
| **PR Pipeline** | `pr-pipeline.yml` | **Automatisch** bei jedem PR auf `main`/`master` | Auto-Fix (ESLint + Prettier) → Typecheck + Lint |
| **Deploy** | `deploy.yml` | **Manuell** — kein Auto-Trigger | Baut das Projekt via Vercel CLI und deployed auf Vercel |
| **LP Generator** | `lp-generator.yml` | **Manuell** — kein Auto-Trigger | Generiert eine Landing Page in einem neuen Repo |

> ⚠️ **Kein automatisches Deployment:** Weder ein PR noch ein Push auf `main` startet automatisch ein Deployment. Alle Deployments werden manuell über den Actions-Tab gestartet.

#### Was du tun musst

1. Überprüfe, dass `Wamocon/github_workflow` die korrekte Org/Repo-Referenz ist.
2. Aktiviere Workflow-Schreibrechte:  
   `Settings → Actions → General → Workflow permissions → Allow GitHub Actions to create and approve pull requests`
3. Füge **ein einziges Secret** zu deinem Repository hinzu:
   - Gehe zu `Repository → Settings → Secrets and variables → Actions → New repository secret`
   - Name: `VERCEL_PROJECT_ID`
   - Wert: *(siehe Abschnitt 5 unten)*

> ✅ **Alle anderen benötigten Secrets** (`VERCEL_TOKEN`, `VERCEL_ORG_ID`) sind **bereits auf GitHub-Organisationsebene konfiguriert**.

#### Manuelles Deployment starten

```
Repository auf GitHub → Actions → "Deploy to Vercel" → Run workflow
→ Environment auswählen: production oder preview
→ Run workflow klicken
```

---

### 5. Vercel Deployment-Strategie

#### Schritt 1: GitHub-Org Vercel-App Zugriff gewähren (Einmalig, Kritisch)

> ⚠️ **Dieser Schritt muss VOR dem Vercel-Import durchgeführt werden.** Ohne ihn erscheint dein Repo nicht in der Vercel-Importliste — auch wenn es öffentlich ist.

1. Gehe zu **GitHub → Wamocon Organisation → Settings**  
   `https://github.com/organizations/Wamocon/settings/installations`
2. Suche die **Vercel**-App in der Liste der installierten GitHub Apps.
3. Klicke auf **Configure**.
4. Scrolle zu **Repository access**.
5. Wähle **"Only select repositories"** und füge dein neues Repo hinzu.
6. Klicke **Save**.

#### Schritt 2: Erstmalige Bereitstellung (Einmalig)

1. **Repo vorübergehend öffentlich machen**  
   `Repository → Settings → General → Change visibility → Public`
2. Gehe zu [vercel.com](https://vercel.com) → **Add New Project** → **Import** → dein Repo auswählen.
3. Deploye das Projekt (Vercel erkennt Next.js automatisch).
4. **Vercel Project ID kopieren:**  
   `Vercel Project → Settings → General → Project ID` → ID kopieren.
5. **Zu GitHub Secrets hinzufügen:**  
   `Repository → Settings → Secrets and variables → Actions → New repository secret`  
   Name: `VERCEL_PROJECT_ID` | Wert: die kopierte ID.
6. **Repo auf intern zurücksetzen:**  
   `Repository → Settings → General → Change visibility → Internal`

> 💡 **Nach diesem einmaligen Setup** deployt die GitHub Action via Vercel CLI — Vercel sieht nicht mehr, wer committed, und es gibt keine Team-Seat-Fehler bei einem privaten Hobby-Account.

#### Schritt 3: Umgebungsvariablen in Vercel eintragen

> ⚠️ **WICHTIG:** Gehe zu `Vercel Project → Settings → Environment Variables` und füge **alle** Variablen aus deiner `.env.local` hinzu. Ohne diese wird der Build **fehlschlagen**.

#### Deployment-Ablauf (nach dem Setup)

| Auslöser | Ergebnis |
|---|---|
| PR auf `main`/`master` | PR Pipeline läuft automatisch (kein Deployment) |
| Merge auf `main`/`master` | Kein automatisches Deployment |
| **Manuelles Workflow-Start** | Deployment nach Auswahl: `production` oder `preview` |

**Manuell deployen:**

```
GitHub → Actions → "Deploy to Vercel" → Run workflow
→ environment: production  (für die Live-URL)
→ environment: preview     (für eine Test-URL)
→ db_schema: (leer lassen — Vercel-Umgebungsvariablen werden genutzt)
```

---

### 6. Domain-Verwaltung

1. **Sichere eine Domain** für deine Anwendung über [Strato](https://www.strato.de).
2. Gehe in den Vercel-Projekteinstellungen zu `Settings → Domains` und füge deine Domain hinzu.
3. Konfiguriere die DNS-Einträge bei Strato wie von Vercel angegeben (typischerweise CNAME oder A-Record).

---

### 7. Projekt-Checkliste

- [ ] Landing Page
- [ ] Handbuch / Manual
- [ ] Hauptprozess (Kernfunktion)
- [ ] Video (Demo / Tutorial)
- [ ] Domain (über Strato gesichert)

---

### 8. Landing Page Generator

Das Workflow-File `.github/workflows/lp-generator.yml` generiert eine Landing Page für diese App.

#### Was der Workflow tut

- Liest den Inhalt dieses Repos aus
- Verwendet ein konfigurierbares **Design-Template** als optische Basis
- Lässt GitHub Copilot eine Landing Page generieren und ein neues Repo dafür anlegen

#### Was du ändern kannst

| Eingabe | Standard | Beschreibung |
|---|---|---|
| `custom_template` | `Wamocon/hochzeitsrechner_lp` | Das GitHub-Repo, das als Design-Template dient |
| `custom_name` | `generated_lp` | Name des neu erstellten Landing-Page-Repos |
| `custom_prompt` | *(allgemeiner Prompt)* | Detaillierte Anweisungen für Copilot |

> 💡 **Tipp:** Je spezifischer dein Prompt, desto besser die generierte Landing Page.

#### Wann du den Workflow starten sollst

Starte diesen Workflow **erst dann**, wenn dein Projekt weitgehend fertig dokumentiert ist:
- Handbuch / Manual
- README mit Produktbeschreibung, Features und Zielgruppe
- Rechtstexte / relevante Seiten

> ✅ **Empfehlung:** In der Regel reicht **ein einmaliger Lauf** am Projektende.

#### Manuell ausführen

`Repository → Actions → "🚀 lp-generator" → Run workflow`

1. Wähle in der linken Liste den Workflow **"🚀 lp-generator"**.
2. Klicke rechts auf **"Run workflow"**.
3. Passe Template, Name und Prompt an.
4. Bestätige mit **"Run workflow"**.

#### Wenn der Workflow fehlschlägt

Wenn bereits ein Repository mit gleichem Namen existiert:
1. Ändere den Namen in `custom_name` und starte erneut.
2. Oder lösche das bestehende Ziel-Repo und starte erneut.

---
---

## EN English

---

### Process Overview

Follow these steps in order to go from template to production:

1. **Create GitHub Repo** — Use this template to create a new repository in the Wamocon GitHub organisation.
2. **Clone Repo** — Clone to your local machine and run `npm install`.
3. **Install pre-commit hook** — Run `bash hooks/install.sh`. One-time setup after cloning — protects you from accidentally pushing secrets.
4. **Check GitHub Workflow files** — Open `.github/workflows/deploy.yml` and `.github/workflows/pr-pipeline.yml`, verify that `Wamocon/github_workflow` is the correct reference.
5. **Update `.env.local` & connect Supabase** — Copy `.env.example` → `.env.local`, create a remote Supabase project, and fill in the credentials.
6. **Run locally & start development** — Run `npm run dev` and start building.
7. **GitHub Organisation Settings: Grant Vercel app access** — Go to the organisation settings on GitHub, find the Vercel GitHub App, and grant it access to your new repo. Without this, the repo will not appear in Vercel's import list.
8. **Make repo temporarily public & import in Vercel** — Set the repo to public temporarily and import it in Vercel.
9. **Get Vercel Project ID** — Copy the Vercel Project ID from the Vercel project settings.
10. **Add Vercel Project ID to GitHub secrets** — Add `VERCEL_PROJECT_ID` to your repository's GitHub Actions secrets.
11. **Make repo internal** — Revert the repository visibility to internal.
12. **First manual deployment** — Go to `Actions → "Deploy to Vercel" → Run workflow` and choose `production`.

> 📖 **For detailed information, read below.**

---

### 1. Clone & Setup

```bash
# Clone the repository
git clone https://github.com/Wamocon/<your-repo-name>.git
cd <your-repo-name>

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env.local

# Install pre-commit hook (once, right after npm install)
bash hooks/install.sh

# Start the development server (with Turbopack for fast refresh)
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

**Available scripts:**

| Command | Description |
|---|---|
| `npm run dev` | Start dev server with Turbopack (hot reload) |
| `npm run build` | Create production build |
| `npm run start` | Start production server |
| `npm run lint` | Run ESLint |
| `npm run typecheck` | Run TypeScript type checking |

---

### 1b. Git Workflow & Branching Strategy

> 💡 **After the first push, always work on a branch — never directly on `main`/`master`.**

**Recommended flow:**

```bash
# One-time: push the initial state to main/master
git add .
git commit -m "chore: initial setup"
git push origin <main-or-master>

# From now on: always work on a feature branch
git checkout -b feature/my-feature

# Test locally, then commit
npm run dev        # test in browser
npm run typecheck  # catch type errors
npm run lint       # catch lint issues

git add .
git commit -m "feat: description of change"
git push origin feature/my-feature
```

**Key rules:**

- **Test locally before pushing.** Always run `npm run typecheck` and `npm run lint` before pushing.
- **Push all changes before opening the PR.** Every new push to an open PR triggers the GitHub Actions pipeline — this consumes GitHub Actions minutes.
- **Keep only one PR open at a time** until it is merged.

> ⚠️ **Why this matters:** Every push to an open PR triggers the PR Pipeline (Auto-Fix + Typecheck + Lint). Test locally first — then push, then open the PR.

---

### 1c. Pre-commit Hook — Secret Scanner

The pre-commit hook prevents API keys, tokens, passwords, or other secrets from accidentally being checked into GitHub. The hook scans all files staged for commit **before** the commit is finalised.

#### Installation

```bash
# Run ONCE after cloning — never needs to run again:
bash hooks/install.sh
```

> ✅ **How often?** Exactly **once** — right after `npm install` when first setting up the repo. After installation, the hook runs automatically before **every** `git commit`.

#### What the hook checks

| Pattern | Example |
|--------|---------|
| AWS keys | `AKIA...`, `aws_secret_access_key = ...` |
| GitHub tokens | `ghp_...`, `github_pat_...` |
| Vercel token | `VERCEL_TOKEN = abc123...` |
| Private keys (PEM) | `-----BEGIN PRIVATE KEY-----` |
| Database connection strings | `postgres://user:password@host` |
| Generic tokens | `api_key =`, `client_secret =`, `password =` |
| JWT tokens | `eyJ...` (full `header.payload.signature` form) |
| Supabase service role | `service_role = eyJ...` |
| `.env` files | `.env`, `.env.local`, `.env.production` |

#### When a commit is blocked

```
[pre-commit] BLOCKED — potential secrets detected
  ✖ src/lib/config.ts:12
    Reason: Generic API key
    Content: const API_KEY = "abc123xyz789..."
```

**How to fix:**
1. Remove the secret from the file.
2. Store it in your `.env.local` (already in `.gitignore`).
3. Use GitHub Actions secrets for CI/CD values.

**False positive** (e.g. an example value in documentation):  
Add the comment `# notsecret` at the end of that line.

**Emergency bypass** (absolute last resort — never for real secrets!):
```bash
git commit --no-verify -m "your message"
```

---

### 2. Supabase Setup & Warning

> ⚠️ **CRITICAL: Once you have a Supabase account, store all test data there directly.**
>
> **Do NOT store test data as local files** (e.g. JSON fixtures, SQL dumps). Insert data directly into your Supabase project — via the Dashboard, an MCP tool, or a migration script.

**Steps:**

1. Go to [supabase.com](https://supabase.com) and create a new project.
2. Copy the **Project URL**, **Anon Key**, and **Service Role Key** from  
   `Project Settings → API`.
3. Paste them into your `.env.local` file:
   ```
   NEXT_PUBLIC_SUPABASE_URL=https://your-project-ref.supabase.co
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
   SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
   ```

---

### 2b. Local Supabase Setup via Docker (Optional)

> 💡 **This step is optional.** By default you connect directly to a remote Supabase project (see section 2). Only use this setup if you prefer developing fully offline.

For a fully local Supabase setup with Docker and a migration-based development workflow, copy this prompt into your AI assistant (e.g. GitHub Copilot in VS Code):

```
Act as an expert DevOps and database engineer. I am developing an app locally. I need to set up a local Supabase instance via Docker and establish a strict migration-based workflow. Please execute the following:

Setup: Initialize a local Supabase environment using Docker and the Supabase CLI. Check automatically before every task if Docker and the Supabase containers are running. When they are down, start them autonomously.

Initial Schema: Create the initial database schema for the app and save it as a formal Supabase migration file.

Environment Variables: Automatically extract the local Supabase connection details (API URL, anon key, service role key, DB URL) and append them to my local .env file.

Autonomous Development & Schema Versioning: You will develop the entire application based on my prompts. You must autonomously create and update tables, generate schemas, and create timestamped migration files for every change. Ensure strict version history and guarantee that absolutely no functions fail due to database inconsistencies.

Production Deployment via MCP: I use the Supabase MCP to push data to production tables. Do not provide manual push commands. Your only job for production is to verify that all local migrations are completely up to date and error-free so the MCP can handle the live deployment seamlessly.

Automated Testing & Verification: Once the Docker setup is running and the schema is applied, automatically write and execute a small integration test. This test must verify that the app can successfully read from and write to the local Docker database. If any errors or bugs are detected, diagnose and fix them immediately on your own.
```

#### Viewing the local database in the browser

| Service | URL | Description |
|---|---|---|
| **Supabase Studio** | `http://localhost:54323` | Database UI: tables, SQL editor, Auth, Storage |
| **REST API** | `http://localhost:54321` | PostgREST API (your app endpoint) |
| **PostgreSQL** | `localhost:54322` | Direct DB access (e.g. pgAdmin, TablePlus) |
| **Inbucket (email)** | `http://localhost:54324` | Local email service for Auth emails |

**Local environment variables:**
```
NEXT_PUBLIC_SUPABASE_URL=http://localhost:54321
NEXT_PUBLIC_SUPABASE_ANON_KEY=<copy from supabase status output>
SUPABASE_SERVICE_ROLE_KEY=<copy from supabase status output>
SUPABASE_DB_URL=postgresql://postgres:postgres@localhost:54322/postgres
```

---

### 3. Supabase MCP & Schemas

#### Using Supabase MCP for Migrations

The Supabase MCP (Model Context Protocol) server allows your AI coding assistant to create and manage migrations and tables directly.

- Migrations are stored in `supabase/migrations/`.
- Use the MCP tools to create tables, alter schemas, and manage indexes.

#### Working with Multiple Schemas

By default, Supabase only exposes the `public` schema via the API. If you need custom schemas:

**1. Create the schema:**
```sql
CREATE SCHEMA IF NOT EXISTS app;
```

**2. Grant permissions:**
```sql
GRANT USAGE ON SCHEMA app TO anon, authenticated, service_role;
GRANT ALL ON ALL TABLES IN SCHEMA app TO anon, authenticated, service_role;
ALTER DEFAULT PRIVILEGES IN SCHEMA app
  GRANT ALL ON TABLES TO anon, authenticated, service_role;
GRANT ALL ON ALL SEQUENCES IN SCHEMA app TO anon, authenticated, service_role;
ALTER DEFAULT PRIVILEGES IN SCHEMA app
  GRANT ALL ON SEQUENCES TO anon, authenticated, service_role;
```

**3. Expose the schema via the Supabase API:**
Go to `Project Settings → API → Exposed schemas` and add your custom schema name.

---

### 4. GitHub Workflow Configuration

This project uses the **centralized Wamocon CI/CD workflow** from [`Wamocon/github_workflow`](https://github.com/Wamocon/github_workflow).

#### Overview of the three workflows

| Workflow | File | Trigger | What it does |
|---|---|---|---|
| **PR Pipeline** | `pr-pipeline.yml` | **Automatic** on every PR to `main`/`master` | Auto-Fix (ESLint + Prettier) → Typecheck + Lint |
| **Deploy** | `deploy.yml` | **Manual only** — no auto-trigger | Builds and deploys to Vercel via CLI |
| **LP Generator** | `lp-generator.yml` | **Manual only** — no auto-trigger | Generates a landing page in a new repo |

> ⚠️ **No automatic deployment:** Neither a PR nor a push to `main` triggers a deployment automatically. All deployments are started manually from the Actions tab.

#### What you need to do

1. Verify that `Wamocon/github_workflow` is the correct org/repo reference.
2. Enable workflow write permissions:  
   `Settings → Actions → General → Workflow permissions → Allow GitHub Actions to create and approve pull requests`
3. Add **one single secret** to your repository:
   - Go to `Repository → Settings → Secrets and variables → Actions → New repository secret`
   - Name: `VERCEL_PROJECT_ID`
   - Value: *(see section 5 below)*

> ✅ **All other required secrets** (`VERCEL_TOKEN`, `VERCEL_ORG_ID`) are **already configured at the GitHub Organisation level**.

#### Triggering a manual deployment

```
GitHub repo → Actions → "Deploy to Vercel" → Run workflow
→ Choose environment: production or preview
→ Click "Run workflow"
```

---

### 5. Vercel Deployment Strategy

#### Step 1: Grant Vercel GitHub App access in Org Settings (One-time, Critical)

> ⚠️ **This step must be done BEFORE importing in Vercel.** Without it, your repo will not appear in Vercel's import list — even if it is public.

1. Go to **GitHub → Wamocon Organisation → Settings → Installed GitHub Apps**  
   `https://github.com/organizations/Wamocon/settings/installations`
2. Find the **Vercel** app in the list.
3. Click **Configure**.
4. Scroll to **Repository access**.
5. Select **"Only select repositories"** and add your new repo.
6. Click **Save**.

#### Step 2: Initial Deployment (One-Time)

1. **Make the repo public** temporarily  
   `Repository → Settings → General → Change visibility → Public`
2. Go to [vercel.com](https://vercel.com) → **Add New Project** → **Import** → select your repo.
3. Deploy the project (Vercel detects Next.js automatically).
4. **Copy the Vercel Project ID:**  
   `Vercel Project → Settings → General → Project ID` → copy the value.
5. **Add to GitHub secrets:**  
   `Repository → Settings → Secrets and variables → Actions → New repository secret`  
   Name: `VERCEL_PROJECT_ID` | Value: the ID you copied.
6. **Revert the repo to internal:**  
   `Repository → Settings → General → Change visibility → Internal`

> 💡 **After this one-time setup**, the GitHub Action deploys via Vercel CLI — Vercel no longer sees who committed, and there are no team seat errors with a personal Hobby account.

#### Step 3: Add environment variables in Vercel

> ⚠️ **CRUCIAL:** Go to `Vercel Project → Settings → Environment Variables` and add **all** variables from your `.env.local`. Without these, the build **will fail**.

#### Deployment flow (after setup)

| Trigger | Result |
|---|---|
| PR targeting `main`/`master` | PR Pipeline runs automatically (no deployment) |
| Merge / push to `main`/`master` | No automatic deployment |
| **Manual workflow run** | Deploys to the chosen environment: `production` or `preview` |

**How to deploy manually:**

```
GitHub → Actions → "Deploy to Vercel" → Run workflow
→ environment: production  (for the live URL)
→ environment: preview     (for a temporary test URL)
→ db_schema: (leave empty — Vercel env vars are used)
```

---

### 6. Domain Management

1. **Secure a domain** for your application via [Strato](https://www.strato.de).
2. In the Vercel project settings, go to `Settings → Domains` and add your domain.
3. Configure the DNS records at Strato as shown by Vercel (typically a CNAME or A record).

---

### 7. Project Checklist

- [ ] Landing Page
- [ ] Handbuch / Manual
- [ ] Main Process (core feature)
- [ ] Video (demo / tutorial)
- [ ] Domain (secured via Strato)

---

### 8. Landing Page Generator

The workflow file `.github/workflows/lp-generator.yml` generates a landing page for this app by calling a central, reusable Wamocon workflow.

#### What the workflow does

- Reads the contents of this repository
- Uses a configurable **design template** as a visual base
- Lets GitHub Copilot generate a landing page and create a new repository for it

#### What you can change

| Input | Default | Description |
|---|---|---|
| `custom_template` | `Wamocon/hochzeitsrechner_lp` | The GitHub repo used as the design template |
| `custom_name` | `generated_lp` | Name for the newly created landing page repository |
| `custom_prompt` | *(generic prompt)* | Detailed instructions for Copilot |

> 💡 **Tip:** The more specific your prompt, the better the generated landing page.

#### When you should run this workflow

Run this workflow **only after** your project is mostly complete:
- Handbook / Manual
- README with product description, features, and target audience
- Legal pages / relevant links

> ✅ **Recommendation:** In most cases, you only need to run it **once** at the end of the project.

#### Running manually

`Repository → Actions → "🚀 lp-generator" → Run workflow`

1. Select **"🚀 lp-generator"** from the left workflow list.
2. Click **"Run workflow"** on the right.
3. Adjust the input fields (template, name, prompt) as needed.
4. Confirm with **"Run workflow"**.

#### If the workflow fails (repository name already exists)

1. Change the `custom_name` value and run the workflow again.
2. Or delete the existing target repository (if no longer needed) and run again.

## ./IDEA.md
# Projektidee

> Fuell diese Datei aus, bevor du den Skill `anforderungsdokument` aufrufst.
> Je mehr Details du hier schreibst, desto besser wird das generierte Dokument.
> Anleitung: `.github/skills/anforderungsdokument/SKILL.md`

---

## Projektname

[Name der App, z.B. "Universal Inventory Manager"]

---

## Beschreibung

[Was macht die App? Welches Problem loest sie? Sei konkret.

Beispiel:
"Eine webbasierte Lagerverwaltungs-App fuer kleine und mittelgrosse Unternehmen in
Deutschland. Sie ersetzt Excel-basierte Bestandslisten durch ein strukturiertes System
mit Echtzeit-Uebersicht, QR-Code-Scanfunktion und automatisierten Benachrichtigungen.
Das Ziel ist es, manuelle Fehler bei der Lagerhaltung um mindestens 80 % zu reduzieren
und den Zeitaufwand fuer Inventurprozesse auf ein Minimum zu senken."]

---

## Zielgruppe

[Wer soll die App nutzen? Branche, Unternehmensgroesse, Rolle.

Beispiel:
"Lager- und Logistikleiter sowie Mitarbeiter in KMU mit 10 bis 200 Angestellten,
insbesondere im Einzel-, Gross- und Onlinehandel in Deutschland und dem
deutschsprachigen Europa."]

---

## Kernproblem

[Das konkrete Problem, das OHNE die App besteht.

Beispiel:
"Lagerfehler durch manuelle Erfassung in Excel kosten KMU durchschnittlich
14 % des Jahresumsatzes. Bestehende Enterprise-Loesungen wie SAP EWM sind
fuer kleinere Betriebe zu komplex und zu teuer."]

---

## Gewuenschte Hauptfunktionen (Version 1)

[Liste der wichtigsten Funktionen. Beispiel:]

- Artikel anlegen, bearbeiten, loeschen
- Lagerbestand in Echtzeit einsehen
- QR-Code-Etiketten generieren und scannen
- Rollenbasierter Zugriff (Admin, Manager, Mitarbeiter)
- Mehrsprachige Oberflaeche (Deutsch und Englisch)
- Dashboard mit Bestandsuebersicht

---

## Tech-Stack (optional, wenn bekannt)

[Bekannte oder gewuenschte Technologien. Standardempfehlung falls leer:
Next.js, React, TypeScript, Supabase, Tailwind CSS, Vercel]

---

## Marktsegment und Branche

[In welchem Markt soll die App operieren?

Beispiel: "Lagerverwaltungssoftware (WMS) fuer KMU in Deutschland, Segment Mittelstand"]

---

## Bekannte Wettbewerber (optional)

[Bestehende Loesungen, die aehnliches tun.

Beispiel: SAP EWM, Sage Wawi, Pickware, Odoo Inventory, Lightspeed]

---

## Ersteller

[Vollstaendiger Name]

---

## Empfaenger (Geschaeftsfuehrung)

[Name und Titel des Entscheidungstraegers, z.B. "waleri moretz, CEO WAMOCON GmbH"]

---

## Welle und Version

1

---

## Zusaetzliche Hinweise (optional)

[Besondere Anforderungen, Einschraenkungen, Deadlines oder andere relevante
Informationen, die im Dokument beruecksichtigt werden sollen.]

## ./docs/PROGRESS.md
# TreffPunkt V1 — Fortschrittsdokumentation

Stand: Session vom 10. Mai 2026

---

## 1. Zusammenfassung

TreffPunkt V1 wurde als vollständige Next.js 16 Webanwendung implementiert. Die App ist ein Mini-Event-Manager für private Gruppenorganisation (Klassentreffen, Freundesgruppen, Ausflüge, JGAs, Familienfeiern). Alle im Anforderungsdokument beschriebenen V1-Module wurden umgesetzt.

---

## 2. Umgesetzte Module (V1)

| Modul | Status | Dateien |
|---|---|---|
| **Authentifizierung** | ✅ Fertig | `login/page.tsx`, `register/page.tsx`, `auth/callback/route.ts` |
| **Dashboard** | ✅ Fertig | `dashboard/page.tsx`, `dashboard-content.tsx` |
| **Event-Erstellung** | ✅ Fertig | `events/new/page.tsx` |
| **Event-Detail** | ✅ Fertig | `events/[id]/page.tsx`, `event-detail-content.tsx` |
| **Teilnehmerverwaltung** | ✅ Fertig | `members-section.tsx` (RSVP, Rollen, Gäste) |
| **Terminabstimmung** | ✅ Fertig | `date-poll-section.tsx` (Doodle-Stil, 3 Optionen) |
| **Standortabstimmung** | ✅ Fertig | `location-poll-section.tsx` (Thumbs up/down) |
| **Aufgaben** | ✅ Fertig | `tasks-section.tsx` (CRUD, Checklisten, Volunteer) |
| **Budget** | ✅ Fertig | `budget-section.tsx` (Kostenaufteilung, Settlements) |
| **Einladungen** | ✅ Fertig | `invite-section.tsx`, `invite-content.tsx`, `invite/[token]/page.tsx` |
| **Internationalisierung** | ✅ Fertig | DE + EN via next-intl, Sprachumschalter |
| **Dark/Light Theme** | ✅ Fertig | next-themes, CSS Custom Properties |
| **Homepage** | ✅ Fertig | Hero, Features, Event-Typen, How It Works, CTA |
| **Legal** | ✅ Fertig | Impressum, Datenschutz, AGB |
| **Seed Data** | ✅ Fertig | 5 User, 4 Events, Polls, Votes, Tasks, Budget |

---

## 3. Technischer Stack

- **Framework:** Next.js 16.2.1 (App Router, Turbopack)
- **Sprache:** TypeScript (strict mode)
- **Styling:** Tailwind CSS v4 mit Custom Theme (`--color-tp-*`)
- **Backend:** Supabase (lokal via Docker)
- **i18n:** next-intl (DE/EN)
- **Icons:** lucide-react
- **Ports:** API: 54351, DB: 54352, Studio: 54353, Inbucket: 54354

---

## 4. Datenbank-Schema

15 Tabellen mit vollständigem RLS:
- `profiles`, `events`, `event_members`
- `date_polls`, `date_options`, `date_votes`
- `location_polls`, `location_options`, `location_votes`
- `tasks`, `task_checklist_items`, `task_comments`
- `budget_items`, `settlements`, `notifications`

Enums: `event_type`, `event_status`, `member_role`, `rsvp_status`, `vote_value`, `task_status`, `payment_status`, `notification_type`

---

## 5. Testdaten

4 realistische Events mit verschiedenen Szenarien:
1. **Klassentreffen Abi 2016** — Vollständig: Date-Poll, Location-Poll, Tasks, Budget, Gäste
2. **JGA von Thomas** — Abgeschlossen: Budget mit Settlements
3. **Wanderausflug Taunus** — Festes Datum, Aufgaben mit Volunteers
4. **Omas 70. Geburtstag** — Familienfeier mit Budget-Planung

Login-Daten (Passwort für alle: `test1234`):
- sarah@example.com (Organisatorin Event 1)
- max@example.com (Organisator Event 2)
- lisa@example.com (Organisatorin Event 4)
- tim@example.com (Organisator Event 3)
- anna@example.com (Helferin)

---

## 6. Verifikation

| Check | Ergebnis |
|---|---|
| `npm run typecheck` | ✅ Keine Fehler |
| `npm run lint` | ✅ Keine Fehler/Warnungen |
| `npm run build` | ✅ Erfolgreich (alle 12 Routen) |
| Datenbank-Seed | ✅ Erfolgreich (alle Tabellen befüllt) |

---

## 7. Bekannte Einschränkungen / Nächste Schritte

### Nicht in V1 enthalten (bewusst ausgeklammert)
- PayPal-Integration für Settlements

### Ideen für zukünftige Versionen (V2+)
- **AI-gestützte Event-Vorschläge** — Basierend auf früheren Events automatisch Aktivitäten, Locations und Zeitfenster vorschlagen
- **Intelligente Budget-Aufteilung** — AI analysiert Ausgabenmuster und schlägt faire Aufteilungen vor (z.B. gewichtete Splits basierend auf Teilnahme)
- **Automatische Zusammenfassung** — AI generiert Event-Zusammenfassungen nach Abschluss (Highlights, Statistiken, Erinnerungen)
- **Smarte Terminvorschläge** — AI berücksichtigt typische Verfügbarkeitsmuster der Gruppe bei Terminvorschlägen
- **Chatbot-Assistent** — Integrierter AI-Chat für schnelle Event-Verwaltung ("Wer hat noch nicht zugesagt?", "Was kostet das Event?")
- **Foto-Galerie mit AI-Tagging** — Automatische Gesichtserkennung und Kategorisierung von Event-Fotos
- **Wiederkehrende Events** — Templates und automatische Erstellung für regelmäßige Treffen

### In V1.1 nachgeliefert
- ✅ Echtzeit-Benachrichtigungen (Supabase Realtime mit Polling-Fallback)
- ✅ Profil-Bearbeitungsseite (Avatar-Upload, Anzeigename, Spracheinstellung)
- ✅ Event-Bearbeitungsseite (Titel, Beschreibung, Typ, Status, Datum, Ort, Max-Teilnehmer, Löschung)
- ✅ Datei-Upload für Event-Bilder (Header-Bild Upload/Ersetzen/Löschen)
- ✅ E-Mail-Versand für Einladungen (via Resend, DE/EN Templates, Fallback auf Link)
- ✅ Detaillierte Berechtigungsprüfung auf UI-Ebene (Permissions-Modul mit Rollen-basiertem Zugriff)

### In V1.2 nachgeliefert
- ✅ Event-Finalisierung/-Wiederöffnung (Organisatoren können Events als abgeschlossen markieren oder wieder öffnen)
- ✅ Dashboard: Getrennte Sektionen "Ich organisiere" / "Ich nehme teil" mit Rollen-Icons
- ✅ Verbesserte Teilnehmerverwaltung: Kontextmenü (⋯) statt winzigem Chevron für Rollenwechsel
- ✅ RSVP-Override: Organisatoren können den RSVP-Status jedes Teilnehmers setzen
- ✅ Teilnehmer entfernen: Organisatoren können Teilnehmer aus Events entfernen (mit Bestätigung)
- ✅ Co-Organisator-Berechtigungen: RLS-Policies erweitert für Co-Organisator-Verwaltungsrechte
- ✅ Neue Berechtigungen: `override_rsvp`, `kick_member`, `finalize_event`
- ✅ Alle neuen Features vollständig internationalisiert (DE + EN)
- ✅ RLS-Sicherheitsaudit: Event-Isolation verifiziert (Daten nur für Mitglieder sichtbar)
- ✅ Settlement-Neuberechnung: Erhält bestehende Zahlungshistorie bei Neuberechnung
- ✅ 52 hartcodierte deutsche Strings in 8 Dateien durch i18n-Aufrufe ersetzt
- ✅ E2E-Testsuite (48 Tests, alle bestanden)

### Middleware-Warnung
Next.js 16 zeigt eine Deprecation-Warnung für `middleware.ts` zugunsten des neuen `proxy`-Konzepts. Die Funktionalität ist aber uneingeschränkt gegeben. Migration auf `proxy` für v2 empfohlen.

### Supabase Session-Refresh
Die Middleware refresht aktuell keine Supabase-Sessions. Für Produktionsbetrieb sollte Session-Refresh in die Middleware integriert werden.

---

## 8. Deployment-Architektur (Local ↔ Production)

**Architekturprinzip:** Lokale Entwicklung und Produktion sind strikt getrennt — keine Interferenz.

### Lokale Entwicklung
- `.env.local` zeigt auf Docker-Supabase (`127.0.0.1:54351/54352`)
- Alle Schema-Änderungen werden als Migrations in `supabase/migrations/` gespeichert
- Testdaten leben ausschließlich in der lokalen DB

### Produktion (Vercel + gehostetes Supabase)
- **Vercel-Domain:** `meinezielcollage.vercel.app`
- **Supabase-Projekt:** `pkvbtwwdjwrxbzmcttpw` (`https://pkvbtwwdjwrxbzmcttpw.supabase.co`)
- Migrationen werden explizit via `npx supabase db push` auf die gehostete DB deployed
- Supabase CLI ist gelinkt via `npx supabase link --project-ref pkvbtwwdjwrxbzmcttpw`

### Vercel Environment Variables (im Vercel Dashboard setzen)

| Variable | Wert | Scope |
|---|---|---|
| `NEXT_PUBLIC_APP_URL` | `https://meinezielcollage.vercel.app` | Production |
| `NEXT_PUBLIC_SUPABASE_URL` | `https://pkvbtwwdjwrxbzmcttpw.supabase.co` | Production |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | `eyJhbGciOi...9go` (anon key) | Production |
| `SUPABASE_SERVICE_ROLE_KEY` | `eyJhbGciOi...NI0` (service role) | Production |
| `SUPABASE_DB_SCHEMA` | `public` | Production |
| `URL_ENCRYPTION_KEY` | *(eigenen 32-Zeichen Hex-Key generieren!)* | Production |

### Supabase Dashboard — Auth-Konfiguration

Im Supabase Dashboard unter **Authentication → URL Configuration**:
- **Site URL:** `https://meinezielcollage.vercel.app`
- **Redirect URLs:** `https://meinezielcollage.vercel.app/**`

---

## 8. Projektstruktur

```
src/
├── app/
│   ├── [locale]/
│   │   ├── page.tsx              # Homepage
│   │   ├── layout.tsx            # Root-Layout (i18n, Theme, Header/Footer)
│   │   ├── login/page.tsx        # Login
│   │   ├── register/page.tsx     # Registrierung
│   │   ├── dashboard/page.tsx    # Dashboard (auth-geschützt)
│   │   ├── profile/page.tsx      # Profil bearbeiten
│   │   ├── events/
│   │   │   ├── new/page.tsx      # Event erstellen
│   │   │   └── [id]/
│   │   │       ├── page.tsx      # Event-Detail
│   │   │       └── edit/page.tsx  # Event bearbeiten
│   │   ├── invite/[token]/page.tsx # Gast-Einladung
│   │   ├── impressum/page.tsx    # Impressum
│   │   ├── datenschutz/page.tsx  # Datenschutzerklärung
│   │   └── agb/page.tsx          # AGB
│   ├── auth/callback/route.ts    # Auth-Callback
│   ├── layout.tsx                # Root-Shell
│   └── page.tsx                  # Redirect → /de
├── components/
│   ├── dashboard/
│   │   └── dashboard-content.tsx
│   ├── events/
│   │   ├── event-detail-content.tsx
│   │   ├── members-section.tsx
│   │   ├── date-poll-section.tsx
│   │   ├── location-poll-section.tsx
│   │   ├── tasks-section.tsx
│   │   ├── budget-section.tsx
│   │   ├── invite-section.tsx
│   │   ├── invite-content.tsx
│   │   └── event-edit-form.tsx
│   ├── layout/
│   │   ├── header.tsx
│   │   └── footer.tsx
│   ├── notifications/
│   │   └── notification-bell.tsx
│   ├── profile/
│   │   └── profile-form.tsx
│   ├── theme-provider.tsx
│   └── ui/
│       ├── logo.tsx
│       └── language-dropdown.tsx
├── hooks/
│   ├── use-permissions.ts
│   └── use-realtime-notifications.ts
├── i18n/
│   ├── routing.ts
│   ├── request.ts
│   └── navigation.ts
├── lib/
│   ├── permissions.ts
│   ├── types.ts
│   ├── url-cipher.ts
│   └── supabase/
│       ├── client.ts
│       └── server.ts
└── middleware.ts
messages/
├── de.json
└── en.json
supabase/
├── config.toml
├── seed.sql
└── migrations/
    ├── 20260506120000_initial_schema.sql
    ├── 20260506130000_fix_rls_recursion.sql
    ├── 20260507120000_notification_triggers.sql
    ├── 20260508120000_add_partial_payments.sql
    ├── 20260509120000_avatars_and_realtime.sql
    └── 20260510120000_co_organizer_permissions.sql
```

## ./legal-docs/agb.md
# Allgemeine Geschäftsbedingungen (AGB)

Stand: {{MONAT}} {{JAHR}}

## § 1 Geltungsbereich

(1) Diese Allgemeinen Geschäftsbedingungen (nachfolgend „AGB") der WAMOCON GmbH, Mergenthalerallee 79 - 81, 65760 Eschborn (nachfolgend „Anbieter"), gelten für alle Verträge über die Nutzung der Software-as-a-Service-Plattform {{PROJEKTNAME}} (nachfolgend „Plattform"), die über die Website {{DOMAIN}} bereitgestellt wird.

(2) Die Plattform richtet sich an Unternehmen und gewerbliche Nutzer (nachfolgend „Auftraggeber") sowie deren Benutzer (nachfolgend „Nutzer"). Es handelt sich um ein B2B-Angebot. Verbraucher im Sinne des § 13 BGB sind nicht Zielgruppe dieses Angebots.

(3) Abweichende, entgegenstehende oder ergänzende AGB des Auftraggebers werden nicht Vertragsbestandteil, es sei denn, der Anbieter stimmt deren Geltung ausdrücklich schriftlich zu.

## § 2 Vertragsschluss

(1) Die Darstellung der Plattform und ihrer Funktionen auf der Website stellt kein verbindliches Angebot im Sinne des § 145 BGB dar, sondern eine Aufforderung zur Abgabe eines Angebots (invitatio ad offerendum).

(2) Der Auftraggeber gibt ein verbindliches Angebot zum Abschluss eines Nutzungsvertrages ab, indem er den Registrierungsprozess auf der Plattform abschließt und diese AGB akzeptiert.

(3) Der Vertrag kommt zustande, wenn der Anbieter das Angebot des Auftraggebers durch Freischaltung des Zugangs annimmt.

## § 3 Leistungsbeschreibung

(1) Der Anbieter stellt dem Auftraggeber die Plattform als Software-as-a-Service (SaaS) über das Internet zur Verfügung.

(2) Der genaue Funktionsumfang ergibt sich aus der jeweils aktuellen Leistungsbeschreibung auf der Website.

(3) Der Anbieter ist berechtigt, die Plattform weiterzuentwickeln, zu erweitern und anzupassen. Wesentliche Einschränkungen des Funktionsumfangs werden dem Auftraggeber vorab mitgeteilt.

## § 4 Nutzungsrechte

(1) Der Anbieter räumt dem Auftraggeber für die Vertragslaufzeit ein einfaches, nicht übertragbares, nicht unterlizenzierbares Recht zur Nutzung der Plattform ein.

(2) Der Auftraggeber darf die Plattform nur für eigene betriebliche Zwecke nutzen.

## § 5 Pflichten des Auftraggebers

(1) Der Auftraggeber ist verpflichtet, seine Zugangsdaten geheim zu halten und vor dem Zugriff Dritter zu schützen.

(2) Der Auftraggeber stellt sicher, dass die Nutzung der Plattform im Einklang mit geltendem Recht erfolgt.

## § 6 Verfügbarkeit

(1) Der Anbieter bemüht sich um eine Verfügbarkeit der Plattform von 99,5 % im Jahresmittel.

(2) Nicht als Ausfallzeit gelten geplante Wartungsarbeiten, die vorab angekündigt werden.

## § 7 Datenschutz

Die Verarbeitung personenbezogener Daten erfolgt gemäß der Datenschutzerklärung des Anbieters und den Bestimmungen der DSGVO.

## § 8 Haftung

(1) Der Anbieter haftet unbeschränkt für Schäden aus der Verletzung des Lebens, des Körpers oder der Gesundheit sowie bei Vorsatz und grober Fahrlässigkeit.

(2) Im Übrigen ist die Haftung auf den vertragstypischen, vorhersehbaren Schaden begrenzt.

## § 9 Vertragslaufzeit und Kündigung

(1) Der Vertrag wird auf unbestimmte Zeit geschlossen und kann von beiden Parteien mit einer Frist von einem Monat zum Monatsende gekündigt werden.

(2) Das Recht zur außerordentlichen Kündigung aus wichtigem Grund bleibt unberührt.

## § 10 Schlussbestimmungen

(1) Es gilt das Recht der Bundesrepublik Deutschland unter Ausschluss des UN-Kaufrechts.

(2) Gerichtsstand ist Eschborn, sofern der Auftraggeber Kaufmann ist.

(3) Sollten einzelne Bestimmungen dieser AGB unwirksam sein, bleibt die Wirksamkeit der übrigen Bestimmungen davon unberührt.

---

> **Hinweis:** Dies ist ein Muster. Ersetze alle `{{PLATZHALTER}}` mit den projektspezifischen Informationen. Lass die AGB vor Veröffentlichung von einem Juristen prüfen.

## ./legal-docs/company-stamp.md
# Firmenstempel / Company Stamp

## Deutsch

### WAMOCON GmbH

**Geschäftsführer:** Dipl.-Ing. Waleri Moretz

**Anschrift:**
Mergenthalerallee 79 - 81
65760 Eschborn
Deutschland

**Kontakt:**
Telefon: +49 6196 5838311
E-Mail: info@wamocon.com

**Registrierung:**
Handelsregister: Eschborn HRB 123666
USt-IdNr.: DE344930486

---

## English

### WAMOCON GmbH

**Managing Director:** Dipl.-Ing. Waleri Moretz

**Address:**
Mergenthalerallee 79 - 81
65760 Eschborn
Germany

**Contact:**
Phone: +49 6196 5838311
Email: info@wamocon.com

**Registration:**
Commercial Register: Eschborn HRB 123666
VAT ID: DE344930486

## ./legal-docs/datenschutzerklaerung.md
# Datenschutzerklärung

Stand: {{MONAT}} {{JAHR}}

## 1. Verantwortlicher

Verantwortlicher im Sinne der Datenschutz-Grundverordnung (DSGVO) und anderer nationaler Datenschutzgesetze ist:

WAMOCON GmbH
Mergenthalerallee 79 - 81
65760 Eschborn
Telefon: +49 6196 5838311
E-Mail: info@wamocon.com
Projektkontakt: {{PROJEKT_EMAIL}}
Geschäftsführer: Dipl.-Ing. Waleri Moretz
Handelsregister: Eschborn HRB 123666
USt-ID: DE344930486

## 2. Überblick über die Datenverarbeitung

Diese Datenschutzerklärung gilt für die Website und Webanwendung {{PROJEKTNAME}} ({{DOMAIN}}).

Wir verarbeiten personenbezogene Daten unserer Nutzer grundsätzlich nur, soweit dies zur Bereitstellung einer funktionsfähigen Plattform sowie unserer Inhalte und Leistungen erforderlich ist.

## 3. Rechtsgrundlagen der Verarbeitung

- **Einwilligung** – Art. 6 Abs. 1 lit. a DSGVO
- **Vertragserfüllung** – Art. 6 Abs. 1 lit. b DSGVO
- **Rechtliche Verpflichtung** – Art. 6 Abs. 1 lit. c DSGVO
- **Berechtigtes Interesse** – Art. 6 Abs. 1 lit. f DSGVO

## 4. Hosting und Infrastruktur

### Vercel Inc.
Die Website und Webanwendung werden über Vercel gehostet. Dabei verarbeitet Vercel technisch notwendige Verbindungsdaten (IP-Adresse, Zeitstempel, Browserinformationen). Rechtsgrundlage: Art. 6 Abs. 1 lit. f DSGVO.

### Supabase Inc.
Für Datenbank, Authentifizierung, Dateispeicher und Teile der Backend-Infrastruktur nutzen wir Supabase. Verarbeitet werden Authentifizierungsdaten, Session-Informationen, Projektdaten sowie gespeicherte Medien. Rechtsgrundlage: Art. 6 Abs. 1 lit. b DSGVO.

## 5. Erhebung personenbezogener Daten

### Registrierung und Nutzerkonto
Bei der Registrierung erheben wir: Name, E-Mail-Adresse und Passwort. Diese Daten sind zur Vertragserfüllung erforderlich (Art. 6 Abs. 1 lit. b DSGVO).

### Server-Logfiles
Bei jedem Zugriff auf unsere Plattform werden automatisch folgende Daten erfasst: IP-Adresse, Datum und Uhrzeit, aufgerufene Seite, Referrer-URL, Browser-Typ und -Version. Rechtsgrundlage: Art. 6 Abs. 1 lit. f DSGVO.

## 6. Cookies und Tracking

Die Plattform verwendet technisch notwendige Cookies für Session-Management und Authentifizierung. Rechtsgrundlage: Art. 6 Abs. 1 lit. f DSGVO.

## 7. Rechte der betroffenen Personen

Sie haben das Recht auf:
- **Auskunft** (Art. 15 DSGVO)
- **Berichtigung** (Art. 16 DSGVO)
- **Löschung** (Art. 17 DSGVO)
- **Einschränkung der Verarbeitung** (Art. 18 DSGVO)
- **Datenübertragbarkeit** (Art. 20 DSGVO)
- **Widerspruch** (Art. 21 DSGVO)
- **Widerruf** erteilter Einwilligungen (Art. 7 Abs. 3 DSGVO)
- **Beschwerde** bei einer Aufsichtsbehörde (Art. 77 DSGVO)

## 8. Datensicherheit

Wir setzen technische und organisatorische Sicherheitsmaßnahmen nach dem Stand der Technik ein, um Ihre Daten gegen zufällige oder vorsätzliche Manipulation, Verlust, Zerstörung oder den Zugriff unberechtigter Personen zu schützen.

## 9. Änderung der Datenschutzerklärung

Wir behalten uns vor, diese Datenschutzerklärung anzupassen, um sie an geänderte Rechtslagen oder bei Änderungen der Plattform anzupassen.

---

> **Hinweis:** Dies ist ein Muster. Ersetze alle `{{PLATZHALTER}}` mit den projektspezifischen Informationen. Lass die Datenschutzerklärung vor Veröffentlichung von einem Juristen prüfen.

## ./legal-docs/impressum.md
# Impressum

Stand: {{MONAT}} {{JAHR}}

## WAMOCON GmbH

Mergenthalerallee 79 - 81
65760 Eschborn
Deutschland

## Kontakt

Telefon: +49 6196 5838311
E-Mail: info@wamocon.com
Projektkontakt: {{PROJEKT_EMAIL}}

## Vertretungsberechtigter Geschäftsführer

Dipl.-Ing. Waleri Moretz

## Registereintrag

Sitz der Gesellschaft: Eschborn
Handelsregister: Eschborn HRB 123666
Umsatzsteuer-Identifikationsnummer: DE344930486

## Angaben zum Angebot

{{PROJEKTNAME}} ist eine webbasierte Software-as-a-Service-Plattform für {{BESCHREIBUNG_DES_ANGEBOTS}}. Das Angebot richtet sich primär an Unternehmen und gewerbliche Nutzer.

---

> **Hinweis:** Ersetze alle `{{PLATZHALTER}}` mit den projektspezifischen Informationen.

## ./legal-docs/imprint.md
# Imprint (Legal Notice)

As of: {{MONTH}} {{YEAR}}

## WAMOCON GmbH

Mergenthalerallee 79 - 81
65760 Eschborn
Germany

## Contact

Phone: +49 6196 5838311
Email: info@wamocon.com
Project Contact: {{PROJECT_EMAIL}}

## Authorized Managing Director

Dipl.-Ing. Waleri Moretz

## Registration

Registered Office: Eschborn
Commercial Register: Eschborn HRB 123666
VAT Identification Number: DE344930486

## About the Service

{{PROJECT_NAME}} is a web-based Software-as-a-Service platform for {{SERVICE_DESCRIPTION}}. The service is primarily aimed at businesses and commercial users.

---

> **Note:** Replace all `{{PLACEHOLDERS}}` with your project-specific information.

## ./legal-docs/privacy-policy.md
# Privacy Policy

As of: {{MONTH}} {{YEAR}}

## 1. Data Controller

The Data Controller as defined by the General Data Protection Regulation (GDPR) is:

WAMOCON GmbH
Mergenthalerallee 79 - 81
65760 Eschborn, Germany
Phone: +49 6196 5838311
Email: info@wamocon.com
Project Contact: {{PROJECT_EMAIL}}
Managing Director: Dipl.-Ing. Waleri Moretz
Commercial Register: Eschborn HRB 123666
VAT ID: DE344930486

## 2. Overview of Data Processing

This Privacy Policy applies to the website and web application {{PROJECT_NAME}} ({{DOMAIN}}).

We process personal data of our users only insofar as this is necessary to provide a functional platform and our content and services.

## 3. Legal Basis for Processing

- **Consent** – Art. 6(1)(a) GDPR
- **Performance of Contract** – Art. 6(1)(b) GDPR
- **Legal Obligation** – Art. 6(1)(c) GDPR
- **Legitimate Interest** – Art. 6(1)(f) GDPR

## 4. Hosting and Infrastructure

### Vercel Inc.
The website and web application are hosted via Vercel. Vercel processes technically necessary connection data (IP address, timestamp, browser information). Legal basis: Art. 6(1)(f) GDPR.

### Supabase Inc.
We use Supabase for database, authentication, file storage, and parts of the backend infrastructure. Authentication data, session information, project data, and stored media are processed. Legal basis: Art. 6(1)(b) GDPR.

## 5. Collection of Personal Data

### Registration and User Account
During registration we collect: name, email address, and password. This data is necessary for the performance of the contract (Art. 6(1)(b) GDPR).

### Server Log Files
Each access to our platform automatically records: IP address, date and time, page accessed, referrer URL, browser type and version. Legal basis: Art. 6(1)(f) GDPR.

## 6. Cookies and Tracking

The platform uses technically necessary cookies for session management and authentication. Legal basis: Art. 6(1)(f) GDPR.

## 7. Rights of Data Subjects

You have the right to:
- **Access** (Art. 15 GDPR)
- **Rectification** (Art. 16 GDPR)
- **Erasure** (Art. 17 GDPR)
- **Restriction of processing** (Art. 18 GDPR)
- **Data portability** (Art. 20 GDPR)
- **Object** (Art. 21 GDPR)
- **Withdraw consent** (Art. 7(3) GDPR)
- **Lodge a complaint** with a supervisory authority (Art. 77 GDPR)

## 8. Data Security

We employ state-of-the-art technical and organisational security measures to protect your data against accidental or intentional manipulation, loss, destruction, or access by unauthorised persons.

## 9. Changes to this Privacy Policy

We reserve the right to amend this Privacy Policy to reflect changes in the law or changes to the platform.

---

> **Note:** This is a template. Replace all `{{PLACEHOLDERS}}` with your project-specific information. Have the Privacy Policy reviewed by a lawyer before publication.

## ./legal-docs/terms-and-conditions.md
# Terms and Conditions

As of: {{MONTH}} {{YEAR}}

## § 1 Scope

(1) These Terms and Conditions (hereinafter "T&C") of WAMOCON GmbH, Mergenthalerallee 79 - 81, 65760 Eschborn (hereinafter "Provider"), apply to all contracts for the use of the Software-as-a-Service platform {{PROJECT_NAME}} (hereinafter "Platform"), provided via the website {{DOMAIN}}.

(2) The Platform is aimed at businesses and commercial users (hereinafter "Client") and their respective users (hereinafter "Users"). This is a B2B offering. Consumers within the meaning of § 13 BGB (German Civil Code) are not the target audience.

(3) Deviating, conflicting, or supplementary terms and conditions of the Client shall not become part of the contract unless the Provider expressly agrees in writing.

## § 2 Conclusion of Contract

(1) The presentation of the Platform and its features on the website does not constitute a binding offer within the meaning of § 145 BGB, but rather an invitation to submit an offer (invitatio ad offerendum).

(2) The Client submits a binding offer by completing the registration process on the Platform and accepting these T&C.

(3) The contract is concluded when the Provider accepts the Client's offer by activating access.

## § 3 Service Description

(1) The Provider makes the Platform available to the Client as Software-as-a-Service (SaaS) via the Internet.

(2) The precise scope of features is set out in the current service description on the website.

(3) The Provider is entitled to further develop, expand, and adapt the Platform. Material restrictions to the scope of features will be communicated to the Client in advance.

## § 4 Usage Rights

(1) The Provider grants the Client a simple, non-transferable, non-sublicensable right to use the Platform for the duration of the contract.

(2) The Client may only use the Platform for its own business purposes.

## § 5 Client Obligations

(1) The Client shall keep its access credentials confidential and protect them from third-party access.

(2) The Client shall ensure that use of the Platform complies with applicable law.

## § 6 Availability

(1) The Provider shall endeavour to maintain an annual average availability of 99.5%.

(2) Scheduled maintenance windows announced in advance shall not count as downtime.

## § 7 Data Protection

The processing of personal data is governed by the Provider's Privacy Policy and the provisions of the GDPR.

## § 8 Liability

(1) The Provider shall be fully liable for damages arising from injury to life, body, or health, as well as for intent and gross negligence.

(2) Otherwise, liability is limited to foreseeable, typically occurring damages.

## § 9 Contract Duration and Termination

(1) The contract is concluded for an indefinite period and may be terminated by either party with one month's notice to the end of a calendar month.

(2) The right to extraordinary termination for good cause remains unaffected.

## § 10 Final Provisions

(1) The law of the Federal Republic of Germany shall apply, excluding the UN Convention on Contracts for the International Sale of Goods.

(2) The place of jurisdiction is Eschborn, provided the Client is a merchant.

(3) Should individual provisions of these T&C be invalid, the validity of the remaining provisions shall remain unaffected.

---

> **Note:** This is a template. Replace all `{{PLACEHOLDERS}}` with your project-specific information. Have the T&C reviewed by a lawyer before publication.

## package.json
{
  "name": "template_repo",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev --turbopack",
    "build": "next build",
    "start": "next start",
    "lint": "eslint .",
    "lint:fix": "eslint . --fix",
    "typecheck": "tsc --noEmit",
    "verify": "npm run typecheck && npm run lint && npm run build",
    "gen:anforderungsdokument": "node scripts/generate-anforderungsdokument.mjs",
    "gen:manual": "node scripts/generate-user-manual.mjs",
    "test:e2e": "node tests/e2e.mjs"
  },
  "dependencies": {
    "@supabase/ssr": "^0.10.2",
    "@supabase/supabase-js": "^2.105.3",
    "docx": "^9.6.1",
    "lucide-react": "^1.14.0",
    "next": "16.2.1",
    "next-intl": "^4.11.0",
    "next-themes": "^0.4.6",
    "pdfkit": "^0.18.0",
    "react": "19.2.4",
    "react-dom": "19.2.4",
    "resend": "^6.12.3"
  },
  "devDependencies": {
    "@tailwindcss/postcss": "^4",
    "@types/node": "^20",
    "@types/react": "^19",
    "@types/react-dom": "^19",
    "eslint": "^9",
    "eslint-config-next": "16.2.1",
    "tailwindcss": "^4",
    "typescript": "^5"
  }
}

