# Issue

Poetry (e.g. version 1.7.1) might be incompatible with unstable-tagged Python version.

An "Invalid PEP 440 version" can be observed from `poetry install`.

```bash
poetry install
Updating dependencies
Resolving dependencies... (0.1s)

Invalid PEP 440 version: '3.11.7+'
```

# Solution

Remove `+` in `PY_VERSION` macro from `Include/patchlevel.h` file, and recompile CPython.

E.g.

```c
/* Version as a string */
#define PY_VERSION              "3.11.7"
/*--end constants--*/
```
