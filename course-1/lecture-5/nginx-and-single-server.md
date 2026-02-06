# NGINX as reverse proxy
* Now we want to route all of our requests to a web server through NGINX
* For this, we need to run a web server using docker like this:
```bash
    docker run -p 7000:5678 hashicorp/http-echo -text="my personal web server"
```
* Now, create an instance of Nginx using docker image and using the custom nginx.conf file
```bash
docker run -d \
  --name my-nginx \
  -p 8080:80 \
  -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro \
  nginx
```
* Look at the content of nginx.conf file for more details, which will route every request to prev server created

* Since, you want your Nginx container to talk to Web server container, they must be on same network
* In case of docker-compose.yml, Network is created by default and each container is tied to the same network
* In case of docker run, you have to manually create a network and each container should be tied to same network as follows

```bash
docker network create mynet
```

```bash
docker run -p 7000:5678 --name raman2 --network mynet hashicorp/http-echo -text="my personal web server"
```

```bash
docker run -d \
  --name my-nginx \
  --network mynet \
  -p 8080:80 \
  -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro \
  nginx
```

## Some trouble shooting commands or tips
When you use Docker Compose, it automatically creates a user-defined bridge network for your app, and all services are attached to it unless you say otherwise.
That means:
✅ Containers can resolve each other by service name
✅ Built-in DNS is already set up
✅ You don’t need to manually create a network (unlike raw docker run)
This is one of the big conveniences of Compose compared to plain docker run in Docker.

It will tell you what network your container is using
```bash
docker inspect container-name | grep NetworkMode
```

It will tell you what available networks are (default ones and custom ones)
```bash
docker network ls
```

You can get internal IP address of a container within a network using:
```bash
docker inspect container-name | grep IPAddress
```

To run some commands within a container, you can open a shell of a container using:
```bash
docker exec -it container-name sh
```

To see the logs of a container:
```bash
docker logs container-name
```

To stop and remove a container:
```bash
docker stop container-name-or-id && docker rm container-name-or-id
```