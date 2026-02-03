# [http-echo](https://hub.docker.com/r/hashicorp/http-echo)

* **`http-echo`** is a tiny Docker image that runs a simple web server
* Its only job is to **echo back whatever you tell it to say** when someone makes an HTTP request.

### What it’s used for

* A **testing and debugging tool** like:
  * Test load balancers or ingress controllers
  * Verify networking, ports, and routing
  * Quickly stand up a fake HTTP endpoint

### How it works

When you run the container:

* It starts an HTTP server
* Listens on a port (usually `5678`)
* Responds to HTTP requests with a fixed message (or request details)

### Most popular common image

```
hashicorp/http-echo
```

### Basic example

Run it with Docker:

```bash
docker run -p 7000:5678 hashicorp/http-echo -text="hello from docker"
```

```
http://localhost:5678
```

### Useful flags

* `-text` → what message to return
* `-listen` → address/port to listen on (default `:5678`)
* `-status` → HTTP status code to return (e.g. 200, 404)

Example:

```bash
docker run -p 8080:8080 hashicorp/http-echo \
  -listen=:8080 \
  -text="OK" \
  -status=200
```

### Why people like it

* Super small image
* Starts instantly
* Zero config
* Perfect for “is my networking working?” checks

