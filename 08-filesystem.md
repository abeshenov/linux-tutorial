# ยง8: File system

---

## What's in the root /? ๐คจ

```
user@cosmos:~$ ls -p /
bin/   dev/   home/  lib64/  mnt/  proc/  run/
srv/   tmp/   var/   boot/   etc/  lib/   media/
opt/   root/  sbin/  sys/    usr/
```

- Linux distributions more or less follow the
  **[Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)**.

---

| Dir        | Contents        | Dir     | Contents                       |
|------------|-----------------|---------|--------------------------------|
| `/bin`     | basic bins      | `/proc` | process info                   |
| `/boot`    | bootloader      | `/root` | root home                      |
| `/dev`     | devices         | `/run`  | run-time data                  |
| `/etc`     | configuration   | `/sbin` | system binaries                |
| `/home`    | home dirs       | `/srv`  | data served                    |
| `/lib(64)` | libs            | `/sys`  | system info                    |
| `/media`   | removable media | `/tmp`  | temporary files                |
| `/mnt`     | mounted fs      | `/usr`  | user shareable, read-only data |
| `/opt`     | addon pkgs      | `/var`  | variable data                  |

---

## Binaries โ

```
โโโ ๐ bin    โ essential binaries available to all users
โ   โโโ โ bash     โ some basic commands
โ   โโโ โ date
โ   โโโ โ mv
โ   โโโ โ rm
โ   โโโ โ tar
โ   โโโ ...     
โ
โโโ ๐ sbin  โ system binaries available to root
โ              (boot, recovery, etc.)
โ
โโโ ๐ usr   โ data shared between users
    โโโ ๐ bin   โ user commands
    โ   โโโ โ apt
    โ   โโโ โ curl
    โ   โโโ โ less
    โ   โโโ โ man
    โ   โโโ โ tree
    โ   โโโ ...
    โ
    โโโ ๐ local
        โ
        โโโ ๐ bin   โ binaries for local installation
```

---

## Libraries ๐

```
โโโ ๐ lib       โ libraries: shared objects = SO,
โโโ ๐ lib64       kernel modules, etc.
โ                  (like DLLs in W*ndows)
โโโ ๐ usr
    โโโ ๐ lib       โ user libraries
    โ
    โโโ ๐ local
        โ
        โโโ ๐ lib
```

---

## Home directories ๐ก

```
โโโ ๐ home   โ user home directories
โ   โโโ ๐ user   (user's data, installations, configurations)
โ   โโโ ...
โ
โโโ ๐ root   โ root's home
```

---

## Devices ๐

### devfs managed by kernel

```
โโโ ๐ dev   โ device files
    โโโ ๐ null      โ null-device (discards data)
    โโโ ๐ pts
    โ   โโโ ๐ 0     โ pseudoterminal connected to standard input
    โ   โโโ ...
    โ
    โโโ ๐ random    โ (pseudo)random byte source, blocks when out of entropy
    โโโ ๐ tty       โ current console (TeleTYpewriter)
    โโโ ๐ urandom   โ (pseudo)random byte source, non-blocking (unlimited)
    โโโ ๐ zero      โ provides zero-characters 0x00
    โโโ ...
```

---

## Info managed by kernel ๐

```
โโโ ๐ proc   โ processes
โ   โโโ ๐ cpuinfo   โ CPU info
โ   โโโ ๐ meminfo   โ memory info
โ   โโโ ๐ version   โ kernel version
โ   โ
โ   โโโ ๐ {pid}   โ directory attached to process ID
โ       โโโ ๐ cmdline   โ command that started the process
โ       โโโ ๐ cws       โ symlink to the current working dir
โ       โโโ ๐ environ   โ environment variables
โ       โโโ ๐ exe       โ symbolic link to the executable
โ       โโโ ๐ fg        โ directory with file descriptors
โ       โโโ ๐ stat      โ status of the process
โ       โโโ ...
โ
โโโ ๐ sys   โ information about devices, drivers, and kernel
```

---

## Temporary data โณ

```
โโโ ๐ run   โ run-time variable data; cleared on boot
โ
โโโ ๐ tmp   โ temporary files,
               may be created by everyone,
               don't persist
```

---

## /usr ๐ฅ

```
โโโ ๐ usr   โ data shared between users
    โโโ ๐ bin
    โโโ ๐ include   โ C header files
    โโโ ๐ lib
    โโโ ๐ local   โ locally installed software
    โ   โโโ ๐ bin
    โ   โโโ ๐ include
    โ   โโโ ๐ lib
    โ   โโโ ๐ share
    โ   โโโ ๐ src
    โ   โโโ ...
    โ
    โโโ ๐ share     โ architecture-independent shared data
    โ   โโโ ๐ dict    โ dictionaries
    โ   โโโ ๐ doc     โ documentation
    โ   โโโ ๐ fonts   โ fonts
    โ   โโโ ๐ locale  โ locales
    โ   โโโ ๐ man     โ man pages
    โ   โโโ ...
    โ
    โโโ ๐ src       โ source code
    โ
    โโโ ...
```

---

## Other stuff ๐ฎ

```
โโโ ๐ etc   โ 'etcetera'; host-specific configuration files
โ
โโโ ๐ opt   โ additional software packages
โ
โโโ ๐ srv   โ data served by the system
โ
โโโ ๐ var   โ variable data
    โโโ ๐ cache
    โโโ ๐ lock
    โโโ ๐ log
    โโโ ๐ mail
    โโโ ...
```

---

## Boot and file systems ๐ค

```
โโโ ๐ boot  โ boot loader files
โ
โโโ ๐ media   โ mount points for removable devices
โ
โโโ ๐ mnt     โ mount points for other file systems
```

---

## Explore it yourself! ๐ช

- Read `cpuinfo`, `meminfo`, `version` inside `/proc` as regular files.

- For a process with some ID, explore `/proc/{pid}`.

- What's the difference between `/bin` and `/usr/bin`?

- Check out `/var/log/apt/history.log`.
