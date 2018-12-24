# Describe the process of signing an image

## Official Docker Documentation
[Sign an image](https://docs.docker.com/datacenter/dtr/2.3/guides/user/manage-images/sign-images/)

By default, when you push an image to DTR, the Docker CLI client doesn’t sign the image.

```
export DOCKER_CONTENT_TRUST=1
docker push <dtr-domain>/<repository>/<image>:<tag>
```


To sign images in a way that UCP trusts them, you need to:

- Configure your Notary client
- Initialize trust metadata for the repository
- Delegate signing to the keys in your UCP client bundle

The tuf directory contains the trust metadata for the images you’ve signed. For each repository there are four files.

|File           |Description
|-              |-
|root.json      | Has data about other keys and their roles. This data is signed by the root key.
|targets.json   | Has data about the digest and size for an image. This data is signed by the target key.
|snapshot.json  | Has data about the version number of the root.json and targets.json files. This data is signed by the snapshot key.
|timestamp.json | Has data about the digest, size, and version number for the snapshot.json file. This data is signed by the timestamp key.

