# §3: Getting help with man and installing packages with APT

---

- We have a very basic system at hand.

- Let's install some software.

- `apt` = Advanced Package Tool.

- Specific to Debian-based distributions.

- Other systems come with their own package managers.

---

## Basic use 📦

| `apt` command      | Action                        |
|--------------------|-------------------------------|
| `list`             | list available packages       |
| `list --installed` | list installed packages       |
| `update`           | download list of packages     |
| `upgrade`          | install package upgrades      |
| `search <pkg>`     | package lookup                |
| `info <pkg>`       | package info                  |
| `install <pkg>`    | install a package             |
| `remove <pkg>`     | remove a package              |
| `autoremove`       | remove no needed dependencies |

---

## Sudo 🦸

- Package management requires `root` privileges.
- Use `sudo` command

```
user@cosmos:~$ apt update
Reading package lists... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
user@cosmos:~$ sudo apt update
. . . . .
```

---

## Install man 📖

We'll install some documentation.

```
user@cosmos:~$ sudo apt update
. . . . .
user@cosmos:~$ sudo apt install man-db manpages
. . . . .
```

---

## --help 🆘

```
user@cosmos:~$ tar --help
Usage: tar [OPTION...] [FILE]...
GNU 'tar' saves many files together into a
single tape or disk archive, and can restore
individual files from the archive.

. . . . .
```

---

## man 📖

```
user@cosmos:~$ man tar
TAR(1)                   GNU TAR Manual                  TAR(1)

NAME
       tar - an archiving utility

SYNOPSIS
   Traditional usage
       tar {A|c|d|r|t|u|x}[GnSkUWOmpsMBiajJzZhPlRvwo] [ARG...]

   UNIX-style usage
       tar -A [OPTIONS] ARCHIVE ARCHIVE

       tar -c [-f ARCHIVE] [OPTIONS] [FILE...]

       tar -d [-f ARCHIVE] [OPTIONS] [FILE...]

. . . . .
```

---

| Command             | Action                                 |
|---------------------|----------------------------------------|
| `whatis cat`        | short summary                          |
| `man cat`           | show manual page                       |
| `apropos <keyword>` | search for `<keyword>` in descriptions |

---

## Calendar 📆

```
user@cosmos:~$ sudo apt install ncal
user@cosmos:~$ cal
    August 2022       
Su Mo Tu We Th Fr Sa  
    1  2  3  4  5  6  
 7  8  9 10 11 12 13  
14 15 16 17 18 19 20  
21 22 23 24 25 26 27  
28 29 30 31
```

---

## UUID 🤖

```
user@cosmos:~$ sudo apt install uuid-runtime
user@cosmos:~$ uuidgen 
050ff192-3dbf-4d32-b64a-e4a3f2bb8e72
```

---

## curl 🌍

```
user@cosmos:~$ sudo apt install curl
. . . . .
user@cosmos:~$ curl wttr.in
Weather report: Guanajuato City, Mexico

      \   /     Sunny
       .-.      19 °C          
    ― (   ) ―   ↙ 8 km/h       
       `-’      10 km          
      /   \     0.0 mm 
```

---

## Possibilities of curl ⭐

- Various protocols.
- Inspection of headers (`-i` and `-v`).
- Sending extra headers (`-H`).
- GET, HEAD, POST, PUT, DELETE (`-X`).
- Sending file contents in POST (`-d`).
- Read `man curl`.
- Postman is a proprietary bloat 🤮

---

## wget 💾

```
user@cosmos:~$ sudo apt install wget lzip
. . . . .

user@cosmos:~$ wget https://data.iana.org/time-zones/releases/tzdb-2022a.tar.lz
. . . . .

user@cosmos:~$ tar -xvf tzdb-2022a.tar.lz
. . . . .
```

---

## Old software

- Don't expect latest software versions in "stable" packages.

- Especially if the Debian release cycle is slower.

- Latest versions are in "unstable".

```
user@cosmos:~$ apt info nodejs
Package: nodejs
Version: 12.22.12~dfsg-1~deb11u1

# 18.x: current Node.js version,
# 12.x: old, not supported anymore.
```

---

## Installing from .deb files 📦

- Packages are stored in `.deb` files.
- Can be installed directly.
- Prefix file name with `./`:

```
$ sudo apt install ./code_1.70.0-1659589288_amd64.deb
$ apt info code
Package: code
Version: 1.70.0-1659589288
Priority: optional
Section: devel
Maintainer: Microsoft Corporation <vscode-linux@microsoft.com>
Installed-Size: 359 MB
Provides: visual-studio-code
. . . . .
```
