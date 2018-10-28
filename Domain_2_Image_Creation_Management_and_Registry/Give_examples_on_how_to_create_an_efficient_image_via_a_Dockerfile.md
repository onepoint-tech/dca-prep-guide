# Give examples on how to create an efficient image via a Dockerfile

## Official Docker Documentation
[Best practices for writing Dockerfiles](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)  

### Create ephemeral containers

Twelve-Factor

### Understand build context

When you issue a docker build command, the current working directory is called the build context. By default, the Dockerfile is assumed to be located here, but you can specify a different location with the file flag (-f). Regardless of where the Dockerfile actually lives, all recursive contents of files and directories in the current directory are sent to the Docker daemon as the build context.

Inadvertently including files that are not necessary for building an image results in a larger build context and larger image size. This can increase the time to build the image, time to pull and push it, and the container runtime size. To see how big your build context is, look for a message like this when building your Dockerfile:

```Sending build context to Docker daemon  187.8MB```

### Exclude with .dockerignore

### Use multi-stage builds

### Don’t install unnecessary packages

### Decouple applications

### Minimize the number of layers

### Sort multi-line arguments

### Leverage build cache
