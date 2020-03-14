# DockerUtils
## Docker cheat sheet

Build an image
```
$ cd /path/to/Dockerfile
$ sudo docker build .
```
```
docker image build [OPTIONS] PATH | URL | -
```

View running processes
```
$ sudo docker ps
```

View all processes
```
$ sudo docker ps -a
```

Run an image in a new container daemonized
```
$ sudo docker run -d <image_name>
```

Run an image in interactive mode with the command `/bin/bash`
```
$ sudo docker run -i -t <image_name> /bin/bash
```

Run an image in interactive mode with the command `/bin/bash` and link the ports.
```
$ sudo docker run -i -t --link <docker_container_name>:<docker_container_alias> <image_name> /bin/bash
```

Run an image with an ENTRYPOINT command in interactive mode with the command `/bin/bash`
```
$ sudo docker run --entrypoint /bin/bash -i -t <image_name>
```

Run an image in interactive mode with the command `/bin/bash` mounting the host director `/var/app/current` to the container directory `/usr/src/app`
```
$ sudo docker run -i -t -v /var/app/current:/usr/src/app/ <image_name> /bin/bash
```

Run an image in interactive mode with the command `/bin/bash` setting the environments variables `FOO` and `BAR`
```
$ sudo docker run -i -t -e FOO=foo -e BAR=bar <image_name> /bin/bash
```

Delete one image
```
$ docker rmi <image_name_or_id>
```

Delete all images
```
$ docker rmi $(docker images -q)
```

Delete one container
```
$ docker rm <container_name_or_id>
```

Delete all running and stopped containers
```
$ docker container rm -f $(docker ps -aq)
```

Run a container from the Alpine version 3.9 image, name the running container “web” and expose port 5000 externally,
mapped to port 80 inside the container.
```
$ docker container run --name web -p 5000:80 alpine:3.9
```

Stop a running container through SIGTERM 
```
$ docker container stop web
```

Stop a running container through SIGKILL
```
$ docker container kill web
```

List the networks
```
$ docker network ls
```

Print the last 100  lines of a container’s logs
```
docker container logs --tail 100 web
```