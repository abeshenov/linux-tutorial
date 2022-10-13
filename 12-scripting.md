# §12: Scripting basics

---

## Install basic editor 🗒

- `sudo apt install nano`

- `vim` or `emacs`.

---

## Scripts 📋

- Script is a file read line by line by the interpreter.

- Should have execution rights (`x`).

- Interpreter is specified in the first line (shebang):
  `#!<path-to-the-interpreter>`

---

## Shebangs 💣

```
#!/bin/bash
#!/usr/bin/python3
#!/usr/bin/perl
#!/usr/bin/node
```

---

## General considerations ✅

- Bash scripts must be simple and short.

- Otherwise, consider Perl, Python, Node.js, etc.

- Perl is good for more complex programs. Syntax- and feature-wise,
it's `bash` + `sed` + ... on acid.

---

## Creating first script 👶

- `nano hello`

```
#!/bin/bash

echo "Hello, World!"
```

- `chmod +x hello`

- `./hello`

---

## Line endings ⛔

- Scripts must have correct line endings `<LF>`.
- With `<CR><LF>` endings, `<CR>` is treated as a part of shebang.

---

## Combining commands 👨‍🔧

- `foo && bar` : executes `bar` if `foo` returns `0` (success),
- `foo || bar` : executes `bar` if `foo` does not return `0` (failure).
- `true` : command that returns `0` (success).
- `false` : command that returns `1` (failure).

---

## Arguments 🤬

- `$0`, `$1`, `$2`, `$3`, ...
- `$@` : all arguments
- `$#`

---

## Examples

For further syntax and examples:

https://github.com/abeshenov/linux-tutorial/tree/main/scripting
