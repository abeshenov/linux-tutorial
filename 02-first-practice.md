# §2: First practice

---

- Run our `debian-playground` image in Docker.

- You will see the **Bash** prompt:

```
user@cosmos:~$ ▮
```

- `user` : user
- `cosmos` : host
- `~` : abbreviation for home directory
- `$` : invitation to type commands

---

## 👋👋👋

```
user@cosmos:~$ echo 'Hello, World!'
Hello, World!
user@cosmos:~$ echo "Hello, $(whoami)!"
Hello, user!
```

---

## Useful commands 💡

| Command   | Action                |
|-----------|-----------------------|
| `reset`   | reset console         |
| `clear`   | clear screen          |
| `history` | command history       |
| `exit`    | exit the shell        |
| `logout`  | log out of the shell  |

Command history is stored in `.bash_history` in your home dir.

---

## Builtins vs. external commands

- `type <command>` : command type.
- `whereis <name>` : find binary by name.

```
user@cosmos:~$ type cd 
cd is a shell builtin
user@cosmos:~$ whereis cd
cd:
```

```
user@cosmos:~$ type --all ls
ls is aliased to `ls --color=auto'
ls is /bin/ls
user@cosmos:~$ whereis ls
ls: /bin/ls /usr/share/man/man1/ls.1.gz
```

---

## Useful keys (`C=Ctrl`, `M=Alt`)

| Key     | Action                                      |
|---------|---------------------------------------------|
| `Tab`   | completion                                  |
| `C-a/e` | cursor to line start/**end**                |
| `M-b/f` | previous/next word (**back**/**forward**)   |
| `C-k`   | delete everything till line end (**kill**)  |
| `C-w`   | delete previous **word**                    |
| `C-y`   | paste what we cut (**yank**)                |
| `C-r`   | **reverse** history search (`C-r` for more) |

---

## More keys ⌨

| Key   | Action                                     |
|-------|--------------------------------------------|
| `C-c` | sends `SIGINT` to the running process      |
| `C-d` | sends end-of-file symbol to console        |
| `C-z` | stops running process (use `fg` to resume) |

---

## cat (concatenate) 📃

```
cat file1.txt [file2.txt ...]
```

Will print to standard output files `file1.txt`, `file2.txt`, etc.
concatenated.

---

## See something with cat

```
user@cosmos:~$ cat /etc/issue
Debian GNU/Linux 11 \n \l
```

```
user@cosmos:~$ cat /etc/debian_version
11.4
```

```
user@cosmos:~$ cat /etc/os-release
PRETTY_NAME="Debian GNU/Linux 11 (bullseye)"
NAME="Debian GNU/Linux"
VERSION_ID="11"
VERSION="11 (bullseye)"
VERSION_CODENAME=bullseye
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
```
