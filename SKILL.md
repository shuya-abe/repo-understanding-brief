---
name: repo-understanding-brief
description: "Understand a Git repo for job interviews, research onboarding, or handoff. Extract what to explain: inputs, environment, outputs, architecture, ownership vs AI, failures. For each tech, say what it is generally and its role in this repo."
---
# Repo understanding brief

Produce a structured **text** brief so a human can **explain and operate** a repository without memorizing every framework detail. Works for **own projects** (job-hunt / portfolio) and **third-party repos** (research / dependency onboarding).

## Design principles

- Prefer **inputs → environment → outputs → failure modes** over API laundry lists.
- Separate **must explain orally** vs **lookup-when-needed**.
- Assume AI may have written much of the code; still identify what a human must own.
- **LLM-capability independent**: the deliverable is structured markdown prose. Do **not** require diagrams, ponti pictures, slide layouts, or infographics. Optional mermaid is fine only when it clarifies a short data-flow; never block on visuals. Glossaries and pretty one-pagers are out of scope unless the user asks—they can derive those from the brief themselves.
- **Beginner-readable stack notes**: for important technologies, always pair (1) what it is in general with (2) what role it plays in *this* repository. Do not assume the reader already knows the name.

## Inputs to gather (ask only if missing)

1. Repo path or `owner/name` (GitHub URL OK).
2. Mode: `job-hunt` | `research-use` | `general`.
3. Audience language: default Japanese (です・ます調) unless asked otherwise.
4. Optional focus: one feature, one service, or "whole repo".

## Procedure

### 1. Map the repo (read, don't guess)

- List top-level layout; read `README`, `LICENSE`, package manifests (`package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, `Dockerfile`, `compose*.yml`, `.env.example`, CI workflows).
- Identify entrypoints (CLI, web server, notebooks, scripts, browser extension, etc.).
- Note secrets patterns; **never** paste secrets into the brief.
- If the tree is huge, sample: manifests → entrypoints → config → one vertical slice of the main path.
- For remote GitHub URLs, clone or fetch README + key paths rather than inventing structure.

### 2. Fill the brief template

Write a single markdown document with these sections (omit G or H when the mode does not need them).

#### A. One-paragraph pitch
What it is, who it's for, what "done" looks like.

#### B. Runtime contract (highest priority)
| | |
|---|---|
| Inputs | files, APIs, user actions, sensors, env vars |
| Environment | OS, runtime versions, GPU/CPU, network, accounts |
| Outputs | UI, files, APIs, logs, side effects |
| Invariants | what must stay true |

#### C. Architecture sketch
- Major modules and data flow (short bullets; mermaid optional, not required).
- External services and why each exists.
- **Do not** dump every library; group by role (UI / API / data / infra / extract / export / …).

#### D. Stack: must-explain vs lookup (write for beginners)

For **each** must-explain item and each lookup-table row, use this shape:

1. **一般** — what this kind of thing does in software generally (one or two sentences; no jargon-only labels).
2. **このリポジトリ** — the concrete role / files / design choice here.
3. **口頭の要点** (must-explain only) — one sentence a candidate could say aloud.

**Must explain** = needed to debug or extend the main path (e.g. request pipeline, auth boundary, why not "save raw HTML").
**Lookup OK** = framework trivia, exact option names, vendor bundlers, generated boilerplate—still give 一般 + このリポジトリ, but mark as non-memorization.

Do not stop at names like "MV3" or "jsdom" without the 一般／このリポジトリ pair.

#### E. Ownership map (especially job-hunt)
- Likely **human decisions**: problem framing, constraints, UX, data model, security boundaries, ops conventions.
- Likely **AI-assisted / generated**: boilerplate UI, glue, repetitive tests.
- Evidence from commits/README when available; mark speculation clearly. Never invent ownership.

#### F. Operate & debug
- How to run locally (commands from the repo, not invented).
- Top failure symptoms → where to look first (file/service/log).
- Tests or checks that exist; how to know it's healthy.

#### G. Research-use extras (mode `research-use` only)
- What to trust vs re-verify.
- Extension points for the user's experiment.
- Citation / license constraints if relevant.

#### H. Job-hunt extras (mode `job-hunt` only)

Go beyond bare bullets. For each likely interview question:

1. What the interviewer is probing.
2. General engineering rationale (why this class of solution exists).
3. How *this* repo instantiates that rationale (files / invariants).
4. A short **answer bone** (not a scripted speech)—facts only; leave "AI vs me" lines for the user to fill with truth.

Also include:

- What to demo in ~3 minutes (concrete click-path or run steps).
- Gaps before / while public (secrets, empty description, docs vs code drift).
- "When it breaks, where first" mapped to interview language.

#### I. Learning checklist (prioritized, with why)

Three buckets. Each item = skill to gain + why it matters for *this* repo (not a generic CS syllabus).

- **今週** — enough to narrate the main path and debug top failures.
- **流し読み** — know where it lives; no need to memorize APIs.
- **今は無視** — safe to skip for interview / first onboarding.

Optional one-line "学び方のコツ" (read order: README → architecture doc → entrypoint → one fixture/test) is encouraged.

### 3. Quality bar

- Prefer evidence from the repo over generic advice.
- If unknown, say **不明** and how to verify.
- Keep scannable: roughly 1–4 pages equivalent; depth goes into D/H/I explanations, not into dumping source.
- Output as markdown the user can save (e.g. `UNDERSTANDING.md`) when they want a file.
- Do **not** auto-generate a separate glossary, slide, or infographic unless asked.

## Optional tools

- Packing tools (e.g. Repomix) may help for large trees; still verify claims against real files.

## Non-goals

- Full framework tutorials.
- Rewriting the project unless asked.
- Claiming the user "understands" code they cannot run or narrate.
- Mandatory visuals, ponti pictures, slide decks, or glossaries as part of the default brief.
- Outputs that only a strong multimodal / diagram-capable model can produce well.
