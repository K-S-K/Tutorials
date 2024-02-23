# Docker

## Docker Context

### [How to deploy on remote Docker hosts with docker-compose](https://www.docker.com/blog/how-to-deploy-on-remote-docker-hosts-with-docker-compose/)

#### Create and use context to target the remote host

- Create a Docker Context
```
docker context create rpi --description "Remote Raspberry PI" --docker "host=ssh://ksk@KSK-PI3B"
```

- List existing docker contexts
```
docker context ls
```

- List docker containers registered at the remote device
```
docker --context rpi ps
```

- Switch to the rpi context
```
docker context use rpi
```

- Switch to the default context
```
docker context use default
```

## [Dockerfile RUN vs CMD vs ENTRYPOINT](https://medium.com/ci-cd-devops/dockerfile-run-vs-cmd-vs-entrypoint-ae0d32ffe2b4)
- **RUN** is an image build step, the state of the container after a RUN command will be committed to the container image. A Dockerfile can have many RUN steps that layer on top of one another to build the image.
- **CMD** is the command the container executes by default when you launch the built image. A Dockerfile will only use the final CMD defined. The CMD can be overridden when starting a container with docker run $image $other_command.
- **ENTRYPOINT** is also closely related to CMD and can modify the way a container is started from an image. Default parameters that cannot be overridden when Docker Containers run with CLI parameters.
