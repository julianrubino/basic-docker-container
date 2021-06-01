#### Creating Image

```bash
$ docker build -t hello-node:v1 .
```

#### Listing Images

```bash
$ docker image ls
```

#### Storing In Public Registry

First you need to login:
```bash
$ docker login
```

Storing in Docker registry:

```bash
$ docker tag hello-node:v1 <USER ID>/hello-node:v1
$ docker push <USER ID>/hello-node:v1
```

#### Running

To run a local image **locally** (meaning, make sure your terminal isn't "attached" to minikube or a docker-machine):

```bash
$ docker run -p 5555:5000 hello-node:v1
```

To run an image from public registry:

```bash
$ docker run -p 5555:5000 gcr.io/<USER ID>/hello-node:v1
```

To run in the background, add `-d`.

#### Listing Containers

To list running containers:

```bash
$ docker container ls
```

or 

```bash
$ docker ps
```

To list all containers:

```bash
$ docker container ls -a
```

#### Testing

To access the container running **locally** (i.e. not in Minikube nor Docker machine):

```bash
$ curl http://localhost:5555
```

If you built and run the containers while your terminal is attached to Minikube or a Docker machine, then replace *localhost* with the IP address of Minikube (`minikube ip` command) or Docker machine, e.g.:

```bash
$ curl http://192.168.99.100:5555
```


If you're on Windows, I think you need to replace *localhost* with the IP address of your host.
 

#### Stopping Container

```bash
$ docker stop <CONTAINER ID>
```
or

```bash
$ docker container stop <CONTAINER ID>
```

Or if the container is running interactively, just press Ctrl-C. On Windows, you still need to issue `docker container stop <CONTAINER ID>` after hitting Ctrl-C. 

#### Removing Container

```bash
$ docker rm <CONTAINER ID>
```
or 

```bash
$ docker container rm <CONTAINER ID>
```

#### Removing Image

```bash
$ docker rmi <IMAGE>
```

or

```bash
$ docker image rm <IMAGE>
```

where `<IMAGE>` can be their tag names or image IDs.

#### Pruning Unused Images

```bash
$ docker image prune
```
