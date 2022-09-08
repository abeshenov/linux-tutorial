# §1: GNU, Linux, and distributions

---

## Why Linux and command line? 🤔

- One of the best operating systems.
- Efficient work flow from the terminal.
- Remote access is via command line.
- Linux is everywhere:
  servers,
  containers,
  IoT.

---

![awk? grep? sed? pwd!](awk-grep-sed-pwd.png)

---

## Origins 🦕🦖	

- **[UNIX](https://en.wikipedia.org/wiki/Unix)**: operating system released
  in 1973. Written in C.

- Has inspired many **[UNIX-like](https://en.wikipedia.org/wiki/Unix-like)**
  operating systems.

- **[POSIX](https://en.wikipedia.org/wiki/POSIX)**:
  a family of standards defining UNIX-like systems.

---

## GNU/Linux = GNU + Linux 🐧

- **[Linux](https://www.kernel.org/)**: free kernel written by Linus Torvalds.
  In collaborative development since 1991.
  Millions of lines of code in C.

- **[GNU](https://www.gnu.org/)** (= *GNU's not a UNIX*) Project,
  founded by Richard Stallman in 1983: together with
  the kernel makes a UNIX-like operating system.

- **GNU/Linux** is sometimes abbreviated to **Linux**.

---

## A few distributions 📦

- A **distribution** comes with
  * custom Linux kernel build,
  * GNU software,
  * additional software,
  * package manager.

- [**Debian**](https://www.debian.org/),
  [**Ubuntu**](https://ubuntu.com/),
  [**Raspberry Pi OS**](https://www.raspberrypi.com/software/);

- [**Fedora**](https://getfedora.org/), [**CentOS**](https://www.centos.org/);
  [**Arch**](https://archlinux.org/);
  [**Gentoo**](https://www.gentoo.org/);

- [**Alpine**](https://www.alpinelinux.org/): often used in containers.
 
---

## Our choice is Debian

- Versions

  |              | Packages  | Stability     |
  |--------------|-----------|---------------|
  | **Stable**   | 😒 older  | 🙂 stable     |
  | **Testing**  | 😐        | 😐            |
  | **Unstable** | 🙂 latest | 😒 not tested |

- Current stable:

  Version 11 "Bullseye" (2021)
