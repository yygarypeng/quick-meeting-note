# Vault Instructions

This is an Obsidian vault for meeting notes and central todo tracking, not a code project. There are no build, test, or lint commands.

## Agent Tooling

- Always load the `obsidian-cli` skill and use the `obsidian` CLI for Obsidian vault operations when an equivalent CLI command exists.
- If the `obsidian` CLI is unavailable, Obsidian is not open, or no matching CLI command exists, fall back to filesystem tools and state the fallback.
- Load relevant Obsidian skills before working on matching files or features:
  - `obsidian-markdown` for `.md` notes, wikilinks, callouts, properties, embeds, and tags.
  - `obsidian-bases` for `.base` files and Bases views.
  - `json-canvas` for `.canvas` files and Obsidian Canvas work.
  - `obsidian-cli` for vault reads, writes, search, tasks, tags, backlinks, and live Obsidian checks.

## Active Files

- `README.md` is the human manual/dashboard page, not a note capture area.
- `QuickNote.md` is the only raw note input area; the user should only need to fill `Date::`, `Type::`, optional `Links::`, and `Raw notes:`.
- `Todo.md` is the only central todo list.
- `Meetings/` stores final cleaned meeting notes in broad category folders, e.g. `Meetings/HGTD/`.
- `.obsidian/`, `.agents/`, and `skills-lock.json` are vault/OpenCode config; do not edit them unless explicitly managing that config.

## Meeting Notes

Use `MM-DD-YYYY` dates.

Final meeting notes go in `Meetings/CATEGORY/` and should be named:

```text
Meetings/CATEGORY/MM-DD-YYYY Meeting Type.md
```

Example:

```text
Meetings/HGTD/05-12-2026 nthu-hgtd.md
```

Use path-aware Obsidian wikilinks for internal source links, e.g. `[[Meetings/HGTD/05-12-2026 nthu-hgtd|05-12-2026 nthu-hgtd]]`.

Use only these meeting types:

- `nthu-qe`
- `nthu-hgtd`
- `nthu-run3coupling`
- `qe`
- `hgtd`
- `students`

Final meeting notes should include `meeting_type`, `meeting_category`, and a matching tag, e.g. `meeting_type: nthu-hgtd`, `meeting_category: HGTD`, and `meeting/nthu-hgtd`.

Use the final meeting note structure in this file; there is no separate template folder.

Keep `README.md` indexed by broad category only; do not split `nthu-*` and non-`nthu-*` exact types into separate subsections:

| Exact Type | Meeting Index Category |
|---|---|
| `nthu-qe`, `qe` | `QE` |
| `nthu-hgtd`, `hgtd` | `HGTD` |
| `nthu-run3coupling` | `Run 3 Coupling` |
| `students` | `Students` |

## Final Meeting Note Structure

Final meeting notes must use this structure:

```markdown
---
date: MM-DD-YYYY
meeting_type: meeting-type
meeting_category: CATEGORY
tags:
  - meeting
  - meeting/meeting-type
---

# MM-DD-YYYY meeting-type

## Summary

## Notes

- 

## Decisions

- 

## Questions

- 

## Links

- Indico:
- GitLab:
- CDS:

## Raw Quick Note

> [!quote]- Original Quick Note
> Date:: MM-DD-YYYY
> Type:: meeting-type
> Links:: 
>
> Raw notes:
>
> - original bullet
```

Tasks belong in `Todo.md`; do not add active task sections to final meeting notes.

## Raw Note Cleanup

When the user asks to organize a messy meeting note:

1. Treat `QuickNote.md` as the source; do not ask the user to manually create meeting or todo files.
2. Require both `Date::` and `Type::`; if either is blank or invalid, ask before creating files.
3. Clean it into an Obsidian meeting note with sections: `Summary`, `Notes`, `Decisions`, `Questions`, `Links`, and collapsed `Raw Quick Note`.
4. Preserve technical details, code names, function names, commands, file names, and exact error messages.
5. Move tasks into `Todo.md`; do not leave final tasks only in the meeting note and do not copy raw task blocks into active final-note sections.
6. Add a path-aware source link to every todo item, e.g. `Source: [[Meetings/HGTD/MM-DD-YYYY nthu-hgtd|MM-DD-YYYY nthu-hgtd]]`.
7. If meaning is unclear, put it in `Questions` instead of guessing.
8. Add the final note link to `README.md` under the matching category.
9. After creating the meeting note and updating `Todo.md`, reset `QuickNote.md` to the blank reset block.

Preserve the full original `QuickNote.md` content at the end of the final meeting note under:

```markdown
## Raw Quick Note

> [!quote]- Original Quick Note
> Date:: MM-DD-YYYY
> Type:: meeting-type
> Links:: 
>
> Raw notes:
>
> - original bullet
```

The raw section is archive-only; tasks inside it must still be moved to `Todo.md`.

## Todo Classification

Classify tasks into `Todo.md` using:

| Task Signal | Todo Board Lane |
|---|---|
| `#urgent` or sounds urgent/blocking/action stop | `Now` |
| clear date or explicit non-urgent deadline | `Scheduled` |
| `#todo` | `Next` |
| `#later` or unclear/future/maybe/background | `Later` |

Keep the original marker on the final todo item.

For scheduled tasks, preserve clear dates as `Due: MM-DD-YYYY`. If a time is explicitly known, append it after the date, e.g. `Due: MM-DD-YYYY 14:00`. Do not create a separate time field. If the deadline is vague, keep the original wording and put the ambiguity in `Questions`.

Group active tasks under board lanes, then meeting-type subsections, then source-date subsections, e.g. `## Scheduled` > `### nthu-hgtd` > `#### 05-04-2026`.

Use built-in Obsidian callouts for lane colors: `Now` uses `[!danger]`, `Scheduled` uses `[!warning]`, `Next` uses `[!todo]`, `Later` uses `[!quote]`, and collapsed `Done` uses `[!success]-`.

When the user asks to clean `Todo.md`, move checked active tasks (`- [x]`) into `## Done`; move unchecked Done tasks (`- [ ]`) back to the matching active lane based on marker and dates. Preserve meeting type, source date, source links, and `Due: MM-DD-YYYY` fields.

Move completed or cancelled checked tasks (`- [x]`) into `## Done`, grouped by meeting type and source date inside a collapsed Obsidian callout:

```markdown
> [!success]- Done
> Completed or cancelled tasks are archived here by meeting type and source date.
> ### nthu-hgtd
> #### 05-04-2026
> - [x] #todo Task text. Source: [[Meetings/HGTD/MM-DD-YYYY nthu-hgtd|MM-DD-YYYY nthu-hgtd]]
```

## QuickNote Reset Block

Use this exact block when resetting `QuickNote.md` after cleanup, preserving its frontmatter and `# Quick Note` heading:

```markdown
Date:: MM-DD-YYYY
Type:: 
Links:: 

Raw notes:

- 
```
