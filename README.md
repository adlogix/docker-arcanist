# Arcanist Docker Container

Docker container to install and run arcanist

## Installation / Usage

1. Install the adlogix/arcanist container:

```sh
$ docker pull adlogix/arcanist
```

2. Run Arcanist through the Arcanist container:

```sh
$ docker run -ti --rm -v $(pwd):/app adlogix/arcanist
```

3. Use Arcanist with a self-signed certificate

```sh
# Create a data container for /home/arcanist
$ docker create --name arcanist-data -v /home/arcanist adlogix/arcanist

# Run arcanist with the data container and configure arcanist
$ docker run -ti --rm --volumes-from arcanist-data -v $(pwd):/app adlogix/arcanist set-config https.blindly-trust-domains '["your-domain.com"]'
$ docker run -ti --rm --volumes-from arcanist-data -v $(pwd):/app adlogix/arcanist install-certificate
```