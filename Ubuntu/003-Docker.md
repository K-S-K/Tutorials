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
