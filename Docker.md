## Docker
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
  -ti -d -e MYSQL_DATABASE=ticketmaster \
  -e MYSQL_USER=ticketmaster -e MYSQL_ROOT_HOST=0.0.0.0 \
  -e MYSQL_PASSWORD=ticketmaster -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 \
  -v /tmp/mysql:/var/lib/mysql mysql --character-set-server=utf8mb4 \
  --collation-server=utf8mb4_0900_as_cs
```
- Go inside MySql container:  
`docker exec -it mysql mysql -u <user> -p<pwd> <db>`
- Starts all stopped containers:  
`docker ps -aq -f status=exited | xargs docker start`
- Stores last started container'id:  
`export ID=$(docker ps -lq)`
- Show you how much disk space you’re using and how much can be potentially reclaimed:  
`docker system df`  
- Remove all stopped containers, networks not used, dangling images, build cache and images that are no longer referenced:  
`docker system prune -a`  
- Deletes all volumes with a specific name:  
`docker volume ls -f name=runner --format "{{.Name}}" | xargs docker volume rm`
- Deletes all containers *exited*:  
`docker ps -aq -f status=exited | xargs -r docker rm`
- Check the resource usage of containers running:  
`docker stats`  
- See what processes are running inside a container:  
`docker top <container>`  
- To see how a container’s file system has changed since it was created:  
`docker diff <container>`  
- Clean up docker datas:  
```bash
docker image prune -a --filter "until=170h" -f
docker container prune --filter "until=170h" -f
docker network prune --filter "until=170h" -f
docker volume prune --filter "until=170h" -f
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
