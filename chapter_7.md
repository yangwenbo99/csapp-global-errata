## Answers to practice questions

Page 754, `buf` should have a `global` symbol type in `m.o`. Furthermore, the following entries should be added:

| Symbol | `.symtab` entry? | Type     | Module   | Section |
| :-     | :-:              | :-:      | :-:      | :-:     |
| `buf`  | Yes              | `extern` | `swap.o` | UND     |
| `swap` | Yes              | `extern` | `m.o`    | UND     |
