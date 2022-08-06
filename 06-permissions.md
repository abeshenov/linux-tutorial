# §6: Permissions

---

- Permissions are important
  * for security reasons,
  * not to touch data you're not supposed to.

- File permissions managed on three levels:
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
Access: (0644/-rw-r--r--)  Uid: ( 1000/    user)   Gid: ( 1000/    user)
user@cosmos:~$ sudo chown root test.txt 
user@cosmos:~$ stat test.txt 
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: ( 1000/    user)
user@cosmos:~$ sudo chgrp root test.txt 
user@cosmos:~$ stat test.txt 
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
```

---

## Permissions ✅

|     | Permission | For files                | For directories               |
|-----|------------|--------------------------|-------------------------------|
| `r` | read       | read contents            | list files inside             |
| `w` | write      | modify contents          | create, rename, delete files  |
| `x` | execute    | execute binary or script | enter the directory with `cd` |

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
  File: /usr/bin
  Size: 3442            Blocks: 0          IO Block: 4096   directory
Device: 43h/67d Inode: 783         Links: 1
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-08-06 01:11:02.277443816 +0000
Modify: 2022-08-06 00:41:08.919538334 +0000
Change: 2022-08-06 00:41:08.919538334 +0000
 Birth: 2022-08-04 05:37:16.647535882 +0000
```

- File type `d` (directory).
- Owner `rwx`, group `r-x`, others `r-x`.

---

## File types 🗂

| Character | Type                     |
|-----------|--------------------------|
| `-`       | Regular file             |
| `d`       | Directory                |
| `l`       | Symbolic link            |
| `c`       | Character special device |
| `b`       | Block special device     |
| `p`       | FIFO                     |
| `s`       | Socket                   |

---

## Examples 📂

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
Access: (0644/-rw-r--r--)  Uid: ( 1000/    user)   Gid: ( 1000/    user)

user@cosmos:~$ chmod +x test.txt 
user@cosmos:~$ stat test.txt 
Access: (0755/-rwxr-xr-x)  Uid: ( 1000/    user)   Gid: ( 1000/    user)

user@cosmos:~$ chmod 666 test.txt 
user@cosmos:~$ stat test.txt 
Access: (0666/-rw-rw-rw-)  Uid: ( 1000/    user)   Gid: ( 1000/    user)
```

---

Remember: `chmod`, `chown`, `chgrp`.
