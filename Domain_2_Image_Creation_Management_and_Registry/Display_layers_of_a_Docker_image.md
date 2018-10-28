# Display layers of a Docker image

## Official Docker Documentation
[docker image history](https://docs.docker.com/engine/reference/commandline/image_history/)  

Docker history
```bash
docker history kong:0.14.1-alpine
IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
65eb0d085fa6        6 weeks ago         /bin/sh -c #(nop)  CMD ["kong" "docker-start…   0B
<missing>           6 weeks ago         /bin/sh -c #(nop)  STOPSIGNAL [SIGTERM]         0B
<missing>           6 weeks ago         /bin/sh -c #(nop)  EXPOSE 8000/tcp 8001/tcp …   0B
<missing>           6 weeks ago         /bin/sh -c #(nop)  ENTRYPOINT ["/docker-entr…   0B
<missing>           6 weeks ago         /bin/sh -c #(nop) COPY file:e1ac3f3f858d8725…   315B
<missing>           6 weeks ago         /bin/sh -c apk add --no-cache --virtual .bui…   88.3MB
<missing>           6 weeks ago         /bin/sh -c #(nop)  ENV KONG_SHA256=e29937c51…   0B
<missing>           6 weeks ago         /bin/sh -c #(nop)  ENV KONG_VERSION=0.14.1      0B
<missing>           6 weeks ago         /bin/sh -c #(nop)  LABEL maintainer=Marco Pa…   0B
<missing>           6 weeks ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B
<missing>           6 weeks ago         /bin/sh -c #(nop) ADD file:ad486f580145bd2de…   4.03MB
```
Note: The ```<missing>``` lines in the docker history output indicate that those layers were built on another system and are not available locally. This can be ignored.
