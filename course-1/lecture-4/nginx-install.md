# NGINX installation

* There are multiple ways to install NGINX on a machine (linux, windows, mac) but the easiest way is to run it with docker image

## Nginx as docker image
```bash
    docker run -d --name my-nginx -p 8080:80 nginx
```
* It will run the nginx with the default nginx.conf file, to provide your custom config file, use below command
```bash
    docker run -d \
  --name my-nginx \
  -p 8080:80 \
  -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro \
  nginx
```
* Make sure nginx.conf file exists in current directory