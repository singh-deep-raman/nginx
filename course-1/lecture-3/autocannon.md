# [autocannon](https://github.com/mcollina/autocannon)

* **autocannon** is perfect for quick, no-nonsense performance testing.
* **autocannon** is a fast HTTP benchmarking tool made by the Node.js folks.
* It hammers an HTTP endpoint with a configurable number of connections and reports:
    * Requests per second
    * Latency (avg / p95 / p99)
    * Throughput
    * Errors & timeouts
* Think of it as a modern, simpler alternative to `ab` (ApacheBench).

## Install autocannon

### Option 1: via npm (most common)
```bash
npm install -g autocannon
```

### Option 2: via npx (no install)
```bash
npx autocannon http://localhost:5678
```

## Basic usage

```bash
autocannon http://localhost:5678
```

Default behavior:

* 10 connections
* 10 seconds
* GET requests

Other options:
* `-c 50` → 50 concurrent connections
* `-d 15` → run test for 15 seconds
* `-a 10000` → fixed number of total requests
* `-m method` → method like POST, GET, PUT, PATCH
* `-H "key: value"`→ pass header like "Content-Type: application/json"
* `-b body` → pass body like json in this example '{"hello":"world"}'

## Pro tip ⚡

If you’re testing something behind Docker/Kubernetes:

* Run autocannon **outside** the cluster to simulate real clients
* Or run it **inside** to isolate networking overhead

