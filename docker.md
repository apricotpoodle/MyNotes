# Docker


[Démystifier ENTRYPOINT et CMD dans Docker](https://aws.amazon.com/fr/blogs/france/demystifier-entrypoint-et-cmd-dans-docker/) - Que choisir entre ENTRY_POINt et CMD dans un Dockerfile.

[Docker Swarm](https://dockerswarm.rocks/) - how-to's on docker swarm.

Export an image to a tar file:

```console
docker save <IMAGE>:<TAG> -o <NAME>.tar
```

Load an image from a tar:

```console
docker load -i <NAME>.tar 
```
## Managing Docker Images

### Download an image

#### Pull command

docker pull nom_image

```bash
docker  pull nginx
```
### Check presence of an image on the system

#### images command

List the images that have already been pulled or downloaded to local host system

```bash
docker images
```

### Check history, how was constructed the image

docker history nom_image

```bash
docker history nginx
```

### TAGGING image

#### syntax command

```bash
# docker tag --help

Usage:  docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]

Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

```

Let's say we've tested then nginx image and it's working perfectly four our needs.
We want to make suure we can use this exact image for future deployments

```bash
# docker tag nginx:latest nginx:my_blog_stable
# docker images
REPOSITORY      TAG           IMAGE_ID      CREATED     SIZE
nginx           latest        e445ab08b2be  ...         ...
nginx           myblog_stable e445ab08b2be  ...         ...
```




You want to limit the number of layers in an image for simplicity
