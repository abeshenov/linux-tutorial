# §4: Working with files

---

- Everything is a file.
- A directory or device is also a special kind of file.
- **Symbolic links**: pointers to files.
- Path separator between directories is `/`.
- `.` is the current directory and `..` is the parent directory.
- File names are case-sensitive.

---

## Stat 🔬

```
user@cosmos:~$ stat /etc/shadow
  File: /etc/shadow
  Size: 671             Blocks: 8          IO Block: 4096   regular file
Device: 40h/64d Inode: 10857       Links: 1
Access: (0640/-rw-r-----)  Uid: (    0/    root)   Gid: (   42/  shadow)
Access: 2022-08-05 17:50:36.095309399 +0000
Modify: 2022-08-05 17:45:16.236327091 +0000
Change: 2022-08-05 17:45:16.247327091 +0000
 Birth: 2022-08-05 17:45:16.236327091 +0000
```

---

```
user@cosmos:~$ stat --format=%F /etc/passwd
regular file
user@cosmos:~$ stat --format=%F /dev/tty
character special file
user@cosmos:~$ stat --format=%F /home
directory
user@cosmos:~$ stat --format=%F /proc/1/exe
symbolic link
```

As you see,

`/etc/passwd`, `/dev/tty`, `/home`, `/proc/1/exe`

are all files, but of different kind.

---

| Command                | Action                              |
|------------------------|-------------------------------------|
| `pwd`                  | print working directory             |
| `ls`                   | list files in the working directory |
| `tree`                 | print file tree (package `tree`)    |
| `ls foo`               | list files in `foo`                 |
| `cd foo`               | go to `foo` directory               |

---

## Some options of ls ⚙

- `-1` : one file per line,
- `-a`, `--all` : show hidden files,
- `-h`, `--human-readable` : human-readable file size,
- `-l` : long listing format,
- `-t` : sort by time, newest first,
- `-r`, `--reverse` : reverse sort.

```
user@cosmos:~$ ls -1ahlp /etc
total 228K
drwxr-xr-x 1 root root   1.5K Aug  5 17:45 .
drwxr-xr-x 1 root root    152 Aug  4 07:30 ..
-rw------- 1 root root      0 Aug  1 00:00 .pwd.lock
-rw-r--r-- 1 root root   3.0K Aug  1 00:00 adduser.conf
drwxr-xr-x 1 root root    462 Aug  5 17:33 alternatives/
. . . . .
```

---

## Hidden files 🫣

- By convention, files starting with `.` are hidden.

```
user@cosmos:~$ ls -1 
user@cosmos:~$ ls -1a
.
..
.bash_history
.bash_logout
.bashrc
.profile
```

- Familiar example: Git stores its local data in `.git` directory.

---

| Command                | Action                       |
|------------------------|------------------------------|
| `mkdir foo`            | create directory `foo`       |
| `mkdir -p foo/bar/baz` | create together with parents |
| `mv foo bar`           | move `foo` to `bar`          |
| `cp foo bar`           | copy `foo` to `bar`          |
| `cp -r ./foo/ bar`     | copy directories recursively |
| `rm foo.txt`           | delete `foo.txt`             |
| `rm -r ./foo/`         | delete `foo` recursively     |
| `ln -s source target`  | create symbolic link         |
| `touch foo.txt`        | modify / create file         |

---

## Viewing files 👀

| Command            | Action                             |
|--------------------|------------------------------------|
| `cat file ...`     | concatenate files                  |
| `less foo.txt`     | view contents interactively        |
| `head foo.txt`     | view first lines                   |
| `tail foo.txt`     | view last lines                    |
| `tail -f log.txt`  | view last lines and watch updates  |

---

## find files 🔍

- `find` : prints files in a directory.

- Finding file by name:

```
user@cosmos:~$ find /usr -name *.txt
/usr/share/doc/libdb5.3/build_signature_amd64.txt
/usr/share/doc/mount/mount.txt
/usr/share/doc/util-linux/00-about-docs.txt
/usr/share/doc/util-linux/PAM-configuration.txt
/usr/share/doc/util-linux/blkid.txt
. . . . .
```

---

## grep through contents 🔍

- Read `man grep`.
- `-r` : recursive search,
- `-i` : ignore case.

```
user@cosmos:~$ grep -r -i torvalds /usr
/usr/share/doc/bsdutils/copyright:           1991, 1992 Linus Torvalds
/usr/share/doc/bsdutils/copyright:Copyright: 1991, 1992 Linus Torvalds
/usr/share/doc/libblkid1/copyright:           1991, 1992 Linus Torvalds
/usr/share/doc/libblkid1/copyright:Copyright: 1991, 1992 Linus Torvalds
/usr/share/doc/libmount1/copyright:           1991, 1992 Linus Torvalds
```

---

## Disk usage 📂


```
user@cosmos:~$ du -sh /usr
136M    /usr

user@cosmos:~$ stat /usr
  File: /usr
  Size: 84              Blocks: 0          IO Block: 4096   directory
Device: 43h/67d Inode: 782         Links: 1
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-08-05 22:26:24.497964420 +0000
Modify: 2022-08-01 00:00:00.000000000 +0000
Change: 2022-08-04 05:56:55.013459324 +0000
 Birth: 2022-08-04 05:37:16.647535882 +0000
```

---

## Disk space 💿

```
user@cosmos:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vdb         50G   46G  4.2G  92% /
tmpfs            64M     0   64M   0% /dev
tmpfs           3.3G     0  3.3G   0% /sys/fs/cgroup
shm              64M     0   64M   0% /dev/shm
/dev/vdb         50G   46G  4.2G  92% /etc/hosts
devtmpfs        3.3G     0  3.3G   0% /dev/tty
tmpfs           3.3G     0  3.3G   0% /proc/asound
tmpfs           3.3G     0  3.3G   0% /proc/acpi
tmpfs           3.3G     0  3.3G   0% /proc/scsi
tmpfs           3.3G     0  3.3G   0% /sys/firmware
```

---

## Other useful commands 🔮

| Command                    | Action                           |
|----------------------------|----------------------------------|
| `sort foo.txt`             | sort lines and print to stdout   |
| `sort -u foo.txt`          | sort lines, print unique entries |
| `diff foo.txt bar.txt`     | compare files                    |
| `sed s/foo/bar/g text.txt` | pattern substitution             |
| `wc`                       | count words, lines, bytes        |

---

Count installed packages:

```
user@cosmos:~$ apt list --installed | wc -l
```

---

![sed and awk](sed-awk.jpg)

---

## Working with archives 📦

| Command                              | Action                    |
|--------------------------------------|---------------------------|
| `zip -r files.zip files`             | create `.zip` acrchive    |
| `unzip files.zip -d /path/to/unzip`  | extract `.zip` archive    |
| `tar -czvf files.tar.gz files`       | create `.tar.gz` archive  |
| `tar -xvf files.tar.bz2`             | extract `.tar.gz` archive |
| `tar -tvf files.tar.bz2`             | list contents             |

---

## What is `.tar.gz`? 📦

- An **archive** packages files together.

  `.tar` = "tape archive" format.

- **Compression** is applied to an archive.

  `.gz` = GNU ZIP, `.bz2` = bzip2, `.lz` = Lzip, `.xz` = xz.

- `tar` command is already aware of those formats applied to `.tar`.
