# Nginx Caching Proxy Docker Container

A [Docker](https://www.docker.com) image with [Nginx](https://www.nginx.com) configured to act as a long caching proxy for HTTP requests.

I use it while performing programming presentations with life coding sessions. It is especially useful when you do some frontend coding and have CDN dependencies in your HTML.

**Warning:** Works only for `http` resources. For `https` returns error (fixme).


## Sample usage

1. Start docker composition `docker-compose up`
2. Set proxy server in system preferences
  - ([Example for Ubuntu](https://help.ubuntu.com/stable/ubuntu-help/net-proxy.html))

## Test case

1. Start the container
2. Send twice the same HTTP request through the caching proxy.
```
curl -I -x 'localhost:8787' 'https://cdnjs.cloudflare.com/ajax/libs/react/15.3.1/react.min.js'
```
Second request should be cached and should contain following headers:
```
X-Cached: HIT
X-Cache-Server: nginx-cache
```
