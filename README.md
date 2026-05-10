---
title: Meeting Notes
date: 2026-05-10
tags:
  - meeting
aliases:
  - Meetings
  - Meeting Notes
---
# Meeting Notes

Human dashboard for the meeting-note vault. Write raw notes only in [[QuickNote]].

## Quick Start

```text
Organize QuickNote.md.
```

Use this after filling out [[QuickNote]]. The assistant will create the organized meeting note, update [[ToDo]], add the note to the index below, and reset [[QuickNote]].

```text
Clean Todo.md.
```

Use this after checking or unchecking tasks in [[ToDo]]. The assistant will move checked tasks to Done and move unchecked Done tasks back to the correct active lane.

## Active Pages

- [[QuickNote|Quick Note Input]]
- [[ToDo|Todo Board]]

## Meeting Index

### QE

No notes yet.

### HGTD

- [[Meetings/HGTD/05-04-2026 nthu-hgtd|05-04-2026 nthu-hgtd]]
- [[Meetings/HGTD/04-27-2026 nthu-hgtd|04-27-2026 nthu-hgtd]]

### Run 3 Coupling

No notes yet.

### Students

No notes yet.

## Daily Workflow

1. Open [[QuickNote]].
2. Fill in `Date::` using `MM-DD-YYYY`.
3. Fill in `Type::` using one exact value from [[#Meeting Types]].
4. Add optional `Links::`.
5. Write rough bullet notes under `Raw notes:`.
6. Mark tasks with `#urgent`, `#scheduled`, `#todo`, or `#later`.
7. Ask the assistant: `Organize QuickNote.md.`

## Task Markers

| Marker | Meaning | Goes To |
|---|---|---|
| `#urgent` | urgent, blocker, deadline, action stop | [[ToDo#Now]] |
| `#scheduled` | deadline task; must include `Due: MM-DD-YYYY Time:` | [[ToDo#Scheduled]] |
| `#todo` | normal follow-up task | [[ToDo#Next]] |
| `#later` | unclear, future, maybe, background work | [[ToDo#Later]] |

If a task sounds urgent even without `#urgent`, it still goes to [[ToDo#Now]].

If a task has a clear deadline, it goes to [[ToDo#Scheduled]] and should keep `Due: MM-DD-YYYY Time:`. Leave `Time:` blank if only the date is known.

If a task is unclear, future, maybe, or background work, it goes to [[ToDo#Later]].

## Todo Cleanup

Ask `Clean Todo.md.` after checking or unchecking tasks.

- Checked active tasks move to [[ToDo#Done]].
- Unchecked Done tasks move back to the matching active lane.
- Task marker decides the active lane: `#urgent` -> Now, `#scheduled` -> Scheduled, `#todo` -> Next, `#later` -> Later.
- Meeting type and source-date subsections are preserved.

## Meeting Types

Use these exact values for `Type::` in [[QuickNote]] and `meeting_type` in final notes:

- `nthu-qe`
- `nthu-hgtd`
- `nthu-run3coupling`
- `qe`
- `hgtd`
- `students`

Broad categories:

| Exact Type | Category Folder |
|---|---|
| `nthu-qe`, `qe` | `Meetings/QE/` |
| `nthu-hgtd`, `hgtd` | `Meetings/HGTD/` |
| `nthu-run3coupling` | `Meetings/Run 3 Coupling/` |
| `students` | `Meetings/Students/` |

## File Rules

Final notes use this path:

```text
Meetings/CATEGORY/MM-DD-YYYY Meeting Type.md
```

Examples:

```text
Meetings/QE/05-12-2026 nthu-qe.md
Meetings/HGTD/05-12-2026 nthu-hgtd.md
Meetings/HGTD/05-12-2026 hgtd.md
```

Use path-aware wikilinks with clean aliases when linking to final notes, e.g. `[[Meetings/HGTD/05-04-2026 nthu-hgtd|05-04-2026 nthu-hgtd]]`.
