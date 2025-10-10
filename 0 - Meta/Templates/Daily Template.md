<%*
/* --- Prompts --- */
const tagInput = await tp.system.prompt(
  "Tags (comma-separated, with or without #)",
  "daily, "
) ?? "";

const tags = tagInput
  .split(",")
  .map(t => t.trim().replace(/^#/, ""))
  .filter(Boolean);
const tagsYaml = tags.map(t => `"${t}"`).join(", ");

const moodOptions = ["Bad 😫","Good 🙂","Great 🤩"];
const mood = await tp.system.suggester(moodOptions, moodOptions) ?? "Good 🙂";
-%>
---
date_created: "<% tp.file.creation_date('dddd, DD MMMM YYYY') %>"
time_created: "<% tp.file.creation_date('hh:mm A') %>"
mood: "<% mood %>"
tags: [<% tagsYaml %>]
---
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