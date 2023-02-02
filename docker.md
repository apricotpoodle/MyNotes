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

## Docker Logging

As you leran more about containers and orchestration, you are likely to use logs more and more to resolve issues.
We'll use the jenkins' application, for example, and demonstration purposes this time because it generates several logs

### command logs

```bash
root@ubuntu:~# docker run -dit --name busylogs -p 8080:8080 -p 5000:5000 jenkins/jenkins:lts
```
Check by docker ps if the container is running
OK, it looks like it's successfully running now for this particular application to access it from a Web browser and start using it, you actually need a password.
And this image as a container generate a unique password the first time you run it.
And so how in the world are we going to get that password ?
Well, we can use the Docker Logs command to view the output provided by this container.
And, of course, in that output is going to be our password that we need.

```bash
docker logs busy_logs

...

*************************************************************
*************************************************************
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

7f2bf58bf38b40458e8aa45367107cc5  <- c'est le mot de passe ! 

This may also be found at: /var/jenkins_home/secrets/initialAdminPassword

*************************************************************
*************************************************************
*************************************************************

```
#### option -f 

```bash
docker -f logs busy_logs
```
So now, if any new output is produced by the container, it will be immediately returned to our screen.
Ctrl-C to break out of this mode.

#### option -t

Now, this gives you access to all the time stamps for each entry written to the log.

### Creating some logs for exercise

Now, what I'm going to do is pull up a Web browser and connect to Port 8080 on this container and create some logs, so I'm just going to hit enter a few times here to show that these new logs will appear as their are being created.

And that'll give us some space to see when something new shows up here to our log.


#### option --since

```bash
docker --since 2011-11-11 logs busy_logs
```

#### Lister les logs fournis par docker au système hôte

Les 25 derniers messages du service docker reçus dans les journaux Debian.

```bash
journalctl -u docker.service -n 25
```

#### option --no-pager pour enrouler toute la longueur des lignes

```bash
sudo journalctl --no-pager -u docker.service -n 25
```
