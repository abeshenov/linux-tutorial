# §3: Using APT

---

- We have a very basic system at hand.

- Let's install some software.

- `apt` = Advanced Package Tool.

- Specific to Debian and Ubuntu.

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

## Getting --help 🆘

```
user@cosmos:~$ tar --help
Usage: tar [OPTION...] [FILE]...
GNU 'tar' saves many files together into a
single tape or disk archive, and can restore
individual files from the archive.

. . . . .
```

---

## Getting manual 📖

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

---

## wget 💾

```
user@cosmos:~$ sudo apt install wget lzip
. . . . .
user@cosmos:~$ wget https://data.iana.org/time-zones/releases/tzdb-2022a.tar.lz
user@cosmos:~$ tar -xvf tzdb-2022a.tar.lz
```

---

## Old software 💩

```
user@cosmos:~$ apt info nodejs
Package: nodejs
Version: 12.22.12~dfsg-1~deb11u1
Priority: optional
Section: web
Maintainer: Debian Javascript Maintainers <pkg-javascript-devel@alioth-lists.debian.net>
Installed-Size: 938 kB
Provides: node-types-node (= 12.20.55~12.22.12~dfsg-1~deb11u1)
Depends: libc6 (>= 2.2.5), libnode72 (= 12.22.12~dfsg-1~deb11u1)
Recommends: ca-certificates, nodejs-doc
Suggests: npm
Conflicts: nodejs-legacy
Breaks: node-babel-runtime (<< 7), node-typescript-types (<< 20210110~)
Replaces: nodejs-legacy
Homepage: https://nodejs.org/
Download-Size: 147 kB
APT-Sources: http://deb.debian.org/debian-security bullseye-security/main amd64 Packages
Description: evented I/O for V8 javascript - runtime executable

N: There is 1 additional record. Please use the '-a' switch to see it
```
