# Ping

 Get IP address and ping host til infinity.

Image size is 9.3 MB.

## Build image

```bash
docker build . --tag=ping
```

## Run image

```bash
docker run -it --rm --name ping -e HOST=google.com ping
```

## Push to Docker Hub

```bash
docker tag ping markokole/ping:latest
```

```bash
docker push markokole/ping:latest
```
