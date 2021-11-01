# DOCKERIZE GOLANG APP

## HOW TO
### RUN
`sudo docker-compose build`  
`sudo docker-compose up`  
### ADD MORE APP
- clone your golang app to `src`  
- add more app to `docker-compose`  

```yml
  web_1:
    build: ./.docker/golang
    command: go run main.go
    volumes:
      - ./src/service-category:/var/www
    ports:
      - "8080:8080"
    networks:
      - backend
    depends_on:
      - db_redis
    restart: unless-stopped
  web_2:
    build: ./.docker/golang
    command: go run main.go
    volumes:
      - ./src/service-anything:/var/www
    ports:
      - "8081:8081"
    networks:
      - backend
    depends_on:
      - db_redis
    restart: unless-stopped
  web_3:
    
```

### ACCESS MARIA DB BASH
`sudo docker exec -it your-container-name bash`

### CHECK CONTAINER
`sudo docker ps`

| CONTAINER ID | IMAGE                     | COMMAND                | CREATED            | STATUS            | PORTS                                     | NAMES                       |
| ------------ | ------------------------- | ---------------------- | ------------------ | ----------------- | ----------------------------------------- | --------------------------- |
| 7d0bf9458a6b | golang-dockerize_web      | "go run main.go"       | About a minute ago | Up About a minute | 0.0.0.0:8082->8082/tcp, :::8082->8082/tcp | golang-dockerize_web_1      |
| 86948f99e8ca | golang-dockerize_db_mysql | "docker-entrypoint.s…" | About a minute ago | Up About a minute | 3306/tcp                                  | golang-dockerize_db_mysql_1 |
| f2c4c3561389 | mariadb:10.3.31-focal     | "docker-entrypoint.s…" | 8 minutes ago      | Up 8 minutes      | 3306/tcp                                  | db_mysql                    |
| b29f25b502e8 | golang-dockerize_db_redis | "docker-entrypoint.s…" | 5 hours ago        | Up 13 minutes     | 6379/tcp                                  | golang-dockerize_db_redis_1 |