# Demonstrate creation of UCP client bundles

## Official Docker Documentation
[Download client certificates](https://docs.docker.com/datacenter/ucp/2.2/guides/user/access-ucp/cli-based-access/#download-client-certificates)

## Docker Blog
[Get Familiar with Docker Enterprise Edition Client Bundles](https://blog.docker.com/2017/09/get-familiar-docker-enterprise-edition-client-bundles/)

download from ui (user profile) or via REST API :

```bash
# Create an environment variable with the user security token
AUTHTOKEN=$(curl -sk -d '{"username":"<username>","password":"<password>"}' https://<ucp-ip>/auth/login | jq -r .auth_token)

# Download the client certificate bundle
curl -k -H "Authorization: Bearer $AUTHTOKEN" https://<ucp-ip>/api/clientbundle -o bundle.zip
```

