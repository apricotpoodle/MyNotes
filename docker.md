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
