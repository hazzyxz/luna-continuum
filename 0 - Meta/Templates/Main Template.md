<%*
/* ---------- Prompts ---------- */
const title = await tp.system.prompt("Note title");
const typeOptions = ["Project","Area","Resource","Archive","General Note"];
const statusOptions = ["Idea","Draft","Active","Archived"];
const status = await tp.system.suggester(statusOptions, statusOptions) ?? "Draft";
const noteType = await tp.system.suggester(typeOptions, typeOptions) ?? "General Note";

const tagInput = await tp.system.prompt("Tags (comma-separated, with or without #)", "notes, research") ?? "";
const tags = tagInput.split(",").map(t => t.trim().replace(/^#/, "")).filter(Boolean);
const tagsYaml = tags.map(t => `"${t}"`).join(", ");
-%>
---
title: "<% title %>"
type: "<% noteType %>"        # PARA category
status: "<% status %>"        # Idea | Draft | Active | Archived
created: "<% tp.file.creation_date('YYYY-MM-DD HH:mm') %>"
updated: "<% tp.date.now('YYYY-MM-DD HH:mm') %>"
tags: [<% tagsYaml %>]
---

# <% title %>

> **Summary** — one sentence on what this note is for.

## Context
- 

## Objectives / Outcomes
- 

## Key Points
- 

## Decisions
- 

## Open Questions
- 

## Tasks
- [ ] 

## Notes
- 

## Links & Assets
- 

---

## References
- 