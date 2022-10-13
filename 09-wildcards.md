# §9: Wildcards and patterns

---

## Patterns 🤖

- `*`: zero or more characters, e.g. `foo.txt` matches `*.txt`.
- `?`: one character, e.g. `123.txt` matches `???.txt`.
- Escaped sequences `\*` and `\?`.
- `[abc]`, `[!abc]`, `[abc]*`, `[!abc]*`: character classes.
- `{foo,bar}` : foo or bar.
- See the docs for more.

---

## Examples 🪄

```[shell]
*.bak        # anything ending in .bak
*.{txt,pdf}  # files ending in .txt or .pdf
???.bak      # matches foo.bak and not foobar.bak
```

---

## Pitfalls 💣

- Bash expands wildcards and passes to the command various arguments.

```
echo {a,b,c}{d,e,f}
ad ae af bd be bf cd ce cf
```

- If there are files named `-r` and `-f`, then `rm *` can mistake files
for arguments. Better option is `rm ./*`.
