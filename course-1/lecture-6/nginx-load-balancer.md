# Nginx as Load balancer for 2 instances

* First we need to run 2 applications, which will return different response so that we can observe
Avengers app:
```bash
docker run -p 7000:5678 --name avengers --network mynet hashicorp/http-echo -text="Avengers are here..."
```

Justice League app:
```bash
docker run -p 7000:5678 --name justice-league --network mynet hashicorp/http-echo -text="Justice League are here..."
```

* Now you need to specify these 2 apps in your nginx.conf so that nginx can balance load
```bash
docker run -d \
  --name my-nginx \
  --network mynet \
  -p 8080:80 \
  -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro \
  nginx
```

* Run your browser and hit localhost:8080 multiple times


# Hands on learning

To remove all the stopped containers in docker use the following command:
```bash
docker container prune
```