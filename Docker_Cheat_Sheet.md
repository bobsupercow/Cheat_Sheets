# Docker General Commands

## Tagging an image
```shell
docker tage <image_id> name_of_the_image
```
## Realtime logs
```shell
docker logs --tail 1 --follow cbceaaea0ef5
```

## Forcing a rebuild
```shell
docker build --no-cache
```

## Publish a port even if it was not exposed in the dockerfile
```shell
docker run -p <port>
```

## Publish all ports that were explosed in the docker file
```shell
docker run -P
```

## Setting up environment variables
```shell
docker run -e WEBAPP_PORT=8000 -e WEBAPP_HOST=www.example.com
```

## Renaming a container
```shell
docker rename <old_name> <new_name>
```

## Using jq with docker
```shell
docker inspect <container_name> | jq .[0] | jq keys

[
  "Architecture",
  "Author",
  "Comment",
  "Config",
  "Container",
  "ContainerConfig",
  "Created",
  "DockerVersion",
  "GraphDriver",
  "Id",
  "Os",
  "Parent",
  "RepoDigests",
  "RepoTags",
  "RootFS",
  "Size",
  "VirtualSize"
]
docker inspect <container_name> | jq .[0] | jq .DockerVersion
"1.12.3"
```

## Using format with docker
```shell
docker inspect --format '' <container_id>
```

## Find the port mapping for a container e.g. port 80
```shell
docker port <containerID> 80
```

## Manual allocation of port
```shell
docker run -d -p host_port:container_port <container>
```

## Finding the container IP address using format (you can use jq)
```shell
docker inspect --format '' <ContainerID>
docker inspect <ContainerID> | jq .[0] | jq .NetworkSetting.IPAddress
```

## Removing a docker container
```shell
docker rm -f <container_name>
```

## Create a custom network
```shell
docker network create <network name>
```

## Some useful options
```shell
--internal # no communication with the outside worlds
--gateway # specify the gateway of choice
--subnet # choose the subnet to use e.g., --subnet 192.168.1.0/24
--ip-range # specify which IPs from the subnet to use
--aux-address # specify reserved addresses not to be used by the network
```

## Create an overlay network
```shell
docker network create mynet --driver overlay
```

## Create a container link
```shell
docker run -it --link datastore:redis alpine ping redis
```
## Connecting a volume on the host to the container
```shell
docker run -d -v $(pwd):/src username/application_name
```

## Create a volume from another container (data-containers usecase)
```shell
docker run --volumes-from <source_container> <destination_container> <commands>
```

## List available volumes
```shell
docker volumes ls
```

## Create named volumes
```shell
docker volume create --name <volume_name>
```
