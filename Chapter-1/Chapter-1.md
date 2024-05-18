# Docker on Ubuntu


### To install Docker run the following commands:
```
curl -sSL https://get.docker.com/ | sh

docker version
```

### To install Docker Machine run the following commands:

```
curl -L "https://github.com/docker/machine/releases/download/v0.9.0/docker-machine-$(uname -s)-$(uname -m)" -o /tmp/docker-machine

chmod +x /tmp/docker-machine

sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
```

### To install Docker Compose, run the following commands:

#### Step 1 — Installing Docker Compose

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

docker-compose --version

Obs: some errors ? try with sudo 
```

### Step 2 — Setting Up a docker-compose.yml File

```
mkdir ~/compose-demo
cd ~/compose-demo

mkdir app

nano app/index.html
```
Place the following content into this file:
```
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>Docker Compose Demo</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/kognise/water.css@latest/dist/dark.min.css">
</head>
<body>

    <h1>This is a Docker Compose Demo Page.</h1>
    <p>This content is being served by an Nginx container.</p>

</body>
</html>
```

Next, create the docker-compose.yml file:
```
nano docker-compose.yml
```

Insert the following content in your docker-compose.yml file:
```
version: '3.7'
services:
  web:
    image: nginx:alpine
    ports:
      - "8000:80"
    volumes:
      - ./app:/usr/share/nginx/html

```
### Step 3 — Running Docker Compose
```
docker-compose up -d
```
Your environment is now up and running in the background. To verify that the container is active, you can run:
```
docker-compose ps

LINK: localhost:8000
```
### Step 4 — Getting Familiar with Docker Compose Commands

To check the logs produced by your Nginx container, you can use the logs command:

```
docker-compose logs
```
If you want to pause the environment execution without changing the current state of your containers, you can use:
```
docker-compose pause
```
To resume execution after issuing a pause:
```
docker-compose unpause
```
The stop command will terminate the container execution, but it won’t destroy any data associated with your containers:
```
docker-compose stop
```
If you want to remove the containers, networks, and volumes associated with this containerized environment, use the down command:
```
docker-compose down
```

In case you want to also remove the base image from your system, you can use:

```
docker image rm nginx:alpine
```




