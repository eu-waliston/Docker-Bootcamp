To download and launch the container all you need to do run the following commands from your
terminal prompt;

```
docker image pull nginx
docker container run -d --name nginx-test -p 8080:80 nginx
```
You can check that the container is running using the following command:
```
docker container ps
```

Opening your browser and going to http://localhost:8080/ should show you the default
Welcome to NGINX page.

#### commands to stop and remove the container and then delete the image:
```
docker container stop nginx-test
docker container rm nginx-test
docker image rm nginx
```