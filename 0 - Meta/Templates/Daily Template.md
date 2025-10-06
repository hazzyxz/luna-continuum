<%*
/* --- Prompts --- */
const tagInput = await tp.system.prompt(
  "Tags (comma-separated, with or without #)",
  "daily, journal"
) ?? "";

const tags = tagInput
  .split(",")
  .map(t => t.trim().replace(/^#/, ""))
  .filter(Boolean);

const moodOptions = ["1 😫","2 😣","3 😔","4 😕","5 😐","6 🙂","7 😊","8 😄","9 🤩","10 🥳"];
const mood = await tp.system.suggester(moodOptions, moodOptions) ?? "5 😐";
-%>
---
title: "<% tp.file.title || tp.date.now('YYYY-MM-DD') %>"
date: "<% tp.date.now('dddd, DD MMMM YYYY') %>"
time_created: "<% tp.file.creation_date('HH:mm') %>"
mood: "<% mood %>"
tags: [<% tags.join(', ') %>]
---

# <% tp.file.title || tp.date.now("YYYY-MM-DD") %>

## Agenda
- 

## Notes
- 

## Tasks
- [ ] 

## Reflection
- What went well:
- What could be better:
- Next action:

---

## References
- 