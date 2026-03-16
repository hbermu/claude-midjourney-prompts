# Mistakes Log

Documented mistakes to avoid repeating them.

<!-- Format:
## <Short description>
**What happened:** <brief description>
**Correct behavior:** <what to do instead>
-->

## Never commit PROMPT.md
**What happened:** Tried to `git add PROMPT.md` — it is intentionally in `.gitignore`.
**Correct behavior:** PROMPT.md is a local working file only. Never stage or push it to the repository.

## Multiple --oref is not supported in V7
**What happened:** Used `--oref URL1 URL2` expecting both character references to work simultaneously. MJ returned "Multiple Omni References aren't supported".
**Correct behavior:** For multi-character scenes, use ONE `--oref` for the primary character and put the secondary character's image URL as an **image prompt** at the very start of the `/imagine` command, controlling its weight with `--iw`:
```
/imagine URL_CHAR2 [text prompt] --oref URL_CHAR1 --ow 120 --iw 1
```
Keep `--iw` between 0.5 and 1.5. Lower = text dominates, higher = image reference dominates.

## Multi-character reference scenes are unreliable in V7
**What happened:** Used one character as image prompt at the start and the other with `--oref`. MJ frequently blended or ignored one character's likeness.
**Correct behavior:** Multi-character reference scenes are unreliable in V7. Always warn the user of this limitation before attempting. If they want to proceed, use the best-effort approach from the Multi-Character Scenes section of CLAUDE.md (one `--oref` for primary + image prompt URL for secondary). Do not promise recognizable results.

## Never omit --no when generating character portraits
**What happened:** Generated a portrait without `--no` flag. MJ added unwanted elements and cropped the composition incorrectly (bust instead of full body).
**Correct behavior:** Always include `--no photo, realistic, cropped, bust, headshot` as a baseline for character portraits. Add specific exclusions based on what the character should NOT have (e.g., `--no dark, gloomy` for colorful characters). Never skip `--no` on character images.

## --cref is not compatible with V7
**What happened:** Used `--cref` in a V7 prompt, resulting in error "Invalid parameter -- cref is not compatible with --version 7".
**Correct behavior:** In V7, use `--oref [URL] --ow [0-1000]` instead of `--cref`/`--cw`. `--oref` is the V7 equivalent for character references.
