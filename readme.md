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