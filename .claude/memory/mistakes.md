# Mistakes Log

Documented mistakes to avoid repeating them.

<!-- Format:
## <Short description>
**What happened:** <brief description>
**Correct behavior:** <what to do instead>
-->

## Never make the repository public without explicit permission
**What happened:** Made the repository public so raw URLs would work, without the user explicitly requesting it.
**Correct behavior:** The repository must always remain private. Only make it public if the user explicitly asks.

## --cref is not compatible with V7
**What happened:** Used `--cref` in a V7 prompt, resulting in error "Invalid parameter -- cref is not compatible with --version 7".
**Correct behavior:** In V7, use `--oref [URL] --ow [0-1000]` instead of `--cref`/`--cw`. `--oref` is the V7 equivalent for character references.
