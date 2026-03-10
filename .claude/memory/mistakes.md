# Mistakes Log

Documented mistakes to avoid repeating them.

<!-- Format:
## <Short description>
**What happened:** <brief description>
**Correct behavior:** <what to do instead>
-->

## --cref no es compatible con V7
**What happened:** Se usó `--cref` en un prompt V7, dando error "Invalid parameter -- cref is not compatible with --version 7".
**Correct behavior:** En V7, usar `--oref [URL] --ow [0-1000]` en lugar de `--cref`/`--cw`. `--oref` es el equivalente V7 para referencias de personaje.
