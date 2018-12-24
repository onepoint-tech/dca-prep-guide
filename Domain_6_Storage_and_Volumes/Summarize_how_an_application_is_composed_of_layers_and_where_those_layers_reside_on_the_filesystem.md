# Summarize how an application is composed of layers and where those layers reside on the filesystem

## Part 1: Summarize how an application is composed of layers

### Official Docker Documentation
[About images, containers, and storage drivers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)  

- image layers are R/O
- container layer is R/W
- All containers based on the same image share the same images layers
- copy-on-write (CoW) strategy : when a container modify a file for the first time this file is copy from the image layer before update

## Part 2: where those layers reside on the filesystem

### Official Docker Documentation
> [...] Each layer is pulled down separately, and stored in Docker’s local storage area, which is usually ´/var/lib/docker/´.

Source: [About images, containers, and storage drivers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)
