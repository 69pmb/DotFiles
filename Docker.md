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
docker run --restart always --name mysql \
  -ti -d -e MYSQL_DATABASE=ticketmaster \
  -e MYSQL_USER=ticketmaster -e MYSQL_ROOT_HOST=0.0.0.0 \
  -e MYSQL_PASSWORD=ticketmaster -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 \
  -v /tmp/mysql:/var/lib/mysql mysql --character-set-server=utf8mb4 \
  --collation-server=utf8mb4_0900_as_cs
```
- Go inside MySql container:  
`docker exec -it mysql mysql -uticketmaster -pticketmaster`
- Go inside volume:  
`docker run -it -v=postgres-data:/var/lib/docker/volumes/44ddfb270f899a016434a24c57a8c50cf92dbd7d20b5305b28f1d6acde965839/_data busybox /bin/sh`
