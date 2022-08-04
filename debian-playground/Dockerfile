FROM debian:bullseye
RUN apt-get update
RUN apt-get install -y sudo
RUN useradd --create-home --shell /bin/bash user
RUN echo 'user:qwerty' | chpasswd
RUN usermod -aG sudo user
USER user
WORKDIR /home/user
