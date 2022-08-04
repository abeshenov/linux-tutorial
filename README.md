# GNU/Linux tutorial

In this tutorial we are going to cover some basics of GNU/Linux systems,
working from the command line. We'll start with some basic commands,
structure of the file system, file permissions, and so on... There will be
probably two sessions of one hour each.


## Part 0: Setup a Docker image

You might already have some UNIX-like system at hand, but we want to make sure
that everyone has the same environment and doesn't mess with their real system.

So we are going to use **[Debian GNU/Linux](https://www.debian.org/)**,
in particular its latest version **Bullseye**. We will run the Docker image
```
debian:bullseye
```
Here you can check the official Docker images for Debian:
https://hub.docker.com/_/debian


### Get started

Get [Docker](https://www.docker.com/) working on your system
and review some basics of using Docker on https://docs.docker.com/

Below I list `docker` commands to be executed. All of them require `root`
privileges, so if you're already on Linux, it should be always `sudo docker ...`


### Build a custom image

We want to prepare our own image that has a non-root user
(later we'll see what that means).

For this build the image from
[debian-playground/Dockerfile](./debian-playground/Dockerfile)

It is based on the `debian:bullseye` image.

First, feel free to replace `user` in the `Dockerfile` with your preferred
username, and password `qwerty` with something else.

Here is how you build the image:

```
cd debian-playground
docker build -t debian-playground .
```


### Check if everything works

Now you should be able to run the new image `debian-playground` with
```
docker run -it --hostname cosmos debian-playground
```

You will see the command line prompt `user@cosmos:~$`.
Instead of `cosmos`, you may put any hostname you like.

For the moment, just type `exit` to exit the container.


### Going back to the container

When we execute `exit`, our container gets stopped. To list all containers, do

```
$ docker container ls -a
CONTAINER ID   IMAGE               COMMAND   CREATED              STATUS                      PORTS     NAMES
26edb150fb3b   debian-playground   "bash"    About a minute ago   Exited (1) 24 seconds ago             eloquent_brattain
```

This means that our `debian-playground` image is in the container named
`eloquent_brattain`, and we are running `bash` shell in there.

To get back to the same container, we do
```
$ docker start -i eloquent_brattain
```

We will continue working in that container, setting up and exploring our Linux
system.


## Part 1: GNU, Linux, and distributions

### Why Linux and command line?

- GNU/Linux is one of the best operating systems.
- Very efficient work flow from the terminal.
- Many servers run Linux. The access is usually remote via command line.
- Inside containers we often run Linux systems.

This is why software developers should be familiar with some basics of Linux
and command line, no matter what operating system they use on their personal
machine.

### Basic terms

- **[UNIX](https://en.wikipedia.org/wiki/Unix)**: operating system released in
  1973.

- Has inspired many operating systems that are still in use nowadays:
  **[Unix-like](https://en.wikipedia.org/wiki/Unix-like) systems**.

- **[POSIX](https://en.wikipedia.org/wiki/POSIX)**:
  a family of standards defining UNIX-like systems.

- **GNU/Linux** = **GNU** + **Linux**. Sometimes abbreviated to "Linux".

- **[Linux](https://www.kernel.org/)**: free kernel written by Linus Torvalds
  that has been in collaborative development since 1991. Millions of lines of
  code in C.

- **[GNU](https://www.gnu.org/)** (= *GNU's not a UNIX*):
  free software project founded by Richard Stallman in 1983 that together with
  the kernel makes a UNIX-like operating system.

- **GNU/Linux distribution**: comes with Linux kernel, GNU software, plus
  additional software, and usually a package manager.

### Some distributions

- [**Debian**](https://www.debian.org/), [**Ubuntu**](https://ubuntu.com/),

- [**Fedora**](https://getfedora.org/),

- [**Arch**](https://archlinux.org/),

- [**Gentoo**](https://www.gentoo.org/),

- [**Alpine**](https://www.alpinelinux.org/): often used in containers.

- ...

### Our choice is Debian

Versions of Debian:

- **Stable**: older versions of packages, but stable,
- **Unstable** ("Sid"): latest versions, but not tested,
- **Testing**: in-between, testing before going to stable.

- Code names: Toy Story characters.
- Last versions:
  * Version 8 "Jessie" (2015),
  * Version 9, "Stretch" (2017),
  * Version 10, "Buster" (2019),
  * Version 11, "Bullseye" (2021).
- Current stable version: **Bullseye**.

![Bullseye](bullseye.png)

### Useful links

- Docker images: https://hub.docker.com/_/debian
- AMIs for AWS: https://wiki.debian.org/Cloud/AmazonEC2Image/Bullseye
- Packages: https://packages.debian.org/stable/

### First practice

Now if you run our `debian:bullseye` image in Docker, you will see the command
prompt

```
user@cosmos:~$ 
```

We will type some commands that tell us that we are indeed running
Debian Bullseye.

- `cat` (concatenate) is a basic command which concatenates files:
  ```
  cat file1.txt [file2.txt ...]
  ```
  this will print to standard output files `file1.txt`, `file2.txt`, etc.
  concatenated.

The following files contain information about the Debian version:

- `/etc/debian_version`
- `/etc/issue`
- `/etc/os-release`

Here is how to print them with `cat`:

```
user@cosmos:~$ cat /etc/issue
Debian GNU/Linux 11 \n \l
```

```
user@cosmos:~$ cat /etc/debian_version
11.4
```

```
$ cat /etc/os-release
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
