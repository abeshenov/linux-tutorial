# GNU/Linux tutorial

In this tutorial we are going to cover some basics of GNU/Linux systems,
working from the command line. We'll start with some basic commands,
structure of the file system, file permissions, and so on... There will be
probably two sessions of one hour each.


## Get a Docker image

You might already have some UNIX-like system at hand, but we want to make sure
that everyone has the same environment and doesn't mess with their real system.

So we are going to use **[Debian GNU/Linux](https://www.debian.org/)**,
in particular its latest version **Bullseye**. We will run the Docker image
```
debian:bullseye
```
Here you can check the official Docker images for Debian:
https://hub.docker.com/_/debian

So to get started,

1. Get [Docker](https://www.docker.com/) working on your system.

2. Pull the `debian:bullseye` image:

```
docker pull debian:bullseye
```

3. Now run this image:
```
docker run -it debian:bullseye
```

4. If everything works, you'll get the `root` shell with something like
   `root@19885a06b06c:/#"`. We'll work there together, but for the moment
   you may close it with
```
exit
```
