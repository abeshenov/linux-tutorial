# GNU/Linux Tutorial

In this tutorial we are going to cover some basics of GNU/Linux systems,
working from the command line. We'll start with some basic commands,
structure of the file system, file permissions, and so on... There will be
probably two sessions of one hour each.

- [**Part I**: Basics](basics.md)
- To be continued...


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
