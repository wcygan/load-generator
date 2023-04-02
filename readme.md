## Load Generator

---

A tool to send load to a server.

This is accomplished by sending as many requests as possible to a server in a given time period.

#### Warning

> You probably don't want to target a host on the internet or use a metered connection with this :)

### Installation

```bash
cargo install --git https://github.com/wcygan/load-generator
```

### Usage

```
A tool to load test a server

Usage: ldg [OPTIONS] --url <URL>

Options:
  -u, --url <URL>                  The URL to send requests to
  -c, --connections <CONNECTIONS>  The number of connections to use [default: 8]
  -t, --time <TIME>                The amount of seconds to run the test for. If not specified, the test will run until an interrupt signal is received
  -h, --help                       Print help

```

### Example

In this example we'll target a local server running on port 3000 with 2 connections for 5 seconds.

Running [Axum Hello Server](https://github.com/wcygan/lib-wc/tree/master/experiments/axum-hello-server) locally & aiming this tool at it yields around 1M - 2M QPS.

```
ldg --url 0.0.0.0:3000 --connections 4 --time 2
```

On a MacBook Pro M1 Max this is running at approximately 1898470.07 requests per second.

### References

Adapted from [A Load Test CLI with Async Rust](https://www.manning.com/liveprojectseries/a-load-test-cli-with-async-rust-ser)
