# Describe process to use external certificates with UCP and DTR

## Official Docker Documentation
[UCP Use your own TLS certificates](https://docs.docker.com/datacenter/ucp/2.2/guides/admin/configure/use-your-own-tls-certificates/)

From UI download :

- ca.pem : file with the root CA public certificate.
- cert.pem : file with the TLS certificate for your domain and any intermediate public certificates, in this order.
- key.pem : file with TLS private key. Make sure it is not encrypted with a password. Encrypted keys should have ENCRYPTED in the first line.

During install, use ```--external-server-cert``` option

[DTR Use your own TLS certificates](https://docs.docker.com/datacenter/dtr/2.3/guides/admin/configure/use-your-own-tls-certificates/)


