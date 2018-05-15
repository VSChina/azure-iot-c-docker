## Build Docker Image

```cmd
docker build --rm -t c-mqtt .
```

## Run Docker Container

```cmd
docker run -d --privileged --name my-c-mqtt c-mqtt
```

## Debug

1. Press `F5`.
2. In dropdown list, select the right process to attach.