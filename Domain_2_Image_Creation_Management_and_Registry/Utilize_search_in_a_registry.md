# Utilize search in a registry

## Official Docker Documentation
[docker search](https://docs.docker.com/engine/reference/commandline/search/)

```docker search [OPTIONS] TERM```
- --automated		**deprecated** : Only show automated builds
- --filter , -f	:	Filter output based on conditions provided
- --format	:	Pretty-print search using a Go template
- --limit	(25) :	Max number of search results
- --no-trunc :		Don’t truncate output
- --stars , -s		**deprecated** : Only displays with at least x stars

[Listing Repositories in a private registry](https://docs.docker.com/registry/spec/api/#listing-repositories)  

```GET /v2/_catalog```