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

## Mixing two characters via image prompt + --oref does not work reliably
**What happened:** Used one character as image prompt at the start and the other with `--oref`. MJ was unable to correctly represent both characters simultaneously — it blended or ignored one of them.
**Correct behavior:** There is currently no reliable way in MJ V7 to generate a scene with two specific pre-existing characters that are both recognizable. Do not attempt multi-character reference scenes. Inform the user of this limitation before generating.

## --cref is not compatible with V7
**What happened:** Used `--cref` in a V7 prompt, resulting in error "Invalid parameter -- cref is not compatible with --version 7".
**Correct behavior:** In V7, use `--oref [URL] --ow [0-1000]` instead of `--cref`/`--cw`. `--oref` is the V7 equivalent for character references.
