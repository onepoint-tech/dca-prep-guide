# Log into a registry

## Official Docker Documentation
[docker login](https://docs.docker.com/engine/reference/commandline/login/)  

```docker login [OPTIONS] [SERVER]```

- --password , -p	:	Password
- --password-stdin	:	Take the password from stdin
- --username , -u	:	Username



Using STDIN prevents the password from ending up in the shell’s history, or log-files :

```cat ~/my_password.txt | docker login --username foo --password-stdin```