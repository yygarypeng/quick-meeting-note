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

## Universal User Preferences

- Preserve LaTeX/math notation exactly as LaTeX when cleaning notes and todos. Keep inline `$...$`, display `$$...$$`, commands such as `\bar{t}`, subscripts, and superscripts; do not convert math snippets to inline code or wrap them in backticks.

## Active Files

- `README.md` is the human manual/dashboard page, not a note capture area.
- `QuickNote.md` is the only raw note input area; the user should only need to fill `Date::`, `Type::`, optional `Links::`, and `Raw notes:`.
- `ToDo.md` is the only central todo list.
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
> ```text
> Date:: MM-DD-YYYY
> Type:: meeting-type
> Links:: 
>
> Raw notes:
>
> - original bullet
> ```
```

Tasks belong in `ToDo.md`; do not add active task sections to final meeting notes.

## Raw Note Cleanup

When the user asks to organize a messy meeting note:

1. Treat `QuickNote.md` as the source; do not ask the user to manually create meeting or todo files.
2. Require both `Date::` and `Type::`; if either is blank or invalid, ask before creating files.
3. Clean it into an Obsidian meeting note with sections: `Summary`, `Notes`, `Decisions`, `Questions`, `Links`, and collapsed `Raw Quick Note`.
4. Preserve technical details, code names, function names, commands, file names, and exact error messages.
5. Move tasks into `ToDo.md`; do not leave final tasks only in the meeting note and do not copy raw task blocks into active final-note sections.
6. Add a path-aware source link to every todo item, e.g. `Source: [[Meetings/HGTD/MM-DD-YYYY nthu-hgtd|MM-DD-YYYY nthu-hgtd]]`.
7. If meaning is unclear, put it in `Questions` instead of guessing.
8. Add the final note link to `README.md` under the matching category.
9. After creating the meeting note and updating `ToDo.md`, reset `QuickNote.md` to the blank reset block.

Preserve the full original `QuickNote.md` content at the end of the final meeting note under:

```markdown
## Raw Quick Note

> [!quote]- Original Quick Note
> ```text
> Date:: MM-DD-YYYY
> Type:: meeting-type
> Links:: 
>
> Raw notes:
>
> - original bullet
> ```
```

The raw section is archive-only; tasks inside it must still be moved to `ToDo.md`. Store the original raw text inside a fenced `text` block within the callout so archived hashtags do not become live vault tags.

## Todo Classification

Classify tasks into `ToDo.md` using:

| Task Signal | Todo Callout |
|---|---|
| `#urgent` or sounds urgent/blocking/action stop | `[!danger] #urgent` |
| clear date or explicit non-urgent deadline | `[!warning] Scheduled` |
| `#todo` | `[!todo] #todo` |
| `#later` or unclear/future/maybe/background | `[!quote] #later` |

Keep the original marker on the final todo item.

Route active tasks into broad area sections using the same category mapping as `README.md`; do not split `nthu-*` and non-`nthu-*` exact types into separate active sections:

| Exact Type | Todo Area Section |
|---|---|
| `nthu-qe`, `qe` | `QE` |
| `nthu-hgtd`, `hgtd` | `HGTD` |
| `nthu-run3coupling` | `Run 3 Coupling` |
| `students` | `Students` |

For scheduled tasks, preserve clear dates as `Due: MM-DD-YYYY`. If a time is explicitly known, append it after the date, e.g. `Due: MM-DD-YYYY 14:00`. Do not create a separate time field. If the deadline is vague, keep the original wording and put the ambiguity in `Questions`.

Group active tasks under broad area sections, then colored hashtag/status callouts, then source-date subsections, e.g. `## HGTD` > `> [!todo] #todo` > `> #### 05-04-2026`.

Use built-in Obsidian callouts for marker colors: `#urgent` uses `[!danger]`, `Scheduled` uses `[!warning]`, `#todo` uses `[!todo]`, `#later` uses `[!quote]`, and collapsed `Done` uses `[!success]-`. Do not use separate `Now`, `Scheduled`, `Next`, or `Later` top-level board-lane sections; the broad area is the top-level active-task section.

When the user asks to clean `ToDo.md`, move checked active tasks (`- [x]`) into `## Done`; move unchecked Done tasks (`- [ ]`) back to the matching broad area section and colored callout based on marker and dates. Preserve source date, source links, exact meeting type in source links, and `Due: MM-DD-YYYY` fields.

Move completed or cancelled checked tasks (`- [x]`) into `## Done`, grouped by broad area and source date inside a collapsed Obsidian callout:

```markdown
> [!success]- Done
> Completed or cancelled tasks are archived here by broad area and source date.
> ### HGTD
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

- always keep the structure coherent and correlated. Make sure the cleanness, and organizations.
