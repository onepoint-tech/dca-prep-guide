# Inspect images and report specific attributes using filter and format

## Official Docker Documentation
[docker image inspect](https://docs.docker.com/engine/reference/commandline/image_inspect/)  

```docker image inspect [OPTIONS] IMAGE [IMAGE...]```

[Filter inspect results](https://docs.docker.com/engine/reference/commandline/images/#filtering)  

```bash
docker images --filter "dangling=true"

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
<none>              <none>              8abc22fbb042        4 weeks ago         0 B
<none>              <none>              48e5f45168b9        4 weeks ago         2.489 MB

docker images --filter "label=com.example.version"

REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE
match-me-1          latest              eeae25ada2aa        About a minute ago   188.3 MB
```

[Format inspect results](https://docs.docker.com/engine/reference/commandline/images/#format-the-output)  

- .ID :	Image ID
- .Repository :	Image repository
- .Tag : Image tag
- .Digest :	Image digest
- .CreatedSince	: Elapsed time since the image was created
- .CreatedAt : Time when the image was created
- .Size	: Image disk size

```bash
docker images --format "{{.ID}}: {{.Repository}}"

77af4d6b9913: <none>
b6fa739cedf5: committ
78a85c484f71: <none>
30557a29d5ab: docker
```