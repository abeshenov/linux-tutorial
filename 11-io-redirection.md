# §11: IO redirection

---

## Basic redirection of STDIN / STDOUT

```
command > file       # redirect STDOUT to file
command >> file      # append to the end
command < file       # send file to the command
command1 | command2  # pipeline
```

---

## Useless cat 😹

- Don't do `cat foo.txt | command` : it's the same as `command < foo.txt`.

- *nix convention: normally a command accepts either a file as argument,
or reads from STDIN. This is to allow piping.

- https://porkmail.org/era/unix/award

---

## Examples 💡

```
echo "Hello" > test.txt
echo "Hello again" >> test.txt
sort -u /etc/passwd | head
```
