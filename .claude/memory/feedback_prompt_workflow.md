---
name: Always show filename at end of prompt messages
description: When generating or iterating on a Midjourney prompt, always display the expected filename at the end of the response.
type: feedback
---

Always end every message that contains a generated or modified Midjourney prompt with the expected filename.

**Why:** User explicitly requested this so they always know the target filename without having to ask or look it up.

**How to apply:** Any time a prompt is generated or iterated (new prompt, modification, style change, parameter tweak), the last line of the response must show the filename, e.g.:

> Archivo: `trosky-overview.png`
