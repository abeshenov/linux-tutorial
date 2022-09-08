# §8: File system

---

## What's in the root /? 🤨

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

## Binaries ⚙

```
├── 📂 bin    ← essential binaries available to all users
│   ├── ⚙ bash     ← some basic commands
│   ├── ⚙ date
│   ├── ⚙ mv
│   ├── ⚙ rm
│   ├── ⚙ tar
│   └── ...     
│
├── 📁 sbin  ← system binaries available to root
│              (boot, recovery, etc.)
│
└── 📂 usr   ← data shared between users
    ├── 📂 bin   ← user commands
    │   ├── ⚙ apt
    │   ├── ⚙ curl
    │   ├── ⚙ less
    │   ├── ⚙ man
    │   ├── ⚙ tree
    │   └── ...
    │
    └── 📂 local
        │
        └── 📁 bin   ← binaries for local installation
```

---

## Libraries 📚

```
├── 📁 lib       ← libraries: shared objects = SO,
├── 📁 lib64       kernel modules, etc.
│                  (like DLLs in W*ndows)
└── 📂 usr
    ├── 📁 lib       ← user libraries
    │
    └── 📂 local
        │
        └── 📁 lib
```

---

## Home directories 🏡

```
├── 📂 home   ← user home directories
│   ├── 📁 user   (user's data, installations, configurations)
│   └── ...
│
└── 📁 root   ← root's home
```

---

## Devices 🌟

### devfs managed by kernel

```
└── 📂 dev   ← device files
    ├── 🌟 null      ← null-device (discards data)
    ├── 📂 pts
    │   ├── 🌟 0     ← pseudoterminal connected to standard input
    │   └── ...
    │
    ├── 🌟 random    ← (pseudo)random byte source, blocks when out of entropy
    ├── 🌟 tty       ← current console (TeleTYpewriter)
    ├── 🌟 urandom   ← (pseudo)random byte source, non-blocking (unlimited)
    ├── 🌟 zero      ← provides zero-characters 0x00
    └── ...
```

---

## Info managed by kernel 📝

```
├── 📂 proc   ← processes
│   ├── 📝 cpuinfo   ← CPU info
│   ├── 📝 meminfo   ← memory info
│   ├── 📝 version   ← kernel version
│   │
│   └── 📂 {pid}   ← directory attached to process ID
│       ├── 📝 cmdline   ← command that started the process
│       ├── 📝 cws       ← symlink to the current working dir
│       ├── 📝 environ   ← environment variables
│       ├── 📝 exe       ← symbolic link to the executable
│       ├── 📝 fg        ← directory with file descriptors
│       ├── 📝 stat      ← status of the process
│       └── ...
│
└── 📁 sys   ← information about devices, drivers, and kernel
```

---

## Temporary data ⏳

```
├── 📁 run   ← run-time variable data; cleared on boot
│
└── 📁 tmp   ← temporary files,
               may be created by everyone,
               don't persist
```

---

## /usr 👥

```
└── 📂 usr   ← data shared between users
    ├── 📁 bin
    ├── 📁 include   ← C header files
    ├── 📁 lib
    ├── 📂 local   ← locally installed software
    │   ├── 📁 bin
    │   ├── 📁 include
    │   ├── 📁 lib
    │   ├── 📁 share
    │   ├── 📁 src
    │   └── ...
    │
    ├── 📂 share     ← architecture-independent shared data
    │   ├── 📁 dict    ← dictionaries
    │   ├── 📁 doc     ← documentation
    │   ├── 📁 fonts   ← fonts
    │   ├── 📁 locale  ← locales
    │   ├── 📁 man     ← man pages
    │   └── ...
    │
    ├── 📁 src       ← source code
    │
    └── ...
```

---

## Other stuff 🔮

```
├── 📁 etc   ← 'etcetera'; host-specific configuration files
│
├── 📁 opt   ← additional software packages
│
├── 📁 srv   ← data served by the system
│
└── 📂 var   ← variable data
    ├── 📁 cache
    ├── 📁 lock
    ├── 📁 log
    ├── 📁 mail
    └── ...
```

---

## Boot and file systems 🤖

```
├── 📁 boot  ← boot loader files
│
├── 📁 media   ← mount points for removable devices
│
└── 📁 mnt     ← mount points for other file systems
```

---

## Explore it yourself! 💪

- Read `cpuinfo`, `meminfo`, `version` inside `/proc` as regular files.

- For a process with some ID, explore `/proc/{pid}`.

- What's the difference between `/bin` and `/usr/bin`?

- Check out `/var/log/apt/history.log`.
