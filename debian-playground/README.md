# Simple Debian setup with a sudo user

This `Dockerfile` creates a basic Debian image with a given
sudoer user and password. Use this to play with Debian.


## Building and using the image

Run everything below with `sudo` on Linux.

Building the image:
```shell
docker build -t debian-playground .
```

Running:
```shell
docker run -it --hostname cosmos --name debian_container debian-playground
```

Listing containers:
```shell
docker container ls -a
```

Going back to the container:

```shell
docker start -i debian_container
```
