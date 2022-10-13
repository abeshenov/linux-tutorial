# §10: Variables

---

- Global scope by default.

- `NAMING_CONVENTION` for global vars.

```[shell]
$ FOO="World!"
$ echo Hello, $FOO
Hello, World!
```

---

## How global? 🤔

Children won't see bindings by default!

```
$ TEST="Can you hear me?"
$ echo $TEST
Can you hear me?
$ bash
> echo $TEST  # TEST is not defined in this shell

> exit
```

---

## Exports 💾

```
$ export TEST="HEY?"
$ bash
> echo $TEST
HEY?
> exit
```

- Run `export` to see exported vars.

---

## Use of quotation marks ⚠

```
FOO=World
BAR=Hello, $FOO!    # WRONG: sees World as a command
BAR="Hello, $FOO!"  # substitutes World! for $FOO
BAR='Hello, $FOO!'  # this is literally Hello, $FOO!
```

---

## Some predefined variables 💡

- `$$` : current PID
- `$?` : exit status of last command
- `$HOSTNAME`, `$USER`, `$HOME`

---

## $PATH variable 🔎

- List of directories with executables for commands.

- E.g. `/usr/local/bin:/usr/bin:/bin`

- To edit your `$PATH`, add to the end of `~/.profile` file
`PATH="/foo/bar/baz:$PATH"`

---

## Escaping $ and other things 🧨

```
curl host/api/Resource/\$operation
curl 'host/api/Resource/$operation'
curl host/api/Resource?foo=true\&bar=true
curl 'host/api/Resource?foo=true&bar=true'
```

---

## Substitution of command ⚙

```
echo "Today is $(date +%F)"

FOO="Today is $(date +%F)"
echo $FOO

echo $USER is running $(lsb_release -ds)

FILE=/etc/apt/sources.list
echo $(basename $FILE) is located in $(dirname $FILE)
```

---

## Arithmetic 🧮

```
$ echo $((2*3*4*5*6*7*8*9*10))
3628800
$ echo $((2**10))
1024
```

---

## Working with text 🗒

```
text="foobar"
${text/bar/baz}  # foobaz
${text^^}        # FOOBAR
${text:1}        # oobar
${text:3}        # bar
${text:1:4}      # ooba
${text:(-2)}     # ar
```

---

## Example: batch processing 🗂

```
for file in *.jpg; do
  convert "$file" "${file/.jpg/.png}"
done
```

(Will see loops later.)
