# Docker

- Create image from docker file:  
    `docker build -t docker-postgres . -f ./Dockerfile`
- Create container from image:  
    `docker create -t docker-postgres`
- Start container:  
    `docker start jovial_easley`
- Get inside container:  
    `docker exec -it jovial_easley bash`
- MySql container:

```bash
docker run --name mysql \
  -ti -d -e MYSQL_DATABASE=name \
  -e MYSQL_USER=user -e MYSQL_ROOT_HOST=0.0.0.0 \
  -e MYSQL_PASSWORD=pwd -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 \
  -v /tmp/mysql:/var/lib/mysql mysql --character-set-server=utf8mb4 \
  --collation-server=utf8mb4_0900_as_cs
```

- Go inside MySql container:  
    `docker exec -it mysql mysql -u <user> -p<pwd> <db>`
- Starts all stopped containers:  
    `docker ps -aq -f status=exited | xargs docker start`
- Stores last started container'id:  
    `export ID=$(docker ps -lq)`
- Show you how much disk space you're using and how much can be potentially reclaimed:  
    `docker system df`
- Remove all stopped containers, networks not used, dangling images, build cache and images that are no longer referenced:  
    `docker system prune -a`
- Deletes all volumes with a specific name:  
    `docker volume ls -f name=runner --format "{{.Name}}" | xargs docker volume rm`
- Deletes all containers _exited_:  
    `docker ps -aq -f status=exited | xargs -r docker rm`
- Check the resource usage of containers running:  
    `docker stats`
- Find the volumne of a container:  
    `docker inspect -f "{{ .Mounts }}" <container>`
- See what processes are running inside a container:  
    `docker top <container>`
- To see how a container's file system has changed since it was created:  
    `docker diff <container>`
- To print image layers with their sizes:  
    `docker history --no-trunc <image>`
- To copy file to container:  
    `docker cp <file_path> <container:/dir_path>`
- To copy file from container:  
    `docker cp <container:/file_path> <dir_path>`
- Clean up docker datas:

```bash
docker image prune -q -f dangling=true | xargs docker rmi
docker ps -a -q | xargs docker rm
docker network prune
docker volume ls -q -f dangling=true | xargs docker volume rm
# Hard core
docker system prune -f
```

- Run localstack:

```bash
docker run -ti -d --name localstack \
  -v /home/localstack:/tmp/localstack \
  -p 8080:8080 -p 4567-4584:4567-4584 \
  -e aws_default_region=eu-west-1 \
  -e port_web_ui=8080 localstack/localstack
```

- Go inside a volume:

```bash
docker run -it \
  -v=postgres-data:/var/lib/docker/volumes/<volume_id>/_data busybox \
  /bin/sh
```

- Push a image to the docker registry:

```bash
docker login -u "docker-id" -p "mypassword" docker.io
docker tag my-container docker-id/image-name:tag
docker push docker-id/image-name:tag
```
