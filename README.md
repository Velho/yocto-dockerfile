# Dockerfile

This project was put together to run Yocto configurations on a different system than Ubuntu 22.04 (Arch ftw).
The container has been configured as described in the https://www.nxp.com/docs/en/user-guide/UG10164.pdf application notes.
Image contains all the necessary setups for this such as configuring the repo tool and the different packages required.

The docker image inherits the UID and GID of the active user as not to run as root in the container.

## Building the Image

Docker image needs to be built first with following command,

```
$ docker build --build-arg USER_UID=$(id -u) --build-arg USER_GID=$(id -g) -t ubuntu22-dev .
```

## Run the Image

Run the image with the following command,

```
docker run -it --rm -v "$(pwd):/work" ubuntu22-dev
```
The current working directory is mounted to `/work`, but I suggest to mount the yocto directory itself into the `/work`.
e.g. `$(pwd)/imx-yocto:/work`



