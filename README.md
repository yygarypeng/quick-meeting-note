---
title: AI Meeting Notes App
date: 2026-05-11
tags:
  - app
  - obsidian
  - ai-assisted
aliases:
  - Meeting Notes App
  - AI Meeting Notes
---

# AI Meeting Notes App

An Obsidian-based app for turning rough meeting input into structured meeting records, a central task board, and a browsable meeting index.

The app is designed around one clean input surface, one task board, and one indexed meeting archive. AI assistance is provided through OpenCode with GPT-5.5 and task-specific agent skills.

## What It Does

| App Function | Result |
|---|---|
| Capture rough meeting text | Write raw bullets in [[QuickNote]] |
| Clean meeting records | Generate structured notes in `Meetings/` |
| Extract follow-up work | Route tasks into [[ToDo]] |
| Keep meetings browsable | Update the index in this README |
| Preserve provenance | Archive the original quick note in each final meeting record |

## App Flow

```text
QuickNote.md
  -> OpenCode + GPT-5.5 + agent skills
  -> Meetings/CATEGORY/MM-DD-YYYY meeting-type.md
  -> ToDo.md
  -> README.md meeting index
```

The source of truth for raw input is always [[QuickNote]]. The source of truth for active tasks is always [[ToDo]]. Final cleaned records live under `Meetings/`.

## App Structure

| Path | Role |
|---|---|
| [[QuickNote]] | Input screen for raw meeting capture |
| [[ToDo]] | Central task board with active and completed lanes |
| `Meetings/` | Structured meeting archive grouped by category |
| `README.md` | App home, manual, and meeting index |
| `AGENTS.md` | Automation rules for the AI assistant |
| `.agents/skills/` | Local agent skills used by the assistant |
| `skills-lock.json` | Skill source and version lock metadata |

## AI-Assisted Workflow

This app uses an AI-assisted operating model rather than a conventional backend service.

| Layer | Tool | Purpose |
|---|---|---|
| App surface | Obsidian | Editing, linking, browsing, and task review |
| Agent interface | OpenCode | Runs the assistant inside this app workspace |
| Model | GPT-5.5 | Cleans, classifies, and organizes meeting content |
| Skills | Agent Skills | Load task-specific instructions only when needed |
| Rules | `AGENTS.md` | Keeps output consistent across notes, todos, and indexes |

The active workflow is OpenCode with GPT-5.5.

## Setup

Install Obsidian and open this folder as a vault. Keep Obsidian open when using CLI-assisted vault operations.

Install OpenCode:

```bash
curl -fsSL https://opencode.ai/install | bash
```

Useful OpenCode references:

| Resource | URL |
|---|---|
| OpenCode install | <https://opencode.ai/install> |
| OpenCode docs | <https://opencode.ai/docs/> |
| OpenCode agent skills docs | <https://opencode.ai/docs/skills/> |

Run OpenCode from the app folder:

```bash
opencode
```

Then ask it to operate on the app files, for example:

```text
Organize QuickNote.md.
```

## Skills

Agent skills make the app behavior reproducible. They provide structured instructions for Obsidian Markdown, Bases, Canvas files, web cleanup, and planning workflows.

| Skill Source | Used For | Install or Source URL |
|---|---|---|
| Obsidian Skills | Obsidian Markdown, Bases, JSON Canvas, Obsidian CLI, Defuddle | <https://github.com/kepano/obsidian-skills> |
| Superpowers | Brainstorming and planning workflows | <https://github.com/obra/superpowers> |
| Agent Skills spec | Standard skill format | <https://agentskills.io/specification> |

For OpenCode, Obsidian Skills can be installed by cloning the full repository into an OpenCode skills directory:

```bash
git clone https://github.com/kepano/obsidian-skills.git ~/.opencode/skills/obsidian-skills
```

OpenCode auto-discovers `SKILL.md` files under its skill paths after restart. This app also includes project-local skills in `.agents/skills/`.

For Superpowers with OpenCode, follow the upstream OpenCode instructions:

```text
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

## Daily Use

1. Open [[QuickNote]].
2. Fill in `Date::` using `MM-DD-YYYY`.
3. Fill in `Type::` using one exact value from [[#Meeting Types]].
4. Add optional `Links::`.
5. Write rough bullet notes under `Raw notes:`.
6. Mark tasks with `#urgent`, `#todo`, or `#later`.
7. For scheduled work, write the date directly in the task text.
8. Ask OpenCode: `Organize QuickNote.md.`

The assistant will create the organized meeting record, update [[ToDo]], add the record to the index below, and reset [[QuickNote]].

## Todo Cleanup

Ask OpenCode to clean the task board after checking or unchecking tasks:

```text
Clean Todo.md.
```

Cleanup behavior:

- Checked active tasks move to [[ToDo#Done]].
- Unchecked Done tasks move back to the matching active lane.
- Meeting type and source-date subsections are preserved.
- Source links remain attached to todo items.

## Task Routing

| Signal | Meaning | Goes To |
|---|---|---|
| `#urgent` | Urgent, blocking, or action-stopping work | [[ToDo#Now]] |
| Clear date | Scheduled work or explicit deadline | [[ToDo#Scheduled]] |
| `#todo` | Normal follow-up task | [[ToDo#Next]] |
| `#later` | Future, unclear, maybe, or background work | [[ToDo#Later]] |

If a task sounds urgent even without `#urgent`, it still goes to [[ToDo#Now]]. If a task has a clear date, the assistant adds `Due: MM-DD-YYYY`; if a time is written, it is appended after the date.

## Meeting Types

Use these exact values for `Type::` in [[QuickNote]] and `meeting_type` in final records:

- `nthu-qe`
- `nthu-hgtd`
- `nthu-run3coupling`
- `qe`
- `hgtd`
- `students`

Category mapping:

| Exact Type | Category Folder | Index Category |
|---|---|---|
| `nthu-qe`, `qe` | `Meetings/QE/` | QE |
| `nthu-hgtd`, `hgtd` | `Meetings/HGTD/` | HGTD |
| `nthu-run3coupling` | `Meetings/Run 3 Coupling/` | Run 3 Coupling |
| `students` | `Meetings/Students/` | Students |

## File Rules

Final meeting records use this path pattern:

```text
Meetings/CATEGORY/MM-DD-YYYY meeting-type.md
```

Examples:

```text
Meetings/QE/05-12-2026 nthu-qe.md
Meetings/HGTD/05-12-2026 nthu-hgtd.md
Meetings/HGTD/05-12-2026 hgtd.md
```

Use path-aware wikilinks with clean aliases when linking to final records, for example:

```text
[[Meetings/HGTD/05-04-2026 nthu-hgtd|05-04-2026 nthu-hgtd]]
```

## Meeting Index

### QE

- [[Meetings/QE/05-06-2026 qe|05-06-2026 qe]]

### HGTD

- [[Meetings/HGTD/05-05-2026 hgtd|05-05-2026 hgtd]]
- [[Meetings/HGTD/05-04-2026 nthu-hgtd|05-04-2026 nthu-hgtd]]
- [[Meetings/HGTD/04-27-2026 nthu-hgtd|04-27-2026 nthu-hgtd]]

### Run 3 Coupling

- [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]

### Students

- [[Meetings/Students/05-03-2026 students|05-03-2026 students]]

## License

This app documentation and note workflow are licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/).

Third-party tools and skills remain under their own licenses.

<p align="center">
  AI-assisted Obsidian meeting workflow app. Licensed under
  <a href="https://creativecommons.org/licenses/by/4.0/">CC BY 4.0</a>.
</p>
