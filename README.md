This repo contains a `Dockerfile` from which you can build a container running VSCode-Server. For detailed instruction, refer to [here](https://medium.com/@techhara/setup-vscode-server-develop-from-any-device-1b55470c05ee)

# Server

## Requirement
- docker
- Github or Microsoft account

## Build image
```bash
docker build -t vscode-remote-tunnel .
```

## Run
You can choose one of the two options below.

### Option 1
```bash
# directly mount the host's filesystem
docker run --rm -d -v /path/to/dev/folder/on/server:/home/dev/repo vscode-remote-tunnel code tunnel -e MACHINE_NAME=b660-vscode
```

### Option 2
```bash
# create a docker volume
docker volume create dev
# mount the docker volume
docker run --rm -d -v dev:/home/dev/repo vscode-server code tunnel -e MACHINE_NAME=b660-vscode
```

## Link account
```bash
# note the container id running vscode-server image
docker container ls
# print out container log and follow instruction to authenticate
docker logs CONTAINER_ID
```

# Client
## Connect to tunnel

### Web browser
Visit [vscode.dev](https://vscode.dev) and select `Connect to Tunnels`, authenticate, and select the instance. 

### VSCode app
Install [remote-tunnels](https://marketplace.visualstudio.com/items?itemName=ms-vscode.remote-server) extension. Connect to the server from `Remote Explorer` tab on the left.

## Develop
Dev container system's user name is `dev` and sudo password is `docker`.
