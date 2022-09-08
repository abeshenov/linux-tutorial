# §6: File permissions

---

- Permissions are important
  * for security reasons,
  * not to touch data you're not supposed to.

- Managed on three levels:
  * file owner,
  * file group,
  * everyone.

---

## Managing owner and group ⚙

- `chown <owner> <file>`
- `chgrp <group> <file>`

---

```
user@cosmos:~$ touch test.txt
user@cosmos:~$ stat test.txt 
Access: (0644/-rw-r--r--)  Uid: (1000/  user)   Gid: (1000/  user)
user@cosmos:~$ sudo chown root test.txt 
user@cosmos:~$ stat test.txt 
Access: (0644/-rw-r--r--)  Uid: (   0/  root)   Gid: (1000/  user)
user@cosmos:~$ sudo chgrp root test.txt 
user@cosmos:~$ stat test.txt 
Access: (0644/-rw-r--r--)  Uid: (   0/  root)   Gid: (   0/  root)
```

---

## Permissions ✅

|     | Permission | Regular files   | Directories                  |
|-----|------------|-----------------|------------------------------|
| `r` | read       | read contents   | list files inside            |
| `w` | write      | modify contents | create, rename, delete files |
| `x` | execute    | execute         | enter with `cd`              |

⚠️ Set `x` only on executable files (binaries, scripts) and directories.

---

## Represented by a number 🤖

| Number | Binary  | Permissions |
|--------|---------|-------------|
| `0`    | `0b000` | `---`       |
| `1`    | `0b001` | `--x`       |
| `2`    | `0b010` | `-w-`       |
| `3`    | `0b011` | `-wx`       |
| `4`    | `0b100` | `r--`       |
| `5`    | `0b101` | `r-x`       |
| `6`    | `0b110` | `rw-`       |
| `7`    | `0b111` | `rwx`       |

<!--
## Sticky bit

- When **sticky bit** is set for a directory, files may only be unlinked or
  renamed by `root`, the directory owner, or the file owner.

- Makes no sense (ignored) on files.

- Example: `/tmp` has sticky bit.

  Because everyone creates temporary files in there, but we want them
  to "stick" to their owner!
-->

---

## Format 🤖

```
user@cosmos:/usr/local/lib$ stat /usr/bin
Access: (0755/drwxr-xr-x)  Uid: (   0/  root)   Gid: (   0/  root)
         │ │  │ │  │  └── all: r-x
         │ │  │ │  └── group: r-x
         │ │  │ └── owner: rwx
         │ │  └── file type: (d)irectory
         │ └── 755 = rwxr-xr-x
   "sticky bit" = 0
```

---

## File types 🗂

| Character | Type                     |
|-----------|--------------------------|
| `-`       | regular file             |
| `d`       | directory                |
| `l`       | symbolic link            |
| `c`       | character special device |
| `b`       | block special device     |
| `p`       | FIFO                     |
| `s`       | socket                   |

---

## Examples

- `777` = `rwxrwxrwx` :
  everything is permitted to everyone.

- `666` = `rw-rw-rw-` :
  permission of the beast, anyone can read and modify the file.

- `644` = `rw-r--r--` :
  owner can read and modify; others can read.

- `755` = `rwxr-xr-x` :
  directory is read-only, except for the owner.

---

## Real examples 📂

| File          | Permissions         |
|---------------|---------------------|
| `/etc/passwd` | `0644` `-rw-r--r--` |
| `/bin/bash`   | `0755` `-rwxr-xr-x` |
| `/tmp`        | `1777` `drwxrwxrwt` |
| `/home`       | `0755` `drwxr-xr-x` |
| `/home/user`  | `0755` `drwxr-xr-x` |

---

## Changing permissions 🖍

```
user@cosmos:~$ touch test.txt
user@cosmos:~$ stat test.txt 
Access: (0644/-rw-r--r--)  Uid: (1000/  user)   Gid: (1000/  user)
user@cosmos:~$ chmod +x test.txt 
user@cosmos:~$ stat test.txt 
Access: (0755/-rwxr-xr-x)  Uid: (1000/  user)   Gid: (1000/  user)
user@cosmos:~$ chmod 666 test.txt 
user@cosmos:~$ stat test.txt 
Access: (0666/-rw-rw-rw-)  Uid: (1000/  user)   Gid: (1000/  user)
```

---

## What is the default? 🤔

- `umask` : print file mode mask.
- `umask 022` : set file mode mask.
- Default permissions:
  - `666` − `umask` for regular files,
  - `777` − `umask` for directories.

```
user@cosmos:~$ umask
0022
user@cosmos:~$ touch test.txt
user@cosmos:~$ mkdir test
user@cosmos:~$ ls -1l
drwxr-xr-x 1 user user 0 Aug  8 20:11 test
-rw-r--r-- 1 user user 0 Aug  8 20:11 test.txt
```

---

Remember: `chmod`, `chown`, `chgrp`.
